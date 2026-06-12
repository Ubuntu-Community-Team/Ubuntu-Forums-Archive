---
title: "Google Earth Problems"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2011-09-24
I'm running Kubuntu 11.04 Beta 2 (64 bit) with the Nvidia proprietary driver.  I seem to have had this same issue with 11.04 since the first Alpha and not sure how to resolve it.  I have the same situation on 3 different machines with the same configuration.

When starting Google Earth, I get the Splash Screen and nothing further.  Starting Google Earth from the terminal, I get a "Caught Signal 11" error and find, after a Google Search, there are pages upon pages of links for this error.  I've tried several fixes, none of which have worked.  Likewise, I've tried installing Google Earth both using the version from the Google Earth website as well as making the package from the Ubuntu repository.  Same result.

Here is what I'm getting from the crash log when starting from the terminal:
Major Version 6
Minor Version 0
Build Number 0003
Build Date May 17 2011
Build Time 00:40:40
OS Type 3
OS Major Version 3
OS Minor Version 0
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1316850779
Up Time 1.26037

Stacktrace from glibc:
/usr/lib/googleearth/libgoogleearth_free.so(+0xab953)[0xf76af953]
/usr/lib/googleearth/libgoogleearth_free.so(+0xabad3)[0xf76afad3]
[0xf7724400]

I have installed the lsb-core and other packages recommended in various tutorials.  

Just wondering if anyone has gotten Google Earth to run and how I might be able to fix this issue.

Thanks,
zenarcher

---

### Post by SevenMachines on 2011-09-24
Using nvidia binary here and see the same, adding
```
 $ LD_PRELOAD=/usr/lib32/nvidia-current-updates/libGL.so.1 ./googleearth
```or change the googleearth script line
```
LD_LIBRARY_PATH=.:/usr/lib32/nvidia-current-updates/:$LD_LIBRARY_PATH ./googleearth-bin "$@"
```without preloading i think it uses the mesa gl libs rather than the nvidia ones. I dont know if its something the alternatives system is broken or google earth needs updated, which seems more likely somehow. No real idea though, just working is how I left it.

---

### Post by BbUiDgZ on 2011-09-24
I had the same issue with 11.04 64bit with the a nvidia gfx card.

I made a symbolic link from "/opt/googleearth/libgoogleearth_free.so" to "/usr/lib32/libgoogleearth_free.so" and "/usr/lib64/libgoogleearth_free.so" which fixed it for me ;)

---

### Post by zenarcher on 2011-09-24
> **BbUiDgZ said:**
> I had the same issue with 11.04 64bit with the a nvidia gfx card.

I made a symbolic link from "/opt/googleearth/libgoogleearth_free.so" to "/usr/lib32/libgoogleearth_free.so" and "/usr/lib64/libgoogleearth_free.so" which fixed it for me ;)

Thanks for the suggestion.  I gave it a try but don't seem to be able to link to the /usr/lib64/libgoogleearth_free.so as it doesn't seem to exist.:

zenarcher@stanmain:~$ sudo ln -s /opt/googleearth/libgoogleearth_free_so /usr/lib32/libgoogleearth_free.so
[sudo] password for zenarcher: 
zenarcher@stanmain:~$ sudo ln -s /opt/googleearth/libgoogleearth_free.so /usr/lib64/libgoogleearth_free.so
ln: creating symbolic link `/usr/lib64/libgoogleearth_free.so': No such file or directory
zenarcher@stanmain:~$

---

### Post by zenarcher on 2011-09-24
> **SevenMachines said:**
> Using nvidia binary here and see the same, adding
```
 $ LD_PRELOAD=/usr/lib32/nvidia-current-updates/libGL.so.1 ./googleearth
```or change the googleearth script line
```
LD_LIBRARY_PATH=.:/usr/lib32/nvidia-current-updates/:$LD_LIBRARY_PATH ./googleearth-bin "$@"
```without preloading i think it uses the mesa gl libs rather than the nvidia ones. I dont know if its something the alternatives system is broken or google earth needs updated, which seems more likely somehow. No real idea though, just working is how I left it.

Thanks for the suggestions here.  I seem to be a bit dumb, as I'm not sure where you meant to add the line or change the googleearth script line.  Could you tell me where make those changes?

Thanks much,
zenarcher

---

### Post by SevenMachines on 2011-09-24
You can add the LD_LIBRARY_PATH on the command line followed by whatever the googleearth, depends how you installed it though. if its installed in /usr/bin then
```
 LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates/ googleearth
```would work

If you want to make the change permanent then you can add it to the googleearth command, its a script calling the real binary. Where this is installed and how it looks again depends on how you've installed it. Adding
```
LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates:${LD_LIBRARY_PATH}
```to the top of any of them. For example, heres one from a local install here, the only change made was the first line. Note that when googleearth has been installed to the system the googleearth script looks different, doesnt matter though, the same line can still be stuck at the top of it

googleearth:
```

# in the right place for libraries that might also be installed
# elsewhere on your system.
#
# Ryan C. Gordon,  Thu Jul 20 14:32:33 PDT 2006

# Function to find the real directory a program resides in.

# Add nvidia's library path first so that we use that for gl stuff, hacky :)
LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates:${LD_LIBRARY_PATH} 

FindPath()
{
    fullpath="`echo $1 | grep /`"
    if [ "$fullpath" = "" ]; then
        oIFS="$IFS"
        IFS=:
        for path in $PATH
        do if [ -x "$path/$1" ]; then
               if [ "$path" = "" ]; then
                   path="."
               fi
               fullpath="$path/$1"
               break
           fi
        done
        IFS="$oIFS"
    fi
    if [ "$fullpath" = "" ]; then
        fullpath="$1"
    fi

    # Is the sed/ls magic portable?
    if [ -L "$fullpath" ]; then
        #fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
        fullpath=`ls -l "$fullpath" |sed -e 's/.* -> //' |sed -e 's/\*//'`
    fi
    dirname $fullpath
}

script_path=$(FindPath $0);

cd $script_path;

LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

```

---

### Post by alphacrucis2 on 2011-09-24
Same problem on a machine using the AMD/ATI Catalyst driver. After upgrading to 11.10 from 11.04 (64 bit) google-earth crashes with signal 11 shortly after starting. Other OpenGL apps such as Stellarium are working fine.

---

### Post by SevenMachines on 2011-09-24
fglrx users might give 
```
 $ LD_LIBRARY_PATH=/usr/lib/fglrx/ googleearth
```
a bash, i can only vouch for it working on nvidia here though

---

### Post by zenarcher on 2011-09-24
> **SevenMachines said:**
> You can add the LD_LIBRARY_PATH on the command line followed by whatever the googleearth, depends how you installed it though. if its installed in /usr/bin then
```
 LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates/ googleearth
```would work

If you want to make the change permanent then you can add it to the googleearth command, its a script calling the real binary. Where this is installed and how it looks again depends on how you've installed it. Adding
```
LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates:${LD_LIBRARY_PATH}
```to the top of any of them. For example, heres one from a local install here, the only change made was the first line. Note that when googleearth has been installed to the system the googleearth script looks different, doesnt matter though, the same line can still be stuck at the top of it

googleearth:
```

# in the right place for libraries that might also be installed
# elsewhere on your system.
#
# Ryan C. Gordon,  Thu Jul 20 14:32:33 PDT 2006

# Function to find the real directory a program resides in.

# Add nvidia's library path first so that we use that for gl stuff, hacky :)
LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates:${LD_LIBRARY_PATH} 

FindPath()
{
    fullpath="`echo $1 | grep /`"
    if [ "$fullpath" = "" ]; then
        oIFS="$IFS"
        IFS=:
        for path in $PATH
        do if [ -x "$path/$1" ]; then
               if [ "$path" = "" ]; then
                   path="."
               fi
               fullpath="$path/$1"
               break
           fi
        done
        IFS="$oIFS"
    fi
    if [ "$fullpath" = "" ]; then
        fullpath="$1"
    fi

    # Is the sed/ls magic portable?
    if [ -L "$fullpath" ]; then
        #fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
        fullpath=`ls -l "$fullpath" |sed -e 's/.* -> //' |sed -e 's/\*//'`
    fi
    dirname $fullpath
}

script_path=$(FindPath $0);

cd $script_path;

LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH ./googleearth-bin "$@"

```


Okay...I understand.  Tried it both ways but still getting the Signal 11 error.  Here's entering by the command line. By the way, yes, googleearth is is 'usr/bin/

zenarcher@stanmain:~$ LD_LIBRARY_PATH=/usr/lib32/nvidia-current-updates/ googleearth
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/zenarcher/.googleearth/crashlogs/crashlog-4e7dcc5b.txt

Please include this file if you submit a bug report to Google.

I wonder if I should completely uninstall Google Earth then reinstall and try it again?

Thanks,
zenarcher

---

### Post by SevenMachines on 2011-09-24
You may need to change the path to 
/usr/lib32/nvidia-current

[EDIT]Have a look at
```
 $ find /usr/lib32/ -name 'libGL*'
```

---

### Post by zenarcher on 2011-09-24
> **SevenMachines said:**
> You may need to change the path to 
/usr/lib32/nvidia-current

[EDIT]Have a look at
```
 $ find /usr/lib32/ -name 'libGL*'
```

Thanks....here's what I get with that command.....

zenarcher@stanmain:~$ find /usr/lib32/ -name 'libGL*'
/usr/lib32/libGLU.so
/usr/lib32/mesa/libGL.so.1.2
/usr/lib32/mesa/libGL.so.1
/usr/lib32/libGL.so.1.2
/usr/lib32/libGL.so.1
/usr/lib32/libGL.so
/usr/lib32/nvidia-current/libGL.la
/usr/lib32/nvidia-current/libGL.so.280.13
/usr/lib32/nvidia-current/libGL.so.1
/usr/lib32/nvidia-current/libGL.so
/usr/lib32/libGLU.so.1.3.071100
/usr/lib32/libGLU.so.1
zenarcher@stanmain:~$ 


zenarcher

---

### Post by zenarcher on 2011-09-24
> **SevenMachines said:**
> You may need to change the path to 
/usr/lib32/nvidia-current

[EDIT]Have a look at
```
 $ find /usr/lib32/ -name 'libGL*'
```

Okay....from the command line, here's what I get:

zenarcher@stanmain:~$ find /usr/lib32/ -name 'libGL*'
/usr/lib32/libGLU.so
/usr/lib32/mesa/libGL.so.1.2
/usr/lib32/mesa/libGL.so.1
/usr/lib32/libGL.so.1.2
/usr/lib32/libGL.so.1
/usr/lib32/libGL.so
/usr/lib32/nvidia-current/libGL.la
/usr/lib32/nvidia-current/libGL.so.280.13
/usr/lib32/nvidia-current/libGL.so.1
/usr/lib32/nvidia-current/libGL.so
/usr/lib32/libGLU.so.1.3.071100
/usr/lib32/libGLU.so.1
zenarcher@stanmain:~$ 

I tried your suggestion changing to nvidia-current, but still seemed to get the same result...Caught Signal 11.


Ah....got it!  I forgot to remove the previous script change you gave me!  Once I did that and just put nvidia-current, all is working properly.

Thanks!

zenarcher

---

### Post by alphacrucis2 on 2011-09-29
Not luck until today's updates. Google Earth is now working for me.

---

### Post by t1497f35 on 2011-09-29
Mozilla ships a (true) Firefox amd64 bit Linux version, too bad Google can't afford doing the same for Linux. Even Adobe is about to ship a (true) amd64 version of flash.

---

### Post by SpEcIeS on 2011-09-29
Thank-you for the tip. It worked wonderfully. ;)

---

### Post by x-shaney-x on 2011-09-29
I'm not able to run it on Intel hardware either, was working fine a day or so ago.

64-bit

```
./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

