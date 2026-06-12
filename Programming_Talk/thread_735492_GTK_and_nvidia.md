---
title: "GTK and nvidia"
date: 2008-03-25
forum: Programming Talk
---

### Post by Kzin on 2008-03-25
Hey there,
This is basically a thread to monitor progress at creating a program to quickly switch between nvidia twinview devices.  The [original thread]("http://ubuntuforums.org/showthread.php?t=615499") was located in the Desktop Environments category, but since this is becoming a little more code oriented I will move everything here.

**CURRENT WORKFLOW:**
Currently, when operating in a twinview scenario with two displays and one television there is no way to have all three enabled at once.  As a result, swapping between configurations is necessary.

Two primary methods have been suggested to accomplish this task.  One is to create xorg.conf files for each desired configuration, copy over the /etc/X11/xorg.conf file and restart X.  This is not an acceptable solution as it interferes with open work etc.  The other solution is to open nvidia-settings, disable one active device and enable the other.  Pressing apply will submit the changes to X "on the fly".  This is not an acceptable solution as... well, my girlfriend doesn't like it, and it truly isn't very user friendly.

**OBJECTIVE**
Create a script, program or applet to quickly swap between configurations without an X reboot.

**CAVEATS**
Only certain features will be able to be switched without an X reboot.  This is acceptable so long as you can disable the 2nd monitor and enable the TV on the fly (and back).

**PROGRESS**
I found the nvidia-settings source code [here]("ftp://download.nvidia.com/XFree86/nvidia-settings/").  I am using the 1.0 version as it is what is currently installed on my Gutsy release by default.
I found the relevant control to be in the file src/gtk+-2.x/ctkdisplayconfig.c
It would seem that the relevant nvidia function would be NvCtrlSetDisplayAttributeWithReply, located in src/libXNVCtrlAttributes/NvCtrlAttributes.c.

**MORE**
I am currently going through the limited documentation provided by nvidia.  I am posting this for people who have done this before, would like to contribute, want to monitor my (slow) progress, or know of another application that achieves the listed objective. Tnx all

:guitar:

PS Ignore the stupid subject for this thread, the wrapper is done for GTK so I was thinking GTK when I wrote it, the code is obviously in C.

---

### Post by Kiri on 2008-04-09
How's it going? 
I would also like to do this. Have you found a way?

---

### Post by brucewestfall on 2009-03-26
I am absolutely stumped on how to get nvidia-settings to work on the command line.  Right now, I've got 3 browsers open on 2 desktops - some with 3 or 4 tabs....

I found the source code, but cannot understand what to do.

I found the man page for nvidia-settings, which only gives 2 examples about assigning settings.

Has anyone found a way to decipher all this so that we can do what the nvidia-settings-user-guide.txt says:

"nvidia-settings has a rich commandline interface: all attributes that can be manipulated with the GUI can also be queried and set from the command line.  The commandline syntax for querying and assigning attributes matches that of the .nvidia-settings-rc configuration file."

I did all that stuff and cannot find anything about how to enable and disable twinview for my 2 identical monitors.

I would post all the things I've tried, but it might overload the server. ;)

Lookin' for HELP!

---

