---
title: "JavaEE SDK Glassfish Update Tool problem"
date: 2014-07-04
forum: Programming Talk
---

### Post by khatkarrohit on 2014-07-04
I am trying to install the JAVAEE SDK. Installation went through and the grassfish server is running but when I run update tool I face the following problem. I have added the 32 bit archtitecture support. Installed many 32 bit pacakges but this problem is not solving. I am running Ubuntu 14.04 64 bit version.

```
Notebook-PC:~/javaee/glassfish4/updatetool/bin$ sh ./updatetool
WX import error.  Verify the WX widgets are in the PYTHONPATH.
The following can be reported to GlassFish Update Tool 2.3.5 Development Team <dev@updatecenter.java.net>.

Traceback (innermost last):
  File "/home/home/javaee/glassfish4/updatetool/vendor-packages/updatetool/common/boot.py", line 283, in init_app_locale
    import wx
  File "wx/__init__.py", line 45, in ?
  File "wx/_core.py", line 4, in ?
 ImportError: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

---

### Post by mireczatko on 2014-08-11
[LIST]
[*]Same problem here... Was this solved? Where can I find solution for the problem?
[*]Why is there prefix "[SOLVED]" in page title if it is not?
[*]Thank you,
[*]mirec
[/LIST]

---

### Post by khatkarrohit on 2014-08-11
This problem is caused by missing 32 bit libraries. I had to install lots of 32 bit libraries. I dont remember the exact packages I installed. I will try to find them in history later today.

 To solve problem for now, follow this procedure.

Whenever you see some error, install the 32 bit package which is causing error. Its easy to use Ubuntu Software Center or Synaptic Package Manager or if you don't find any package than Google it for right package name or command.

For example, the following error is caused by "libgtk-x11-2.0.so.0": 

```
ImportError: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

In this case install "libgtk-x11-2.0.so". After installing this there will be new error than install the missing package that caused error. Repeat this process till it stop showing you error messages.

---

### Post by jung_kim2 on 2014-08-11
Thanks!

---

### Post by mireczatko on 2014-08-13
Thank you, khatkarrohit!

!!! I just want to ask you all to be really careful if using [FONT=courier new]apt-get[/FONT] for installing new packages as it can cause removal of some other packages. I do not recommend to uninstall/remove anything...
On my Ubuntu 14.04 amd64 I did it exactly that wrong way and it almost damaged my system... Lot of packages were removed. Even unity and others... Fortunately, I was able to fix it with installing all removed packages back. All packages was listed in my previous "horrible" [FONT=courier new]apt-get -y[/FONT] as "will be removed".

---

### Post by khatkarrohit on 2014-08-13
In my case it did not removed anything. I usually stop when it says it will uninstall any package that I am not sure. There is always some other way around to do same thing. 

apt-get command and should not be run with -y yes option as in that case you can't stop it.

Just run sudo apt-get package-name 
Read what it says and then decide whether to proceed further or not.

You can test things in virtual machine like virtual box before installing on real system.

---

### Post by khatkarrohit on 2014-08-13
> **mireczatko said:**
> Thank you, khatkarrohit!

!!! I just want to ask you all to be really careful if using [FONT=courier new]apt-get[/FONT] for installing new packages as it can cause removal of some other packages. I do not recommend to uninstall/remove anything...
On my Ubuntu 14.04 amd64 I did it exactly that wrong way and it almost damaged my system... Lot of packages were removed. Even unity and others... Fortunately, I was able to fix it with installing all removed packages back. All packages was listed in my previous "horrible" [FONT=courier new]apt-get -y[/FONT] as "will be removed".

The following 3 commands are safe to run.
```
sudo dpkg --add-architecture i386
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 libjpeg62:i386  libpangoxft-1.0-0:i386 libpangox-1.0-0:i386 libsm6:i386 libidn11:i386

```

This is from the history of my PC. That day I ran all these commands.It also removed few things for me but I reinstalled those immediately before restarting my PC.
Below not all commands are safe to run. DO NOT RUN purge commands listed below. Not all commands are right but everything worked fine at the end.
```

sh ./updatetool
sudo apt-get install ia32-libs
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 
sh ./updatetool
sudo apt-get install libstdc++
sh ./updatetool
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386
sh ./updatetool
sudo apt-get install libglib2.0-0 
sudo apt-get install libglib2.0-0:386
sh ./updatetool
sudo apt-get install libudev0:i386
sudo apt-get install libudev1 
sh ./updatetool
sudo apt-get install libudev1:386
sh ./updatetool
sudo apt-get install ia32-libs
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
sudo apt-get install libgtk2.0-0:i386
sh ./updatetool
sudo apt-get purge libgtk2.0-0:i386
sudo apt-get install libcanberra-gtk-module:i386
sudo apt-get install gtk2-engines-murrine
sudo apt-get install gtk2-engines-murrine:i386
sudo apt-get install unity-gtk-module:i386 
sudo apt-get install overlay-scrollbar-gtk2:i386 
sudo apt-get install overlay-scrollbar:i386
sudo apt-get install overlay-scrollbar
sh ./updatetool
sudo apt-get install libgtk2.0-0:i386
sh ./updatetool
sudo apt-get install ia32-libs libglib2.0-dev
sudo apt-get install libgtk2.0-0
sudo aptitude reinstall libgtk2.0-0
sudo apt-get reinstall libgtk2.0-0
sudo apt-get install -reinstall libgtk2.0-0
sudo apt-get install --reinstall libgtk2.0-0
sh ./updatetool
sudo apt-get install --reinstall libgtk2.0-0
sh ./updatetool
sudo apt-get install --reinstall libpangox-1.0-0 
sh ./updatetool
sudo apt-get install --reinstall libpangox-1.0-dev 
sudo apt-get install --reinstall libpangox-1.0-0:386
sudo apt-get install --reinstall libpangox-1.0-0
sh ./updatetool
sudo apt-get install libpangox-1.0-0:i386 libpangoxft-1.0-0:i386
sh ./updatetool
sudo apt-get install libXxf86vm
sh ./updatetool
sudo apt-get install libjpeg
sh ./updatetool
sudo apt-get install libjpeg62:i386
sh ./updatetool
```

There may be few packages I installed from Ubuntu Software Centre. So they are not listed.

---

