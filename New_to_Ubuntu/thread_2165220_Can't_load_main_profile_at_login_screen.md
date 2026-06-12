---
title: "Can't load main profile at login screen"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by 34H8CTY on 2013-08-04
I was using my computer last night with no issues, today when I tried to log in, instead of loading the desktop I was faced with the login screen.
I ensured my username was selected and typed my password. The screen goes black for a moment and then come back to the login screen.
I instead tried to use remote login and was advised that my email or password were incorrect.
Guest seems to login with no issues.
I have therefore removed the password from my main account and set it to auto login, but to no avail.

I don't seem to have access to my main (administrator account).
Any ideas?

Update: It seems I can keep restarting and every now and then it will log in correctly, however when it does, my 2nd monitor will not connect and the keyboard seems to have some sort of Greek layout which is not listed in the Keyboard Layout Options - nothing I do there changes it back to English (US).

---

### Post by bapoumba on 2013-08-04
You may be running out of disk space in your /home folder.

Can you log into one of the TTY with <crtl><alt>F1 and run **df -h** to see the disk usage? If /home is full, you can run this from your /home folder to see which are the 10 largest files and make up some room.
```
du -hsx * | sort -rh | head -10
```
Or clean some of your Trash.

Other possibilities involve .ICEAuthority permissions, but you should have error messages.. [http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)

---

### Post by 34H8CTY on 2013-08-04
Thanks for your response.
I've not been able to work that screen properly, it wants me to log in, but won't accept the details I'm entering.
I've instead looked at the properties within the /Home folder (Right click > Properties) and it says I have around 94GB free of my 120GB drive.

Since then I've also unplugged the second monitor cable from the PCI card (main monitor is running from the M/Board) and it looks like it's loading correctly each time now. Plus the keyboard is using its correct layout constantly.

Is there a possibility having the cable connected to my 2nd monitor was interfering with it?
I recently tried to update the driver for the card (NVIDIA Geforce 8400 GS). I'm not sure if that worked correctly or not.
When that monitor is plugged in and the profile loads correctly, I click on the Display options in settings and it closes the window and throws up a message that Ubuntu had an error.

---

### Post by bapoumba on 2013-08-05
Hmm, is there some info in that error message ? Without it, it may be difficult to troubleshoot. I'm not much into video configs, I can move your thread to the Video forum if you wish.

---

### Post by 34H8CTY on 2013-08-05
[COLOR=#444444][FONT=Arial]There is, it says:
> Sorry, Ubuntu 13.04 has experienced an internal error.
If you notice further problems, try restarting the computer.
&#9660; ExecutablePath
     /usr/bin/gnome-control-center
&#9660; Package
     gnome-control-center 1:3.6.3-0ubuntu24.1
&#9660; ProblemType
     Crash
&#9660; Title
     [display]: gnome-control-center crashed with SIGABRT in raise()
&#9660; ApportVersion
     2.9.2-0ubuntu8.1
&#9660; Architecture
     amd64
&#9658; CoreDump
&#9660; CrashCounter
     1
&#9660; Date
     Tue Aug 6 09:55:42 2013
&#9658; Dependencies
&#9658; Disassembly
&#9660; DistroRelease
     Ubuntu 13.04
&#9660; InstallationDate
     Installed on 2013-07-28 (8 days ago)
&#9660; InstallationMedia
     Ubuntu 13.04 "Raring Ringtail@ - Release amd64 (20130424)
&#9660; MarkForUpload
     True
&#9660; PackageArchitecture
     amd64
&#9660; ProcCmdline
     gnome-control-center --overview
&#9658; ProcEnviron
&#9658; ProcMaps
&#9658; ProcStatus
&#9660; ProcVersionSignature
     Ubuntu 3.8.0-27.40-generic 3.8.13.4
&#9658; Registers
&#9660; Signal
     6
&#9660; SourcePackage
     gnome-control-center
&#9658; Stacktrace
&#9660; StacktraceAddressSignature
     /usr/bin/gnome-control-center:6:x86_64:/lib/x86_64-linux-gnu/libc-2.17.so+37037:/lib/x86_64-linux-gnu/libc-2.17.so+3a698:/lib/x86_64-linux-gnu/libglib-2.0.so.0.3600.0+6b3b6:/lib/x86_64-linux-gnu/libglib-2.0.so.0.3600.0+6b914:/usr/lib/libgnome-desktop-3.so.4.0.0+1c3e6:/usr/lib/libgnome-desktop-3.so.4.0.0+1c57d:/usr/lib/control-center-1/panels/libdisplay.so+a8b5:/usr/lib/control-center-1/panels/libdisplay.so+bf81:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3600.0+16ce1:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3600.0+174d0:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3600.0+17804:/usr/bin/gnome-control-center+9e8c:/usr/bin/gnome-control-center+7e47:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3600.0+10620:/usr/lib/x86_64-linux-gnu/libobject-2.0.so.0.3600.0+21f00
&#9658; StacktraceTop
&#9660; Tags
     raring display
&#9658; ThreadStacktrace
&#9660; Uname
     Linux 3.8.0-27-generic x86_64
&#9660; UnreportableReason
     You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

     gnupg, gpgv, libgcrypt11
&#9660; UpgradeStatus
     No upgrade log present (probably fresh install)
&#9660; UserGroups
     adm cdrom dip lpadmin nopasswdlogin plugdev sambashare sudo
&#9658; XsessionErrors
&#9658; usr_lib_gnome-control-center

Now having typed all that, I think I might have to update some packages...I'll post again if this has resolved it. (Perhaps I'll read the error before posting next time :-S )[/FONT][/COLOR]

---

### Post by bapoumba on 2013-08-06
Maybe you should check your sources.list : **cat /etc/apt/sources.list**. Please post it here, maybe you have an outdated repo or ppa or something that prevents the upgrade. Then you will be able to finish the update/upgrade process. Then we'll see :)

---

### Post by 34H8CTY on 2013-08-07
Actually, whilst trying to fix the issue, I killed the installation completely.
I ended up re-installing after removing the unnecessary graphics card.
All is working better than before now.

Thanks for your assistance.

---

### Post by bapoumba on 2013-08-07
Nice to see you got it to work.

The usual saying is that reinstalling is rarely an option, my saying is what works for you is the best :)

---

