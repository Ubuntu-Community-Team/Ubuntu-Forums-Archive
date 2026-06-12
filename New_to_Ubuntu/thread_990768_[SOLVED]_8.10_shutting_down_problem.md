---
title: "[SOLVED] 8.10 shutting down problem"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by fedex1993 on 2008-11-23
Well it seems after i finally got ibex up and running good i now cant seem to shutdown with at all ecept by holding down power button. Is there a way that i can fix this?

---

### Post by mbsullivan on 2008-11-23
What's it do, does it just hang @ the splash screen?

Mike

---

### Post by fedex1993 on 2008-11-23
yeah hangs on the splash screen.

---

### Post by drubin on 2008-11-23
Try this [http://ubuntuforums.org/showpost.php?p=5917737&postcount=6](http://ubuntuforums.org/showpost.php?p=5917737&postcount=6) and post the output.

---

### Post by mbsullivan on 2008-11-25
> Try this [http://ubuntuforums.org/showpost.php...37&postcount=6](http://ubuntuforums.org/showpost.php...37&postcount=6) and post the output.

Nice one!

If you don't like the splash screen and want to see for yourself where it hangs, you can always get rid of it by editing /boot/grub/menu.lst and changing the following line:

```
# defoptions=quiet splash
```

to read:

```
# defoptions=
```

Then, run:

```
sudo update-grub
```

Basically, before you can tell what to fix, you must see where it has a problem and what output it gives.

Mike

---

### Post by Keen101 on 2008-11-25
I agree with mbsullivan. But, i like to see the splash screen and the extra stuff in the background. Ubuntu used to actually show the startup scripts and stuff in an older version, but they took it out for some reason. It can be very helpful. I configure mine like this though.

sudo gedit /boot/grub/menu.lst


GRUB before:
> 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=90ee8ca9-a49a-458f-a4c1-8a97c89a073f **ro quiet splash**


GRUB after:
> 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=90ee8ca9-a49a-458f-a4c1-8a97c89a073f **ro splash**

---

### Post by fedex1993 on 2008-11-25
i already fixed the problem :\

---

### Post by siliconut on 2008-11-25
hi, 
i don't know if its related, but i have a similar problem. 
i hav a toshiba techra 8100, and its got ubuntu 8.10 on it. 

it works fine, but when i shutdown it:
closes the desktop
shows just the background (as normal)

it then goes to the screen with the ubuntu logo, and the scroll bar thing that gets smaller and smaller
then once it has no orange stuff in it, indicating its ready to power off or watever, 
it stops doing anything.  


its like all it has to do now is turn its screen off.. but it doesnt. and it just stays on that screen for an eternity, until i hold down the power key.. 

any help? thanks

---

### Post by siliconut on 2008-11-25
also possible related, 

when i click hibernate.. 

it leaves the desktop.. 
goes to this screen.. with writing.. something about device 0000:00:00.0 failed to thaw. error -16

then a new line apears:
Power Down


but it doesnt power down, again it waits like this until i eventually hold down on button to manually shut it down.. 

thanks for help :)

---

### Post by mbsullivan on 2008-11-25
> i already fixed the problem :\

What was it? The answer might help other people.

> 
it then goes to the screen with the ubuntu logo, and the scroll bar thing that gets smaller and smaller
then once it has no orange stuff in it, indicating its ready to power off or watever,
it stops doing anything. 

Hi siliconut,

Would you follow the instructions earlier in the thread and report what the last thing that runs (before freezing) is?

Try posting the output of [this]("http://ubuntuforums.org/showpost.php?p=5917737&postcount=6"), courtesy of Drubin.

Mike

---

### Post by siliconut on 2008-11-26
haha.. ok.. im still a n00b to how the engine behind linux works.. do i have to open a 'terminal' thing to enter those codes?

---

### Post by mbsullivan on 2008-11-26
> haha.. ok.. im still a n00b to how the engine behind linux works.. do i have to open a 'terminal' thing to enter those codes?

Okay... Goto Applications->Terminal, paste the code in, and press enter.

Working from the command line is pretty imperative in Linux, especially when working with these forums (because it's much easier to paste a command than to describe how to do steps in a GUI :) ).

Here's a quick breakdown of what the command does:

```
sudo shutdown -vh now >> /var/log/shutdown.log 2>&1
```

**sudo** - short for "super-user do", allows you to execute a command whose permissions prevent anybody but "root" from running it. Will ask for an administrative password.

**shutdown -vh** - shutdown, halting or powering down the system, giving verbose output.

**now** - you provide a time to "shutdown" to tell it when to shut the machine down. Obviously, "now" shuts it down immeadiately.

**>> /var/log/shutdown.log** Redirects the textual output of the shutdown command to the end of /var/log/shutdown.log. This is what will allow you to see the output once you restart your computer. **Post this file** once you reboot.

**2>&1** I know this part looks complicated, but basically it says to redirect text that is output in the standard error stream (used for errors, typically) to the standard output stream (used for non-errors, typically). This will make sure that you log EVERYTHING that is given by the program, not just the non-error text.

Hope this helps!
Mike

---

### Post by drubin on 2008-11-26
> **mbsullivan said:**
> Okay... Goto Applications->Terminal, paste the code in, and press enter.

Working from the command line is pretty imperative in Linux, especially when working with these forums (because it's much easier to paste a command than to describe how to do steps in a GUI :) ).

Here's a quick breakdown of what the command does:

```
sudo shutdown -vh now >> /var/log/shutdown.log 2>&1
```

**sudo** - short for "super-user do", allows you to execute a command whose permissions prevent anybody but "root" from running it. Will ask for an administrative password.

**shutdown -vh** - shutdown, halting or powering down the system, giving verbose output.

**now** - you provide a time to "shutdown" to tell it when to shut the machine down. Obviously, "now" shuts it down immeadiately.

**>> /var/log/shutdown.log** Redirects the textual output of the shutdown command to the end of /var/log/shutdown.log. This is what will allow you to see the output once you restart your computer. **Post this file** once you reboot.

**2>&1** I know this part looks complicated, but basically it says to redirect text that is output in the standard error stream (used for errors, typically) to the standard output stream (used for non-errors, typically). This will make sure that you log EVERYTHING that is given by the program, not just the non-error text.

Hope this helps!
Mike

Thanks for explaining my command I never had a chance when I wrote it a while ago. :)

---

### Post by dondad on 2008-11-26
> **siliconut said:**
> hi, 
i don't know if its related, but i have a similar problem. 
i hav a toshiba techra 8100, and its got ubuntu 8.10 on it. 

it works fine, but when i shutdown it:
closes the desktop
shows just the background (as normal)

it then goes to the screen with the ubuntu logo, and the scroll bar thing that gets smaller and smaller
then once it has no orange stuff in it, indicating its ready to power off or watever, 
it stops doing anything.  


its like all it has to do now is turn its screen off.. but it doesnt. and it just stays on that screen for an eternity, until i hold down the power key.. 

any help? thanks

I had the same problem with a Dell computer. Putting reboot=b at the end of the grub boot line fixed it. The command returns the reboot control to the bios. Might be worth a try in your case.

---

### Post by siliconut on 2008-11-26
ok, i am getting more familiar with the terminal language, as i was trying to connect my netgear wg511t wireless adaptor before (without luck.. but thats another story).

i put in:
sudo shutdown -vh now >> /var/log/shutdown.log 2>&1 

and it replied:
bash: /var/log/shutdown.log: Permission denied

i thought the sudop part gave me permissions.. and if it wasnt sure if it was still me on the computer( hadn't put the password in for a while) then it would ask for it again..? :confused:

thanks.

---

### Post by mbsullivan on 2008-11-27
> i put in:
sudo shutdown -vh now >> /var/log/shutdown.log 2>&1

and it replied:
bash: /var/log/shutdown.log: Permission denied

i thought the sudop part gave me permissions.. and if it wasnt sure if it was still me on the computer( hadn't put the password in for a while) then it would ask for it again..? 

Haha, you're right, the sudo part does give you permissions. With the redirect, you'll probably have to enter shell mode, which will allow you to operate as if you were the user "root" (this is only because we're chaining multiple commands with >>):

```
sudo -s 
shutdown -vh now >> /var/log/shutdown.log 2>&1
```

Sorry about that... I would've tested it, but I didn't really want to shut my computer down right then.

> Thanks for explaining my command I never had a chance when I wrote it a while ago. 

No problem! Thanks for the command. I'll be sure to keep it around.

> Putting reboot=b at the end of the grub boot line fixed it. The command returns the reboot control to the bios. Might be worth a try in your case.

Hmm... this might be worth a try... the best way to do this is similar to the procedure I described above for disabling the splash screen. 

(1) edit /boot/grub/menu.lst and append "reboot=b" at the end of the following line:

```
# defoptions= ...
```

(2) then run:

```
sudo update-grub
```

Mike

---

### Post by siliconut on 2008-12-06
ok i did that, and it shutdown when i hit return. it shutdown like it has been - stopping at the end..

i started it up and read the shutdown.log file, but it had no text in it at all.. does this mean i could have entered it incorrectly into the terminal? 
thanks

---

### Post by drubin on 2008-12-06
> **siliconut said:**
> ok i did that, and it shutdown when i hit return. it shutdown like it has been - stopping at the end..

i started it up and read the shutdown.log file, but it had no text in it at all.. does this mean i could have entered it incorrectly into the terminal? 
thanks

I assume you ran the scrip posted here, and not this [one]("http://ubuntuforums.org/showpost.php?p=5918695&postcount=8")?

---

### Post by siliconut on 2008-12-06
> **drubin said:**
> I assume you ran the scrip posted here, and not this [one]("http://ubuntuforums.org/showpost.php?p=5918695&postcount=8")?

ok, i'll try that one now. Do i use gedit to create the .sh file?

---

### Post by drubin on 2008-12-06
> **siliconut said:**
> ok, i'll try that one now. Do i use gedit to create the .sh file?

You can use any editor you choose :), Just remember to give it execute permisions, Right click on the file and permissions tab.

---

### Post by drubin on 2008-12-06
> **mbsullivan said:**
> Haha, you're right, the sudo part does give you permissions. With the redirect, you'll probably have to enter shell mode, which will allow you to operate as if you were the user "root" (this is only because we're chaining multiple commands with >>):

```
sudo -s 
shutdown -vh now >> /var/log/shutdown.log 2>&1
```

Sorry about that... I would've tested it, but I didn't really want to shut my computer down right then.


I can't see how sudo -s giving you the root shell is different from prefixing sudo to the command? 

Could some one please explain the reason for the permission issues...

I understand the differences between sudo -i and sudo -s but why would sudo command be different

---

### Post by mbsullivan on 2008-12-07
> I can't see how sudo -s giving you the root shell is different from prefixing sudo to the command?

Could some one please explain the reason for the permission issues...

I understand the differences between sudo -i and sudo -s but why would sudo command be different 

I'd have to do more research to figure out exactly what's going on, but I could hand wave something right now. I think with the first command:

```

sudo shutdown -vh now >> /var/log/shutdown.log 2>&1

```

The sudo was applying only to the first command, such that if we wrote it with parenthesis meaning things applied with permission, it would be:


```

(sudo shutdown -vh now) >> /var/log/shutdown.log 2>&1

```

Once you're logged in as root, (obviously) the whole thing is run with permissions:

```
sudo -s 
(shutdown -vh now >> /var/log/shutdown.log 2>&1)
```

There's probably some way to make sudo apply permissions to a chain of commands. However, I don't know if off of the top of my head. One hackish way to do it would be:

```
sudo sh -c "shutdown -vh now >> /var/log/shutdown.log 2>&1"
```

There's probably a better way, though. Anybody know?

Mike

PS: siliconut, have  you had any luck debugging your problem? What's your status?

---

### Post by drubin on 2008-12-07
> drubin@gizmo:/root$ sudo echo "asdf" >/root/file
bash: /root/file: Permission denied


I am shocked and amazed. Never knew this. When reading your post I had to ask others and test it to make sure. :)  (I kinda thought my system as broken)

---

### Post by siliconut on 2008-12-09
woo hoo! it finally wrote to the log file. :)
i did the method of creating that .sh file, and entering:

sudo ~/Desktop/myshudown.sh

andd i'll put up what was in the shutdown.log file asap, but its long as so i'll post it directly from the computer in question.

---

### Post by siliconut on 2008-12-10
ok, i've got the jog file - this is what iyt ccontained:

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 18:46 ?        00:00:02 /sbin/init
root         2     0  0 18:46 ?        00:00:00 [kthreadd]
root         3     2  0 18:46 ?        00:00:00 [migration/0]
root         4     2  0 18:46 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 18:46 ?        00:00:00 [watchdog/0]
root         6     2  0 18:46 ?        00:00:00 [events/0]
root         7     2  0 18:46 ?        00:00:00 [khelper]
root        46     2  0 18:46 ?        00:00:00 [kintegrityd/0]
root        48     2  0 18:46 ?        00:00:00 [kblockd/0]
root        67     2  0 18:46 ?        00:00:00 [cqueue]
root        71     2  0 18:46 ?        00:00:00 [kseriod]
root       121     2  0 18:46 ?        00:00:00 [pdflush]
root       122     2  0 18:46 ?        00:00:00 [pdflush]
root       123     2  0 18:46 ?        00:00:00 [kswapd0]
root       167     2  0 18:46 ?        00:00:00 [aio/0]
root       176     2  0 18:46 ?        00:00:00 [kpnpbiosd]
root      1037     2  0 18:46 ?        00:00:00 [ksuspend_usbd]
root      1038     2  0 18:46 ?        00:00:00 [khubd]
root      1045     2  0 18:46 ?        00:00:00 [ata/0]
root      1047     2  0 18:46 ?        00:00:00 [ata_aux]
root      1107     2  0 18:46 ?        00:00:00 [scsi_eh_0]
root      1108     2  0 18:46 ?        00:00:00 [scsi_eh_1]
root      1868     2  0 18:46 ?        00:00:00 [kjournald]
root      2042     1  0 18:46 ?        00:00:01 /sbin/udevd --daemon
root      2204     2  0 18:47 ?        00:00:00 [pccardd]
root      2215     2  0 18:47 ?        00:00:00 [pccardd]
root      2231     2  0 18:47 ?        00:00:00 [kpsmoused]
root      2509     2  0 18:47 ?        00:00:00 [kgameportd]
root      3825     1  0 18:47 tty4     00:00:00 /sbin/getty 38400 tty4
root      3826     1  0 18:47 tty5     00:00:00 /sbin/getty 38400 tty5
root      3835     1  0 18:47 tty2     00:00:00 /sbin/getty 38400 tty2
root      3837     1  0 18:47 tty3     00:00:00 /sbin/getty 38400 tty3
root      3839     1  0 18:47 tty6     00:00:00 /sbin/getty 38400 tty6
root      3912     2  0 18:47 ?        00:00:00 [kondemand/0]
syslog    3995     1  0 18:47 ?        00:00:00 /sbin/syslogd -u syslog
root      4049     1  0 18:47 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4051     1  0 18:47 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4074     1  0 18:47 ?        00:00:00 /bin/dbus-daemon --system
avahi     4096     1  0 18:47 ?        00:00:00 avahi-daemon: running [linuxlaptop2.local]
avahi     4097  4096  0 18:47 ?        00:00:00 avahi-daemon: chroot helper
root      4107     2  0 18:47 ?        00:00:00 [kapmd]
root      4121     1  0 18:47 ?        00:00:00 /usr/sbin/apmd -P /etc/apm/apmd_proxy --proxy-timeout 30
root      4160     1  0 18:47 ?        00:00:00 /usr/sbin/cupsd
111       4228     1  0 18:47 ?        00:00:01 /usr/sbin/hald
root      4231     1  0 18:47 ?        00:00:00 /usr/sbin/console-kit-daemon
root      4294  4228  0 18:47 ?        00:00:00 hald-runner
root      4323  4294  0 18:47 ?        00:00:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      4340  4294  0 18:47 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1
root      4366     1  0 18:47 ?        00:00:00 /usr/sbin/bluetoothd
root      4371     2  0 18:47 ?        00:00:00 [btaddconn]
root      4373     2  0 18:47 ?        00:00:00 [btdelconn]
root      4385     2  0 18:47 ?        00:00:00 [krfcommd]
root      4419     1  0 18:47 ?        00:00:00 /usr/sbin/NetworkManager
root      4428     1  0 18:47 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      4431     1  0 18:47 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      4459     1  0 18:47 ?        00:00:00 /usr/sbin/gdm
root      4462  4459  0 18:47 ?        00:00:00 /usr/sbin/gdm
root      4466  4462  1 18:47 tty7     00:00:19 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      4482     1  0 18:47 ?        00:00:00 /usr/bin/system-tools-backends
root      4501     1  0 18:47 ?        00:00:00 /usr/sbin/anacron -s
daemon    4517     1  0 18:47 ?        00:00:00 /usr/sbin/atd
root      4545     1  0 18:47 ?        00:00:00 /usr/sbin/cron
root      4647     1  0 18:47 tty1     00:00:00 /sbin/getty 38400 tty1
1000      4669  4462  0 18:47 ?        00:00:00 x-session-manager
1000      4786  4669  0 18:47 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
1000      4789     1  0 18:47 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
1000      4790     1  0 18:47 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
1000      4793     1  0 18:47 ?        00:00:00 /usr/bin/pulseaudio -D --log-target=syslog
1000      4796  4793  0 18:47 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
1000      4798     1  0 18:47 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2
1000      4804  4669  0 18:47 ?        00:00:00 /usr/bin/seahorse-agent --execute x-session-manager
1000      4809  4669  0 18:47 ?        00:00:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
1000      4811     1  0 18:47 ?        00:00:00 /usr/bin/gnome-keyring-daemon
1000      4813     1  0 18:47 ?        00:00:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
1000      4814  4669  0 18:47 ?        00:00:02 /usr/bin/metacity --replace
1000      4834     1  0 18:47 ?        00:00:00 /usr/lib/gvfs/gvfsd
1000      4840  4669  0 18:47 ?        00:00:06 gnome-panel
1000      4843     1  0 18:47 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/linuxlaptop/.gvfs
1000      4848  4669  0 18:47 ?        00:00:05 nautilus --no-desktop --browser
1000      4850     1  0 18:47 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
1000      4869     1  0 18:47 ?        00:00:03 gnome-screensaver
1000      4871     1  0 18:47 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
1000      4873     1  0 18:47 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
1000      4877     1  0 18:47 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=20
1000      4881     1  0 18:48 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.13 /org/gtk/gvfs/exec_spaw/0
1000      4883  4669  0 18:48 ?        00:00:00 trackerd
1000      4885     1  0 18:48 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.13 /org/gtk/gvfs/exec_spaw/1
1000      4890  4669  0 18:48 ?        00:00:01 nm-applet --sm-disable
1000      4898  4669  0 18:48 ?        00:00:00 update-notifier
1000      4899  4669  0 18:48 ?        00:00:00 python /usr/share/system-config-printer/applet.py
1000      4900  4669  0 18:48 ?        00:00:00 tracker-applet
1000      4901  4669  0 18:48 ?        00:00:00 /usr/lib/evolution/2.24/evolution-alarm-notify
1000      4902  4669  0 18:48 ?        00:00:00 bluetooth-applet
1000      4906     1  0 18:48 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=21
1000      4909     1  0 18:48 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=28
1000      4912     1  0 18:48 ?        00:00:00 gnome-power-manager
1000      4983     1  0 18:49 ?        00:00:00 /usr/lib/notification-daemon/notification-daemon
root      5063  4501  0 18:52 ?        00:00:00 /bin/sh -c nice run-parts --report /etc/cron.daily
root      5064  5063  0 18:52 ?        00:00:00 run-parts --report /etc/cron.daily
root      5075  5064  0 18:52 ?        00:00:00 /bin/sh /etc/cron.daily/apt
root      5115  5075  0 19:01 ?        00:00:00 sleep 539
1000      5136     1  1 19:04 ?        00:00:01 gnome-terminal
1000      5138  5136  0 19:04 ?        00:00:00 gnome-pty-helper
1000      5139  5136  0 19:04 pts/0    00:00:00 bash
root      5159  5139  0 19:05 pts/0    00:00:00 /bin/bash /home/linuxlaptop/Desktop/myshutdown.sh
root      5160  5159  0 19:05 pts/0    00:00:00 ps -ef
------ MARK-----


yee. thanks foro your helpj

---

### Post by dai_trying on 2008-12-11
Hi, I think I have the same problem with my pc not shutting down properly, and noticed this thread marked as solved, but, I cannot see the solution anywhere... If I am missing something please could somebody point me in the right direction.
Thanks.
Dave.

---

### Post by RVcruzer on 2009-04-06
Same here. I'm a newbie to Linux. Previously used Windows, and Data General's AOS/VS. It doesn't look all that complicated and I have installed a number of aps, printers, and played around with it. Stil a newbie though. :p But I too am having the same shutdown issues. I've been following the above and have created the same shutdown.log file with all those lines.

Now, If I could only find out what's wrong. ;)

My symptoms are that I can boot up the computer and I can restart it just fine and logoff/login. But I can't shutdown the system in any mode. I've tried just pressing the power button, using the GUI shutdown links, and the various commands in the terminal window. Every time it begins the process and the Ubuntu logo appears and the yellow bars cycle to the right. Then I get a black screen with a text line and it just hangs there forever. The only way to get it unhung is by pulling the power plug to it.

I reinstalled the system in the event that something was interferring with it. It's only the initially installed system without any additional software or updates installed. However it makes no difference in the shutdown.

The hardware is a basic custom built PC - Asus motherboard with Intel 945 chipset, Core 2 Duo, CPU, 2 GB RAM, SAT hard drive, IDE DVD-R drive, GeForce 5200 PCIO video card. Nothing cutting edge or antiquated.

---

