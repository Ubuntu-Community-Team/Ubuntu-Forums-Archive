---
title: "Ubuntu 16.06 doesn't start after last update"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by rubeto on 2017-02-11
Hello, 
this is my first post and i am a newbie :D.

I've been using Ubuntu 16.04 for a few moths and everything works nice since now. I run yesterday apt get update && apt get upgrade and turn off my pc. When i try to turn on today Ubuntu doesn't start. It shows a black screen with five dots in color after grub. I try to run on recovery mode and this is the result of apt's history (/var/log/apt/history.log):

 ```
Start-Date: 2017-02-10  17:20:09
Commandline: apt-get upgrade
Requested-By: evotarubeto (1000)
Upgrade: gstreamer1.0-plugins-ugly-amr:amd64 (1.8.2-1ubuntu0.1, 1.8.3-1ubuntu0.1), gstreamer1.0-alsa:amd64 (1.8.2-1ubuntu0.2, 1.8.3-1ubuntu0.1), libgles2-mesa:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), libdrm-nouveau2:amd64 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), libdrm-nouveau2:i386 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), os-prober:amd64 (1.70ubuntu3, 1.70ubuntu3.3), gstreamer1.0-plugins-base-apps:amd64 (1.8.2-1ubuntu0.2, 1.8.3-1ubuntu0.1), gstreamer1.0-tools:amd64 (1.8.2-1~ubuntu1, 1.8.3-1~ubuntu0.1), gstreamer1.0-plugins-good:amd64 (1.8.2-1ubuntu0.3, 1.8.3-1ubuntu0.3), libglapi-mesa:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), libglapi-mesa:i386 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), sudo:amd64 (1.8.16-0ubuntu1.2, 1.8.16-0ubuntu1.3), console-setup-linux:amd64 (1.108ubuntu15.2, 1.108ubuntu15.3), libxatracker2:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), console-setup:amd64 (1.108ubuntu15.2, 1.108ubuntu15.3), libegl1-mesa:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), gstreamer1.0-plugins-base:amd64 (1.8.2-1ubuntu0.2, 1.8.3-1ubuntu0.1), libklibc:amd64 (2.0.4-8ubuntu1.16.04.2, 2.0.4-8ubuntu1.16.04.3), libwxgtk3.0-0v5:amd64 (3.0.2+dfsg-1.3, 3.0.2+dfsg-1.3ubuntu0.1), libgstreamer-plugins-good1.0-0:amd64 (1.8.2-1ubuntu0.3, 1.8.3-1ubuntu0.3), gstreamer1.0-pulseaudio:amd64 (1.8.2-1ubuntu0.3, 1.8.3-1ubuntu0.3), libgbm1:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), krb5-locales:amd64 (1.13.2+dfsg-5ubuntu1, 1.13.2+dfsg-5ubuntu2), libdrm-amdgpu1:amd64 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), libdrm-amdgpu1:i386 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), im-config:amd64 (0.29-1ubuntu12.3, 0.29-1ubuntu12.4), libwayland-egl1-mesa:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), libgstreamer-plugins-base1.0-0:amd64 (1.8.2-1ubuntu0.2, 1.8.3-1ubuntu0.1), libdrm2:amd64 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), libdrm2:i386 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), gstreamer1.0-x:amd64 (1.8.2-1ubuntu0.2, 1.8.3-1ubuntu0.1), appmenu-qt5:amd64 (0.3.0+16.04.20151130-0ubuntu1, 0.3.0+16.04.20151130-0ubuntu2), libwxbase3.0-0v5:amd64 (3.0.2+dfsg-1.3, 3.0.2+dfsg-1.3ubuntu0.1), gir1.2-gst-plugins-base-1.0:amd64 (1.8.2-1ubuntu0.2, 1.8.3-1ubuntu0.1), libgl1-mesa-dri:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), libgl1-mesa-dri:i386 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), keyboard-configuration:amd64 (1.108ubuntu15.2, 1.108ubuntu15.3), gstreamer1.0-libav:amd64 (1.8.2-1~ubuntu1, 1.8.3-1ubuntu0.1), libgl1-mesa-glx:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), libgl1-mesa-glx:i386 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), libdrm-intel1:amd64 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), libdrm-intel1:i386 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), gir1.2-gstreamer-1.0:amd64 (1.8.2-1~ubuntu1, 1.8.3-1~ubuntu0.1), libdrm-radeon1:amd64 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), libdrm-radeon1:i386 (2.4.67-1ubuntu0.16.04.2, 2.4.70-1~ubuntu16.04.1), mesa-vdpau-drivers:amd64 (11.2.0-1ubuntu2.2, 12.0.6-0ubuntu0.16.04.1), linux-firmware:amd64 (1.157.6, 1.157.8), klibc-utils:amd64 (2.0.4-8ubuntu1.16.04.2, 2.0.4-8ubuntu1.16.04.3), libgstreamer1.0-0:amd64 (1.8.2-1~ubuntu1, 1.8.3-1~ubuntu0.1), base-files:amd64 (9.4ubuntu4.3, 9.4ubuntu4.4), gstreamer1.0-plugins-ugly:amd64 (1.8.2-1ubuntu0.1, 1.8.3-1ubuntu0.1)
End-Date: 2017-02-10  17:20:58
```

If i disable 'quiet splash' on grub Ubuntu starts on console mode but i cannot see why doesn't start normally.

On start it shows 'FAILED TO START LIGHT DISPLAY MANAGER' so i run 
```
systemctl status lightdm.service
``` and this is the result:

```
&#9679; lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/display-manager.service.d
           &#9492;&#9472;xdiagnose.conf
   Active: failed (Result: resources) since sáb 2017-02-11 09:16:15 CET; 1min 17s ago
     Docs: man:lightdm(1)
  Process: 1436 ExecStart=/usr/sbin/lightdm (code=exited, status=1/FAILURE)
  Process: 1429 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exited, status=0/SUCCESS)
 Main PID: 1436 (code=exited, status=1/FAILURE)

feb 11 09:16:15 evotarubeto-Ubuntu systemd[1]: lightdm.service: Service hold-off time over, scheduling restart.
feb 11 09:16:15 evotarubeto-Ubuntu systemd[1]: lightdm.service: Failed to schedule restart job: Transaction is destructive.
feb 11 09:16:15 evotarubeto-Ubuntu systemd[1]: lightdm.service: Unit entered failed state.
feb 11 09:16:15 evotarubeto-Ubuntu systemd[1]: lightdm.service: Triggering OnFailure= dependencies.
feb 11 09:16:15 evotarubeto-Ubuntu systemd[1]: lightdm.service: Failed with result 'resources'.
```

journalctl shows:

```
-- Logs begin at sáb 2017-02-11 09:49:25 CET, end at sáb 2017-02-11 09:50:11 CET. --
feb 11 09:49:26 evotarubeto-Ubuntu systemd[1]: Starting Light Display Manager...
feb 11 09:49:26 evotarubeto-Ubuntu systemd[1]: lightdm.service: Main process exited, code=exited, status=1/FAILURE
feb 11 09:49:26 evotarubeto-Ubuntu systemd[1]: Failed to start Light Display Manager.
feb 11 09:49:26 evotarubeto-Ubuntu systemd[1]: lightdm.service: Unit entered failed state.
feb 11 09:49:26 evotarubeto-Ubuntu systemd[1]: lightdm.service: Triggering OnFailure= dependencies.
feb 11 09:49:26 evotarubeto-Ubuntu systemd[1]: lightdm.service: Failed with result 'exit-code'.
feb 11 09:49:27 evotarubeto-Ubuntu systemd[1]: lightdm.service: Service hold-off time over, scheduling restart.
feb 11 09:49:27 evotarubeto-Ubuntu systemd[1]: lightdm.service: Failed to schedule restart job: Transaction is destructive.
feb 11 09:49:27 evotarubeto-Ubuntu systemd[1]: lightdm.service: Unit entered failed state.
feb 11 09:49:27 evotarubeto-Ubuntu systemd[1]: lightdm.service: Triggering OnFailure= dependencies.
feb 11 09:49:27 evotarubeto-Ubuntu systemd[1]: lightdm.service: Failed with result 'resources'.
```

Not sure what's going on.

What can i do? 

Thank you!

---

### Post by Bashing-om on 2017-02-11
rubeto; Hello; Welcome to the forum .

Suspect is that the graphic's driver got broke in the upgrade process .
Re-boot the system and at the login screen key combo ctl+alt+F1 to gain a (C)ommand (L)ine ) (I)nterface.
Log in here with username and pass word - there will be no response to the screen when password is entered . enter the pass word blindly and hit the enter key.

If you can log into the system then that indicates the issue is in the X layer :)
Let's see what X relates - as you do not have the amenities of a terminal emulator in this interface, let us resort to a pastebin site to see this log file.
In this terminal execute terminal command:
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```
the result is a URL back in terminal. pass that link back here and we can access the generated file.
Then we see where we go from what X relates . - maybe as simple as re-installing the driver ??


[INDENT][INDENT]we put the pieces back together
[/INDENT][/INDENT]

---

### Post by rubeto on 2017-02-12
Thank you Bashing-om for your response[B].
[/B]
The result for 

```
cat /var/log/Xorg.0.log | nc termbin.com 9999
```

is: [http://termbin.com/hc8i](http://termbin.com/hc8i)

If i need to re-install the driver i will be very grateful if you tell me how to do that through command line

R.

---

### Post by Bashing-om on 2017-02-12
rubeto; Well !

I do not see see a problem in X in and of it's self .. looks to be happy .
We have hybrid graphics, now the questions are if the config file is consistent and what is controlling the graphic's sets.
Pastebin:
```

cat /var/log/Xorg.0.log | nc termbin.com 9999
dpkg -l | grep -i nvidia | nc termbin.com 9999

```

Also, is this only in "your" account that the GUI fails to start ?
what results when you boot the guest account form the login screen ?

[INDENT][INDENT]process of fault isolation
[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rubeto on 2017-02-12
Hi George,

After grubs runs the screen frezzes, it does not reach login screen so i cannot test guest account.

This are the results of Xorg.0.log and dpkg:

[http://termbin.com/caar](http://termbin.com/caar)

[http://termbin.com/nx16](http://termbin.com/nx16)

Thank you,
Rubén

---

### Post by Bashing-om on 2017-02-12
rubeto; Well !

That says the driver is not fully installed !
we do in that F1 terminal:
```

sudo apt purge nvidia*
sudo rm /etc/X11/Xorg.conf
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
Reboot for the install of the driver to take full effect.
Now do "you" boot to the GUI ?



[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by rubeto on 2017-02-13
Ir works!! 
Now GUI starts and i can see my desktop (i have auto login activaded) but... my keyboard and mouse do not work... i tried to ctrl+alt+F1 after grub but nothing seems to happen...

Ruben

---

### Post by wildmanne39 on 2017-02-13
If your booting issue is fixed please use thread tools at the top of the page to mark this thread solved and start a new thread for your other issue.
Thanks

---

