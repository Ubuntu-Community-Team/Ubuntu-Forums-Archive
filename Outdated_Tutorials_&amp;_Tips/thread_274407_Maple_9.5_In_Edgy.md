---
title: "Maple 9.5 In Edgy"
date: 2006-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by calvinthomas on 2006-10-09
Firstly, if you are one of the lucky people with Maple 10 (the latest version) then please follow the method from here as it works and is easier:
[URL="http://www.ubuntuforums.org/showthread.php?t=270443"]
http://www.ubuntuforums.org/showthread.php?t=270443[/URL]

If like me you still have Maple 9.5 that method may not work (it didn't for me) however a method used for installing Maple 9.5 on x64 Dapper did work for me, this method was constructed by **bmcage** and also simplified (at least for me) by **dimis** no credit should go to me for this guide as i'm simply putting together others work for easy access.
[B]
The How-To Errors[/B]

Firstly, you will notice if you just try and run the script installer you get several errors like this:

```
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)
```

This is an error with Java that can be fixed like so and also not give this error when you try to open the installer (this is the problem I had with the method that works for Maple 10)

```
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NullPointerException
        at ZeroGgi.<init>(DashoA8113)
        at ZeroGgb.a(DashoA8113)
        at ZeroGgb.<init>(DashoA8113)
        at ZeroGfr.a(DashoA8113)
        at com.zerog.ia.installer.AAMgr.a(DashoA8113)
        at com.zerog.ia.installer.Main.d(DashoA8113)
        at com.zerog.ia.installer.Main.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
```
[B]
The How-To Solve[/B]

Firstly we are going to copy the installer to our harddisk like so (with making a directory for it etc):

```
mkdir ~/tmpmaple
cd /media/cdrom0
cp -a . ~/tmpmaple
cd ~/tmpmaple
chmod u+w Linux/Disk1/InstData/VM/LinuxInstaller.bin
```

We now need to edit one line in the installer file, you can either open the file with an editor like vi and navigate to line 2093 or use the simpler method of copying and pasting the below:

```
mv LinuxInstaller.bin LinuxInstaller.bin.bak
sed 's/export LD_ASSUME_KERNEL=2.2.5/#xport LD_ASSUME_KERNEL=2.2.5/' LinuxInstaller.bin.bak > LinuxInstaller.bin

```

Now simply navigate to the folder containing this file on your computer and execute the script like so:

```
sudo sh installMapleLinuxSU
```

The GUI installer should then begin and you shouldn't get any errors that stop you from installing or using package.

HTH

Calv

P.S. Once again all credit goes to **bmcage** & **dimis**

---

### Post by FizDev on 2006-10-12
Thanks! Worked flawlessly for me! :D

---

### Post by darqfaux on 2006-10-27
Awesome!! Worked like a charm! :-D

---

### Post by mrphd on 2006-12-29
Thanks very much for this. Now, however, I want to uninstall maple 9.5 as I have recently upgraded to version 10. There is an uninstall script in the directory where it is installed, but when i run it I get the following error:

```
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/root/maple9.5/Uninstall_Maple 9.5/../jre.IBM_INTEL_LINUX/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

I've replaced LD_ASSUME_KERNEL=2.2.5 with #xport LD_ASSUME_KERNEL=2.2.5 in the uninstall script but it doesn't help.

Any suggestions on how I might be able to get the uninstall script to work, or is it okay to just delete the directory?

Thanks!

---

### Post by reza81 on 2007-01-02
I have folowed the instructions above & get some arror about libc.so.6 as you can see hier below


```

reza@reza-desktop:~/tmpmaple$ sudo sh installMapleLinuxSU
Password:
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.12042/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
reza@reza-desktop:~/tmpmaple$ 


```

can anyone help me with this?

---

### Post by eschwalb on 2007-01-16
I've been trying to install Maple 9.5 in Edgy AMD 64 and this post got me most of the way there, but after following the instructions here, I was still getting this error:

"current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultInvocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)"

I found this which was helpful:  [http://ubuntuforums.org/showthread.php?t=40392&highlight=locale+set+CX](http://ubuntuforums.org/showthread.php?t=40392&highlight=locale+set+CX)

topindex's comment got the installer to run, as well as the application itself!

---

### Post by shak on 2007-02-02
THANK YOU !!!!! :D 

great solution

---

### Post by sammysam on 2007-02-25
i was able to install everthing, but when i try to run xmaple, i get the maple splashscreen, but maple never opens.  anybody come across this before?

---

### Post by calvinthomas on 2007-03-07
Sammysam, I just upgraded to Feisty and I am having this issue now aswell, did you come up with a solution?

Calv

---

