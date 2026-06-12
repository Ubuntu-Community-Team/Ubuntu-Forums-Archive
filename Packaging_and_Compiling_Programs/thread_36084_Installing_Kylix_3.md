---
title: "Installing Kylix 3"
date: 2005-05-21
forum: Packaging and Compiling Programs
---

### Post by CarnMeynen on 2005-05-21
Hi Ppl,

I've just installed Ubuntu 4.1 and tried installing Kylix 3 professional and got the following response when I ran 'sh setup.sh'

Checking dependencies...
WARNING: could not locate libX11.so
Kernel version >= 2.2.0....OK
Glibc version >= 2.1.2....OK
X11 Server....OK
Libjpeg version >= 6.2.0....OK
setup.sh: line 350: [: x11-2: integer expression expected
setup.sh: line 352: [: x11-2: integer expression expected
setup.sh: line 354: [: x11-2: integer expression expected
setup.sh: line 350: [: x11-2: integer expression expected
setup.sh: line 352: [: x11-2: integer expression expected
setup.sh: line 354: [: x11-2: integer expression expected
Libgtk version >= 1.2.0....FAILED

Lines 350-354 are...

    for gtkso in $gtksolist; do
       gtkOK=1
       major=`echo $gtkso | awk -F. '{print $2}'`
       minor=`echo $gtkso | awk -F. '{print $3}'`
       build=`echo $gtkso | awk -F. '{print $5}'`

350   if [ $major -gt $GTK_MAJOR ]; then
351      gtkOK=0
352   elif [ $major -eq $GTK_MAJOR -a $minor -gt $GTK_MINOR ]; then
353      gtkOK=0
354   elif [ $major -eq $GTK_MAJOR -a $minor -eq $GTK_MINOR -a $build -ge $GTK_BUILD ]; then
         gtkOK=0
      fi

      if [ $gtkOK -eq 0 ]; then
         gtk_version="$major.$minor.$build"
         return $gtkOK
      fi
   done

   return $gtkOK
}

Are there any work arounds or fixes for this?

Andrew

---

### Post by eric222 on 2005-05-26
I ran into this as well.  Create a symbolic link from /usr/x11R6/lib/libx11.so.6.2 to /usr/x11R6/lib/libx11.so

You will also need to do the following to get the menus and toolbars to work (and pretty much everything else in kylix).  In the startdelphi script, add this:

LANG=en_US.ISO8859-1

Cheers,

Eric

---

### Post by lvincent on 2005-06-17
Eric, 

    What about the kylix 3 hanging during running a simple app? have you done some fixes like changing LD_ASSUME_KERNEL?


   thanks,

lvincent

---

### Post by metavoid on 2005-10-01
So kylix 3 works on ububtu 4?

---

### Post by masterping on 2006-07-24
Well.. a long time since the last post. But I'm having problems with kylix. Using ubuntu 6.06 and kylix 3

The installation was clean but when I tried to run kylix all the windows are very VERY large and nothing can be read.
I already changed winelook=win95

Any help?

---

### Post by davbren on 2007-04-09
Ok I'm trying to install Kylix onto edgy but it doesn't seem to like the setup.sh file. it tells me I don't have permission, even though I am logged in as root...

---

### Post by JackInBottle on 2008-03-04
> **CarnMeynen said:**
> Hi Ppl,

I've just installed Ubuntu 4.1 and tried installing Kylix 3 professional and got the following response when I ran 'sh setup.sh'

Checking dependencies...
WARNING: could not locate libX11.so
Kernel version >= 2.2.0....OK
Glibc version >= 2.1.2....OK
X11 Server....OK
Libjpeg version >= 6.2.0....OK
setup.sh: line 350: [: x11-2: integer expression expected
setup.sh: line 352: [: x11-2: integer expression expected
setup.sh: line 354: [: x11-2: integer expression expected
setup.sh: line 350: [: x11-2: integer expression expected
setup.sh: line 352: [: x11-2: integer expression expected
setup.sh: line 354: [: x11-2: integer expression expected
Libgtk version >= 1.2.0....FAILED

Lines 350-354 are...

    for gtkso in $gtksolist; do
       gtkOK=1
       major=`echo $gtkso | awk -F. '{print $2}'`
       minor=`echo $gtkso | awk -F. '{print $3}'`
       build=`echo $gtkso | awk -F. '{print $5}'`

350   if [ $major -gt $GTK_MAJOR ]; then
351      gtkOK=0
352   elif [ $major -eq $GTK_MAJOR -a $minor -gt $GTK_MINOR ]; then
353      gtkOK=0
354   elif [ $major -eq $GTK_MAJOR -a $minor -eq $GTK_MINOR -a $build -ge $GTK_BUILD ]; then
         gtkOK=0
      fi

      if [ $gtkOK -eq 0 ]; then
         gtk_version="$major.$minor.$build"
         return $gtkOK
      fi
   done

   return $gtkOK
}

Are there any work arounds or fixes for this?

Andrew
Hello, 
I had this problem exactly. 
I did follow eric222's sugestion but that did not solve the problem. Cause I even could not find the /usr/X11R6 directory since X window are mostly using xorg nodays.
So it is obviously the setup scipt way behind the current situation. 
But I finally solved the problem, I am not a Linux geek, that is why I want make kylix works on Linux, so please forgive me that I made a set of ugly steps to make setup.sh works for ubuntu 7.10:
1. Copy all the cdrom files to your hardrive. (I do not want to copy the giant run image file to my disk, so I first  made a local empty image file by touch command, There must be better way to avoid copy specified files, but I do not know that yet)
    $> mkdir kylix
    $> cd kylix
    $> touch runimage.tar.gz
    $>cp -u -r /media/cdrom0/. .
2. Find what gtk versions string that setup.sh got
    setup.sh trys to find version number of libgtk. But the script assumes the old fashion of version string, that is where the problem came from.
    insert following line at setup.sh at line 345, it will print of the gtk string it found:
...
       for gtkso in $gtkfiles; do
      gtkso=`basename $gtkso`
      gtksolist="$gtksolist `echo $gtkso | awk -F\  '{print $NF}' | sed s/-/./1`"
    done
echo $gtkso  <-- this is the line added

3 run the setup.sh script
   note: ubuntu's sh shell won't work with setup.sh, I checked the first line of setup.sh, then I tried bash, it worked
   $ bash ./setup.sh
   setup.sh still fails, but you got the string of gtkso printed out on screen. For Ubuntu 7.10
it is libgtk-x11-2.0.so.0.1200
   With this string, I know all the three varibles in script got wrong information, and that was why script fails. I modified the script, (I am not good at awk  etc, so I specify the varible manually :))
Here they are:
#line 348
    for gtkso in $gtksolist; do
       gtkOK=1
       major=`echo $gtkso | awk -F. '{print $2}'`
       minor=`echo $gtkso | awk -F. '{print $3}'`
       build=`echo $gtkso | awk -F. '{print $5}'`
#wgm192 : following 3 lines are added by specify the version info.  
	major="2"   
        minor="0"
        build="1200"
...

after that, the installation went through!

good luck!

---

### Post by jfgarcia on 2008-07-15
Thank you, JackInBottle,

I'd try to install Kylix 3 in Ubuntu 7.1 and with the modifications you suggest the installer now works.

But, something in the way went wrong; some links and scripts in the /bin directory are missing (startdelphi, startkylix, etc...).

To solve this, I do:
export SETUP_INSTALLPATH=$HOME/kylix3

from the install directory:
cd setup.data
bash main.sh

this script will create the necessary links and scripts.

But, after that, when I run startdelphi, I get the error:
"version GLIBC_2.0 not defined in file libc.so.6"

looking in some forums I found that I can try LD_ASSUME_KERNEL=2.4.1
Now I get the error:
"sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory"

I fact, I get this error even when I do a simple "ls".

some hints to get Kylix 3 running on Ubuntu 7.10 or 8?

Thanks in advance.

---

