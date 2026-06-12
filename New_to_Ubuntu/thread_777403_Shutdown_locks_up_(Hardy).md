---
title: "Shutdown locks up (Hardy)"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by rbc on 2008-05-01
I upgraded to Hardy two nights ago. Everything seemed to go fine. The computer boots OK, and Hardy loads OK, but freezes when shutting down. I’ve tried to shut down via GUI, and terminal, with the same result. The splash screen comes up, the progress bar goes blank, and then it locks up. The problem does not occur when I boot using the 2.6.22-14 kernel. I apologize if this is vague. Usually I know what the problem is, I just do not know how to fix it. In this case, I haven’t a clue even what information to provide to help with the diagnosis. I’m not sure if this is at all related but this message pops up shortly after logon: “Invalid problem report       This problem does not apply to a packaged program                      ( /usr/share/hplip/systray.py)”. I also have a Radeon X1300 graphics card. Again, I don’t know if that’s the problem. Just grasping at straws. Thanks to all

---

### Post by piousp on 2008-05-01
Did you enable the restricted driver for your ATI card??
Something similar happens to me after i enabled the driver.

---

### Post by rbc on 2008-05-01
Thanks for the hint. I should have mentioned that I tried that. It was enabled already. I tried disabling it, which made the screen resolution all wacky, and still did not help with shutdown

---

### Post by piousp on 2008-05-01
What happens if you go to a terminal (Ctrl + Alt + F1), kill de X, and then try to shutdown??

---

### Post by rbc on 2008-05-01
Same deal. I did Ctrl+Alt+F1, typed in my username and password, then typed "sudo shutdown -r 0". A bunch of commands run by, then it goes to the splash screen with blank progress bar

---

### Post by piousp on 2008-05-01
OK, i'm back. I'm just guessing here too.
Try to kill the X window before shuting down.
I do not know how to do that in gnome, but try this:

```

ps -eH

```

Then, kill the process. After that, try to shutdown.

---

### Post by rbc on 2008-05-02
OK. Now I'm back. Here's what ps -eH gives. What process should I kill, and how exactly?
 PID TTY          TIME CMD
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00   migration/0
    4 ?        00:00:00   ksoftirqd/0
    5 ?        00:00:00   watchdog/0
    6 ?        00:00:00   migration/1
    7 ?        00:00:00   ksoftirqd/1
    8 ?        00:00:00   watchdog/1
    9 ?        00:00:00   events/0
   10 ?        00:00:00   events/1
   11 ?        00:00:00   khelper
   47 ?        00:00:00   kblockd/0
   48 ?        00:00:00   kblockd/1
   51 ?        00:00:00   kacpid
   52 ?        00:00:00   kacpi_notify
  132 ?        00:00:00   kseriod
  174 ?        00:00:00   pdflush
  175 ?        00:00:00   pdflush
  176 ?        00:00:00   kswapd0
  217 ?        00:00:00   aio/0
  218 ?        00:00:00   aio/1
 1471 ?        00:00:00   ksuspend_usbd
 1472 ?        00:00:00   khubd
 1512 ?        00:00:00   ata/0
 1513 ?        00:00:00   ata/1
 1514 ?        00:00:00   ata_aux
 1527 ?        00:00:00   khpsbpkt
 2301 ?        00:00:00   knodemgrd_0
 2310 ?        00:00:00   scsi_eh_0
 2311 ?        00:00:00   scsi_eh_1
 2349 ?        00:00:00   scsi_eh_2
 2350 ?        00:00:00   scsi_eh_3
 2612 ?        00:00:00   kjournald
 3280 ?        00:00:00   kpsmoused
 4819 ?        00:00:00   kondemand/0
 4820 ?        00:00:00   kondemand/1
 5574 ?        00:00:00   btaddconn
 5575 ?        00:00:00   btdelconn
 5596 ?        00:00:00   krfcommd
    1 ?        00:00:02 init
 2814 ?        00:00:00   udevd
 4596 tty4     00:00:00   getty
 4597 tty5     00:00:00   getty
 4599 tty2     00:00:00   getty
 4602 tty3     00:00:00   getty
 4603 tty6     00:00:00   getty
 4782 ?        00:00:00   acpid
 4903 ?        00:00:00   syslogd
 4959 ?        00:00:00   dd
 4962 ?        00:00:00   klogd
 4984 ?        00:00:00   dbus-daemon
 5001 ?        00:00:00   NetworkManager
 5015 ?        00:00:00   NetworkManagerD
 5028 ?        00:00:00   system-tools-ba
 5047 ?        00:00:00   hald
 5112 ?        00:00:00     hald-runner
 5129 ?        00:00:00       hald-addon-hid-
 5131 ?        00:00:00       hald-addon-cpuf
 5132 ?        00:00:00       hald-addon-acpi
 5143 ?        00:00:00       hald-addon-inpu
 5153 ?        00:00:00       hald-addon-stor
 5162 ?        00:00:00       hald-addon-stor
 5050 ?        00:00:00   console-kit-dae
 5216 ?        00:00:00   gdm
 5219 ?        00:00:00     gdm
 5222 tty7     00:00:05       Xorg
 5371 tty7     00:00:00         Xorg
 5883 ?        00:00:00       x-session-manag
 5937 ?        00:00:00         seahorse-agent
 5946 ?        00:00:00         gnome-settings-
 5950 ?        00:00:00           pulseaudio
 5953 ?        00:00:00             gconf-helper
 5967 ?        00:00:00         metacity
 5968 ?        00:00:00         gnome-panel
 5970 ?        00:00:00         nautilus
 5984 ?        00:00:00         bluetooth-apple
 5987 ?        00:00:00         update-notifier
 5993 ?        00:00:00         tracker-applet
 5994 ?        00:00:00         evolution-alarm
 6003 ?        00:00:00         python
 6005 ?        00:00:00         nm-applet
 5305 ?        00:00:00   avahi-daemon
 5306 ?        00:00:00     avahi-daemon
 5360 ?        00:00:00   cupsd
 5417 ?        00:00:00   atieventsd
 5540 ?        00:00:00   dhcdbd
 5788 ?        00:00:00     dhclient
 5566 ?        00:00:00   hcid
 5586 ?        00:00:00     bluetoothd-serv
 5587 ?        00:00:00     bluetoothd-serv
 5620 ?        00:00:00   anacron
 5634 ?        00:00:00   atd
 5650 ?        00:00:00   cron
 5755 tty1     00:00:00   getty
 5878 ?        00:00:00   gconfd-2
 5881 ?        00:00:00   gnome-keyring-d
 5945 ?        00:00:00   dbus-daemon
 5962 ?        00:00:00   gnome-screensav
 5977 ?        00:00:00   bonobo-activati
 5980 ?        00:00:00   gvfsd
 5999 ?        00:00:00   trackerd
 6004 ?        00:00:00   gnome-volume-ma
 6007 ?        00:00:00   gnome-power-man
 6024 ?        00:00:00   evolution-excha
 6032 ?        00:00:00   gvfsd-burn
 6035 ?        00:00:00   gvfsd-trash
 6043 ?        00:00:00   modem_applet
 6049 ?        00:00:00   gnome-netstatus
 6051 ?        00:00:00   mixer_applet2
 6080 ?        00:00:06   firefox
 6158 ?        00:00:00   gnome-terminal
 6161 ?        00:00:00     gnome-pty-helpe
 6162 pts/0    00:00:00     bash
 6179 pts/0    00:00:00       ps

---

### Post by piousp on 2008-05-02
OK, too kill a process you type the command

```
kill
```

Before you use it, read its man page

```
man kill
```

If you dont get how to use it, just tell me and i'll help you out.

By the way, there's a thread on how to kill the X server. Let me check while you do your homework ;)

---

### Post by piousp on 2008-05-02
I'm going to refer you for now at [this thread]("http://http://ubuntuforums.org/showthread.php?t=774237")

---

### Post by piousp on 2008-05-02
Ok, i found how to kill x in gnome. At the end, you wont need to mess around 'kill'. Lucky you.

Anyway, here is how:

Before shuting down, press and hold CTRL + ALT + F1 to go to terminal 1. Once there, type this:

```
sudo /etc/init.d/gdm stop
```

If you want to "revive it", just type:
```
sudo /etc/init.d/gdm start
```

Now, once the X is no longer active, try to shutdown.
Also, try to check the other threads i gave you, they may have a solution for you too.

---

