---
title: "a beginner shell-scripting help"
date: 2008-07-18
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-18
this is what i encountered in an example for taking backup :
```
 # Backup using tar; redirect any errors to a
  # temporary file
  # For multi-disk support, you can use the
  # -M option to tar
  tar -czf /dev/fd1 . >|/tmp/ERRORS$$ 2>&1
  # zero status indicates backup was successful
  if [ "$?" = "0" ]
    then
    dialog --title "Backup" --msgbox "Backup \
completed successfully." 10 50
```

i cant understand whats going on in the 5th line (begins with tar command).

---

### Post by moma on 2008-07-18
[COLOR="SeaGreen"]tar -czf /dev/fd1 . 2>&1  >| /tmp/ERRORS$$ [/COLOR]

[COLOR="Green"]tar -czf [/COLOR]
**-c** = create a new archive and compress files to tar format
**-z** = and further compress to gzip format.
**-f** output filename.
In your case tar will send the compressed files to /dev/fd1. 
/dev/fd0 = floppy disk 0 (A:/ in windows terms) and 
/dev/fd1 = floppy disk 1 (B:/ in windows terms). 

**.** (a dot) means the current directory. So the tar command will take all files from the current directory.

**2>&1** = Redirect stderr to stdout (standard output). 2 = file number for stderr.  1 = file number for the stdout. 
">" means redirect, send to.
In other words, 2>&1 will send all errors and warnings to the standard output (your terminal window). And the next command...

**>|** = Redirect,send stdout (standard output) to file /tmp/ERRORS$$. 
$$ means the current process id (number). For example, test this command 
[COLOR="Green"]echo "this process has id:$$"[/COLOR]

Notice: Do not be confused by the ">|" syntax. It's basically same as the normal redirect symbol ">", but ">|" will overwrite the existing file even the **noclobber** shell options is set. Normal ">" will not overwrite the file if noclobber option is set. Noclobber is a safety issue but ">|" will override it.

Search for ">|" here: [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

Ok, that's it.

More information.
Browse to [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html) and study:**The ABS guide...** and **Shell tutor...** guides.

Read also:[http://linuxbasiccommands.wordpress.com/2008/04/04/linux-tar-command/](http://linuxbasiccommands.wordpress.com/2008/04/04/linux-tar-command/)

---

### Post by dexter.deepak on 2008-07-19
some more problems...
```
tempfile=`tempfile 2>/dev/null` || tempfile=/tmp/test$$
trap "rm -f $tempfile" 0 1 2 5 15
```

i forgot the role of `` and am not able to google it out..
i have encountered tempfile for the first time.. the manual page says that it creates temporaray files in a "safe" way ...what is meant by safe here..is it any good from a manual temporary file creation ?
also why is 2>/dev/null a parameter to tempfile ??
theres no man page for trap..so i need help there too....what are these nos. at the end ??

---

### Post by dwhitney67 on 2008-07-19
Look at the man-page for 'bash'.  That will have information concerning 'trap'.

Basically 'trap' is used to prevent an operator from interrupting or killing the script while it is running.  An interrupt can be issued with a ctrl-c.  A kill can come in the form of 'kill <pid>', where <pid> is the process id of the script that is running.

As far as I know, there is no way to prevent a script from terminating when it is killed with extreme prejudice:  'kill -9 <pid>'

As for the 'trap' numbers, you can correlate those with the different kill signals that are listed in /usr/include/bits/signum.h.  As for the 0, I am not sure what that is for, but it is probably described in the man-page for 'bash'.

---

### Post by moma on 2008-07-19
Re-hello,

(I changed the variable name to mytempfile to improve readability)
**[COLOR="DarkGreen"]mytempfile=`tempfile 2>/dev/null` || mytempfile=/tmp/test$$[/COLOR]**

Most Linux/Unix systems have a "tempfile" command. It just creates a unique filename for your temporary data. Start gnome-terminal and test it
[COLOR="SeaGreen"]tempfile [/COLOR]

However some older Unix systems (I think) DO NOT HAVE the tempfile command, and execution of [COLOR="SeaGreen"]`tempfile 2>/dev/null`[/COLOR] will fail (it's false), then it executes the other command after logical **or** "||". It's a very clever way to ensure that the mytempfile variable will **always** get a proper value (in this case a temporary filename).

Study these examples very carefully. You must learn to understand the logical **or** "||" and **and** "&&" operators. Test these lines in you terminal window. 
[COLOR="SeaGreen"]/bin/true || echo "it's me"[/COLOR]
[COLOR="SeaGreen"]/bin/false || echo "it's me"[/COLOR]
--
**[COLOR="DarkGreen"]2 > /dev/null[/COLOR]**
If the tempfile command fails (eg. it does not exists or it just fails to create a temp filename) it will send all error messages to /dev/null (/dev/null is a big black hole that can eat anything). Do you remember?  2 is the file number of stderr (standard error output, normally your terminal window). The command 2>/dev/null just sends all error messages to the /dev/null black hole.
--

**[COLOR="DarkGreen"]`tempfile 2>/dev/null`[/COLOR]**
The back quotes `...` mean; execute this command. You can also use the $(command) syntax. Study these examples. They are equal.
[COLOR="SeaGreen"]atext="Today is date: `date`"
echo $atext

atext="Today is date: $(date)"
echo $atext[/COLOR]
--

Agree with dwhitney67, check the manual page for "bash"
[COLOR="SeaGreen"]man bash [/COLOR]

---

### Post by mssever on 2008-07-19
> **moma said:**
> **-c** = create a new archive and compress files to tar format
**-z** = and further compress to gzip format.
Actually, that isn't quite correct. A plain tar file (i.e., created with -c but not -z or -j) is uncompressed. If you want compression you have to explicitly ask for it. You can either give the -z or -j options (-j is for bzip2), or you can manually run the uncompressed tar file through the compressor of your choice.
> **dexter.deepak said:**
> ```
tempfile=`tempfile 2>/dev/null` || tempfile=/tmp/test$$
trap "rm -f $tempfile" 0 1 2 5 15
```i forgot the role of `` and am not able to google it out..
Try this instead: ```
tempfile="$(tempfile 2>/dev/null)" || tempfile=/tmp/test$$
```Using $() is preferred over backquotes for command substitutions, because it's more readable and more flexible. You can nest $() if you need to, but you can't nest backquotes. Both constructs run the enclosed command and replace themselves with the command's output to stdout. It's a really good idea to make a habit of surrounding command substitutions (and other variable assignments) with double quotes. In this particular instance, you can get away with not doing it. But if the output ever contains special characters (including spaces), you could be in for some very unpleasant surprises. Double quotes will prevent those surprises.

---

### Post by moma on 2008-07-20
> **mssever said:**
> Actually, that isn't quite correct. A plain tar file (i.e., created with -c but not -z or -j) is uncompressed.

Thanks. You are absolutely right. 

An ordinary tar archive (without -z or -j options) is not compressed. The archive contains file headers (metadata with file names and checksums) and each file is padded with "\0"s to nearest 512 bytes block.

I read about it here: [http://en.wikipedia.org/wiki/Tar_(file_format)](http://en.wikipedia.org/wiki/Tar_(file_format)) ;-)

As a test I archived some _pure text files_.
[COLOR="SeaGreen"]tar -cvf archive.tar *.txt[/COLOR]

Type it on screen
[COLOR="SeaGreen"]cat archive.tar[/COLOR]

And the archive.tar seems to be an ascii encoded tarball with a lot of (\0)s. Nice.

---

### Post by mssever on 2008-07-20
> **moma said:**
> Type it on screen
[COLOR=SeaGreen]cat archive.tar[/COLOR]

And the archive.tar seems to be an ascii encoded tarball with a lot of (\0)s. Nice.
I'm surprised doing that didn't hose your terminal. Using cat to print binary data to the terminal usually results in sending what the terminal interprets as weird escape codes which have the effect of rendering the terminal useless. Sounds like NULLs are safe to print, but less is a better tool for examining binary file formats. hd is also good.
```
less archive.tar #or
hd archive.tar | less
```

---

