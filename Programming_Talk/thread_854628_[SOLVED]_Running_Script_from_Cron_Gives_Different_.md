---
title: "[SOLVED] Running Script from Cron Gives Different Results"
date: 2008-07-09
forum: Programming Talk
---

### Post by MasterXandrex on 2008-07-09
OK, I am using a script that should cycle through all files in a directory, determine what is gone and what has been added, it then removes and adds them to SVN and commits. It then updates. All that is fine, the weird thing is when I run it from CRON.

When I run it from CRON, the script does not complete as when I run it from the terminal. 

The command is: 

/home/xandrex/Home_Repo/scripts/svnautocommit /home/xandrex/Home_Repo/ >> /home/xandrex/SVN_log

the crontab entry is: 

0,5,10,15,20,25,30,35,40,45,50,55 * * * * /home/xandrex/Home_Repo/scripts/svnautocommit /home/xandrex/Home_Repo/ >> /home/xandrex/SVN_log

When I look at SVN_log I recieve the following results when ran from terminal:

Wed Jul  9 17:11:34 EDT 2008
At revision 21.

or if I have updated something I get this or similar:

Wed Jul  9 17:12:36 EDT 2008
Sending        scripts/svn/svnautocommit
Transmitting file data .
Committed revision 22.
At revision 22.

but when it is ran from CRON, I only get the date portion

The script is below and any help would be useful.

Thanks,

Xan -- ](*,)


```

#!/bin/bash 
date 

#------------------------------- Subroutines ---------------------------------
usage(){
echo " Usage: $(basename $0) PATH" 
echo ""
echo "Automatically commits the changes of svn working copy located in PATH."
echo "The new files are automatically added and the files that have been removed"
echo "are removed."
echo ""
echo "By Gael Varoquaux"
}

#------------------------------- Process the options -------------------------
if [ $# -eq 1 ]
then
    workingdir="$1"
else
    usage
    exit 1
fi

if ! cd $workingdir
then
    echo $workingdir is not a accessible path.
    usage
    exit 1
fi

#------------------------------- Find out what has changed -------------------

# A warning if this fails :
mkdir -p $HOME/.local
echo "SVN autocommit failed" > $HOME/.local/motd

svnstatus=$(svn status $workingdir)
added=$(printf "$svnstatus" | sed -n 's/^[A?] *\(.*\)/\1/p')
removed=$(printf "$svnstatus" | sed -n 's/^! *\(.*\)/\1/p')

if [ "x$added" != "x" ]
then
    echo adding "$added" to repository
    svn add $added
fi

if [ "x$removed" != "x" ]
then
    echo removing "$removed" to repository
    svn remove $removed
fi

svn commit -m "autocommit" && rm $HOME/.local/motd 
svn update

```

---

### Post by apmcd47 on 2008-07-09
This could be a stupid question as I don't know svn, but what environment variables do you need to run svn? For instance I need CVSROOT for cvs. My guess is that the full environment you need to run this script is not set. Cron tends to use a minimal environment, so you find things like your extended PATH, or CVSROOT, are not set. You may need to source your .bashrc file from svnautocommit, or, if you have one, source /etc/default/svn.

Andrew

---

### Post by Trumpen on 2008-07-09
Moreover, $HOME is normally not set during the execution of a cron script.

Edited: 
oops, the above seems to be untrue; in fact, according to man 5 crontab:

> HOME is set from the /etc/passwd line of the crontab&#8217;s owner.

By the way, crontab sends a local email when something goes wrong; it may be helpful ;)

---

### Post by MasterXandrex on 2008-07-09
SVN does not require environment variables -- it uses the CWD.

I'll try swapping out $HOME

Xan

---

### Post by MasterXandrex on 2008-07-09
That didn't work, I'm still getting the same thing.

Any other suggestions?

Thanks,

Xan

---

### Post by skeeterbug on 2008-07-09
A while ago I had problems with a perl script I had setup in cron. I set it up to CD into the script directory before executing it, and it worked exactly how I was executing it from the terminal. Sorry it has been a long time, I have no idea what the exact problem was then (so this may not be relevant to you at all).

The crontab:

02 00 01 * *  cd /home/jbest/usage_report/ && perl create_report.pl >> /home/jbest/usage_report/create_report.log

---

### Post by MasterXandrex on 2008-07-09
The bash script does taht as soon as it begins with $1

Xan

---

### Post by unutbu on 2008-07-09
```
echo "SVN autocommit failed" > $HOME/.local/motd
```

Is this line executed?

Perhaps add 

```
echo $PATH > $HOME/.local/path
```

to you script so you can check that your PATH is proper too.

---

### Post by MasterXandrex on 2008-07-10
I thought about that, in the crontab I've set the environment and path identically, and there are no other variables.

Plus I just realized that from the Cron run I was not getting the errors, this is the output of the cron after I redirected the errors into the log.
```

Thu Jul 10 09:30:01 EDT 2008
svn: Can't convert string from native encoding to 'UTF-8':
svn: Assignment A ?\226?\128?\147 Class 4 ?\226?\128?\147 Mining Department Presentation-ENGR199.doc
svn: Working copy '/home/xandrex/Home_Repo' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
svn: Working copy '.' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
svn: Can't convert string from native encoding to 'UTF-8':
svn: Assignment A ?\226?\128?\147 Class 4 ?\226?\128?\147 Mining Department Presentation-ENGR199.doc

```
and from the terminal it works perfectly... I don't understand what's going on. They have the same path and shell.


From terminal env:
```
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=4f0c2f83914a938118680516483ef5ac-1215709210.963196-1735041177
SSH_CLIENT=157.182.63.67 42314 22
SSH_TTY=/dev/pts/3
USER=xandrex
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
MAIL=/var/mail/xandrex
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/xandrex
LANG=en_US.UTF-8
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/xandrex
LOGNAME=xandrex
SSH_CONNECTION=157.182.63.67 42314 192.168.1.100 22
LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

```

and from the Cron env:
```
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/xandrex
SHLVL=1
HOME=/home/xandrex
LOGNAME=xandrex
_=/usr/bin/env

```


Xan

---

### Post by unutbu on 2008-07-10
This is just a guess. Since the error log mentioned UTF-8, perhaps try adding

```
LANG=en_US.UTF-8
```

to the cron environment.

---

### Post by MasterXandrex on 2008-07-10
Worked beautifully, thanks so much.

---

