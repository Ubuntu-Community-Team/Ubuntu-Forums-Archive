---
title: "[SOLVED] anyone know how to install sun studio express 2008?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by iansane on 2008-09-15
Hi, I'm trying to install sun studio express 2008 from the .sh script they provide. Sun says just to chmod +x and run the script. It doesn't work because something is wrong with the tar.bz2 code that is in the script. I don't know why they can't put it in it's own file to avoid problems but it's a 150MB .sh script with tar.bz2 code in the script. All one file.

The error I get says it is not a tar and then when I change a line of code as suggested on sun forums I get error that it is not in bzip format.

Anyone succesfully installed this in Ubuntu 8.04?

Thanks

---

### Post by Sorivenul on 2008-09-15
Working to recreate this.  In all the times I've run large .sh installers I've never had a problem.  I will update when I have more information.  In the meantime, can you post what exactly you changed in the installer and what you changed it to?

---

### Post by iansane on 2008-09-15
Thanks sorivenul.

Line I chaged was
 ```
tail  +651
```
I changed it to
 ```
tail --lines=+651
```

I had to use nano because gedit could not open it. (encoding problem).

I had to scroll down almost to the end of the script to find the line and had no line number to go by. The next line is the one that tells shell to unpack the tar. So I assume it has something to do with parameters for the system to unpack it. I really have no idea.

---

### Post by Sorivenul on 2008-09-15
Well, the good news is I have successfully recreated this error.  The bad news is that having tried the "tail" solution myself, I'm still getting the same error.  I will do more searching on the issue.  At this point it really may be that it is corrupt.  It's hard to tell as we can't test the error against previous SunStudio Express versions as they are deprecated and unavailable for download from the main Sun site.  Will post back with yet more information.

---

### Post by iansane on 2008-09-15
Well thanks a lot for giving it a shot. I posted it on sun forums. LOL I finally got a reply, someone telling me how to extract a tar file. Gotta just grit my teeth and breath when people do that. Anyway, I'll keep trying too. Thanks :-)

---

### Post by Sorivenul on 2008-09-15
Got it!
After reviewing the README, I realized SSE requires the official Sun Java JDK to be installed.  Crazy, I know.  
A simple:
```
sudo apt-get install sun-java6-jdk
```
After that, simply follow the regular install instructions.  Let me know if you're still having issues.

---

### Post by iansane on 2008-09-15
Sorevinul,

I'm glad that worked for you but now I'm alone with this.

I didn't have jdk6 installed the first time but after installing it I downloaded a fresh copy of SSE and got the same errors. The exact errors are.

```

Please wait while Sun Studio is unpacked into this directory.
tail: cannot open `+651' for reading: No such file or directory
bzcat: /tmp/ssregister.18473/sunstudio.tar.bz2 is not a bzip2 file.
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
exit: 648: Illegal number: Sun Studio instllation failed.

```

And fix the error for "tail" line as mentioned before.
Then I get this.
```

Please wait while Sun Studio is unpacked into this directory.

bzcat: Data integrity error when decompressing.
        Input file = /tmp/ssregister.18546/sunstudio.tar.bz2, output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
exit: 648: Illegal number: Sun Studio instllation failed.

```

I appreciate your help, but it's 12:00 and I have to be at school in the morning so I'll check back tomorrow. Thanks

---

### Post by Sorivenul on 2008-09-16
Put the "tail" section back to its original state if you've edited it again.
Then try this before running the install:
```
export _POSIX2_VERSION=199209
```

I forgot to include this bit, which is obviously crucial, in my solution.  If you're still having problems let me know.

---

### Post by iansane on 2008-09-16
That did it!! Thanks Sorivenul

I had to download a fresh copy again cause apparently making changes to the script corrupted in when nano rewrote it. Even after putting the "tail" section back to original.

I did get an error after the succesful install.

```

Sun Studio was successfully installed.
[: 650: Illegal number: 

```

But it appears to be installed and working. Updated without error. 
I'll need to make a menu entry under applications>programming to open ~/sunstudioceres/prod/bin/sunstudio but that's no big deal.

If you don't mind, can you explain the "export _POSIX2_VERSION=199209" command and why it worked?

Thanks

---

### Post by Sorivenul on 2008-09-16
> **iansane said:**
> 
If you don't mind, can you explain the "export _POSIX2_VERSION=199209" command and why it worked?
The program that makes the .sh installers is called [makeself]("http://megastep.org/makeself/").  This is the quote from the website that offered me the solution:
> Important note for recent GNU/Linux distributions: Archives created with Makeself prior to v2.1.2 were using an old syntax for the head and tail Unix commands that is being progressively obsoleted in their GNU forms. Therefore you may have problems uncompressing some of these archives. A workaround for this is to set the environment variable $_POSIX2_VERSION to enable the old syntax.
Take a closer look at the website for more information.  It might be worthwhile to post the full solution on the Sun forums since you have an account and the question posted there already.

---

### Post by iansane on 2008-09-16
Thanks again Sorevinul. It's posted there now. I'm gonna mark this solved.

---

