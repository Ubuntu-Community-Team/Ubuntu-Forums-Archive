---
title: "ubuntu 10.10 does not boot"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Amateur_Linux on 2011-10-17
Hi everyone!! I'm new to ubuntu as my username projects.... 

I've been using ubuntu 10.10 for a month... i was changing some boot options and when i logged out i cannot log in again..( back then i didn't know byepassing gui login)...

i shut it down forcefully and when i restarted my laptop i found the following message....(this was in recovery mode)

Could anyone help me...(i posted this in general help initially by mistake)

---

### Post by peperomia on 2011-10-19
What was the message you get when you try to boot?

---

### Post by Amateur_Linux on 2011-10-22
> **peperomia said:**
> What was the message you get when you try to boot?
Sorry about the delay...
 I thought I had attached a snapshot... (which in fact I didn't)

The message is

Failed to spawn plymouth main process: Unable to execute: Too many symbolic links
Failed to spawn hwclock main process: Unable to execute: Too many symbolic links

---

### Post by Silent Warrior on 2011-10-22
First thing to try is changing the boot options back, if possible (GRUB commands?). How did you change these boot options? I'm asking because programs for that specific purpose tend to update your initram - which will probably be a complication, as then you'd have to update it again to undo these changes. Boot issues, however, is not my area of expertise.

---

### Post by Amateur_Linux on 2011-10-25
> **Silent Warrior said:**
> First thing to try is changing the boot options back, if possible (GRUB commands?). How did you change these boot options? I'm asking because programs for that specific purpose tend to update your initram - which will probably be a complication, as then you'd have to update it again to undo these changes. Boot issues, however, is not my area of expertise.
I changed the login options.... It was intially on automatic login... I changed it to show users... Apart from that i tried to install Salome...
There is no problem with the GRUB... windows 7 boots properly...

 Plus I checked the syslog ... The warning lines are

Oct 16 15:20:38 ananth-VPCEB16FG pulseaudio[1599]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Oct 16 15:20:38 ananth-VPCEB16FG pulseaudio[1599]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 16 15:20:38 ananth-VPCEB16FG pulseaudio[1599]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Oct 16 15:46:38 ananth-VPCEB16FG AptDaemon: INFO: Initializing daemon
Oct 16 15:51:39 ananth-VPCEB16FG AptDaemon: INFO: Quiting due to inactivity
Oct 16 15:51:39 ananth-VPCEB16FG AptDaemon: INFO: Shutdown was requested
Oct 16 16:04:28 ananth-VPCEB16FG AptDaemon: INFO: Initializing daemon
Oct 16 16:09:29 ananth-VPCEB16FG AptDaemon: INFO: Quiting due to inactivity
Oct 16 16:09:29 ananth-VPCEB16FG AptDaemon: INFO: Shutdown was requested
Oct 16 16:17:01 ananth-VPCEB16FG CRON[6990]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Oct 16 16:17:01 ananth-VPCEB16FG CRON[6988]: (CRON) error (grandchild #6990 failed with exit status 1)
Oct 16 16:22:53 ananth-VPCEB16FG ntfs-3g[2940]: Unmounting /dev/sda3 ()
Oct 16 16:22:59 ananth-VPCEB16FG console-kit-daemon[1164]: WARNING: Unable to restart system: Failed to execute child process "/usr/lib/ConsoleKit/scripts/ck-system-restart" (Too many levels of symbolic links)
Oct 16 16:22:59 ananth-VPCEB16FG gnome-session[1474]: WARNING: Unable to restart system: Unable to restart system: Failed to execute child process "/usr/lib/ConsoleKit/scripts/ck-system-restart" (Too many levels of symbolic links)
Oct 16 16:23:00 ananth-VPCEB16FG console-kit-daemon[1164]: WARNING: Unable to spawn /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck: Failed to execute child process "/usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck" (Too many levels of symbolic links)
 
  And thanks bro...

---

### Post by Silent Warrior on 2011-10-25
Ok, GRUB appears to be fine, then. That makes things easier. The very easiest solution is, of course, to just reinstall, but that wouldn't be sporting. I will readily admit I don't know much about this part of Linux, so I'd be ever so happy to see someone else step up.
What boot options did you change, then? Using what application/configurator?

---

### Post by Amateur_Linux on 2011-10-28
> **Silent Warrior said:**
> Ok, GRUB appears to be fine, then. That makes things easier. The very easiest solution is, of course, to just reinstall, but that wouldn't be sporting. I will readily admit I don't know much about this part of Linux, so I'd be ever so happy to see someone else step up.
What boot options did you change, then? Using what application/configurator?
I just used the default ubuntu options... but wouldn't reinstalling wipe out all data? I need the files i've stored that's why i'm so keen in repairing it...

---

### Post by Silent Warrior on 2011-10-29
You must have done something more than what you've told us so far - you don't get a message about 'too many symlinks' for no reason, especially not if you're using any default options. That's the problem you need to sort out. If I could have a say, I would suggest reinstalling Plymouth, but that will be a challenge if you can't boot normally - to say the least.
I thought there was an option for ls that lets you see if a file is a symlink or not, but I couldn't find it... Anyone else have better luck? Maybe there are quite a few symlinks in /boot that could be pruned.

A reinstall would only destroy any personal data if you format the partition where you keep your data (/home). You would only need to format your root partition (/).

---

### Post by lightwarrior on 2011-10-29
You can backup your data by booting with a LiveCD and then plug an USB or external drive.
It seems you lost something on the gnome desktop.

---

### Post by Amateur_Linux on 2011-10-30
I was trying to install SALOME and guess I must have made some mistake while typing the commands.
 This is what I doubt must have happened,
  /$ sudo rm /bin/sh ( I think I entered bash for sh here)

  And is there any way of reading the encrypted files I have in that? I used Cryptkeeper ... I am not able to view it using Live CD .... At least that would be greatly helpful....

---

### Post by Silent Warrior on 2011-10-30
Jesus, Mary, and Josef... and that's coming from an atheist! Did you really enter that command?? /bin is a critical system directory - NEVER EVER remove something from there manually, not even if you have a reason to! If you actually did remove /bin/bash, you've just erased your shell - command line, script interpretation, essentially the veins of your operating system. While this has left your system thoroughly crippled, it should still be possible to recover.
First try this:
- Boot from your installation/live CD
- Access your harddrive through Nautilus/Dolphin (file manager X) - should show up as x Gb Storage media, or something along those lines
- Copy the /bin/bash (or /bin/sh - most likely a symlink pointing to bash) file from the live CD (it will be listed as the normal File system or Root), depending on which you removed, and paste it into your harddrive's /bin directory

A less hacky solution involves booting from your live CD, mount your /bin in place of the CD's /bin, and attempting to reinstall bash through Synaptic, but there's no guarantee that would work - you might not have an interpreter for the scripts run before and after the installation. This is a more elegant procedure, but is somewhat time consuming, as it requires the most work at the terminal.

The only solution that is both easy and guarantees success is: Reinstall. (Backing up as desired, of course, though the only partition you need to reformat is / (root).)

---

### Post by scott-ian on 2011-10-30
I think you can install programs into the ram on the livecd, so you could install Cryptkeeper and use that to access the files.  Then you can try copying the /bin/bash file.  If that doesn't work, you may be able to fix things by doing a chroot to the broken install, although you would need to run some shell.

---

### Post by Amateur_Linux on 2011-11-06
> **Silent Warrior said:**
> Jesus, Mary, and Josef... and that's coming from an atheist! Did you really enter that command?? /bin is a critical system directory - NEVER EVER remove something from there manually, not even if you have a reason to! If you actually did remove /bin/bash, you've just erased your shell - command line, script interpretation, essentially the veins of your operating system. While this has left your system thoroughly crippled, it should still be possible to recover.
First try this:
- Boot from your installation/live CD
- Access your harddrive through Nautilus/Dolphin (file manager X) - should show up as x Gb Storage media, or something along those lines
- Copy the /bin/bash (or /bin/sh - most likely a symlink pointing to bash) file from the live CD (it will be listed as the normal File system or Root), depending on which you removed, and paste it into your harddrive's /bin directory

A less hacky solution involves booting from your live CD, mount your /bin in place of the CD's /bin, and attempting to reinstall bash through Synaptic, but there's no guarantee that would work - you might not have an interpreter for the scripts run before and after the installation. This is a more elegant procedure, but is somewhat time consuming, as it requires the most work at the terminal.

The only solution that is both easy and guarantees success is: Reinstall. (Backing up as desired, of course, though the only partition you need to reformat is / (root).)
(Excuse my delayed reply... Never saw there was a second page link!!!:oops:](*,))Thanks a lot... I'll try it soon enough ... Having semester exams now.... I'll reply in a couple of days after trying... And one more thing .. I tried to edit the files in my hard disc using live CD and it failed ...
 Do you think I'll be able to paste files into my hard disc using live CD?

---

### Post by Amateur_Linux on 2011-11-06
> **scott-ian said:**
> I think you can install programs into the ram on the livecd, so you could install Cryptkeeper and use that to access the files.  Then you can try copying the /bin/bash file.  If that doesn't work, you may be able to fix things by doing a chroot to the broken install, although you would need to run some shell.
And would the newly installed CryptKeeper identify the already created virtual drive?

---

### Post by Silent Warrior on 2011-11-06
I don't use CryptKeeper, so I have absolutely no idea. If you can't access it from the live CD, it seems you're pretty much out of options. Of course, you COULD install Linux to a separate disk, if you really want to preserve your root partition, install what you need to access your other disk, and go on from there.

---

### Post by Amateur_Linux on 2011-11-13
> **Silent Warrior said:**
> I don't use CryptKeeper, so I have absolutely no idea. If you can't access it from the live CD, it seems you're pretty much out of options. Of course, you COULD install Linux to a separate disk, if you really want to preserve your root partition, install what you need to access your other disk, and go on from there.
I was trying to use the live CD today, It asks for username and password... Weird... Never happened before.... What would be the problem???

---

### Post by Silent Warrior on 2011-11-13
Live CDs aren't normally supposed to do that, at least Ubuntu's... What did you do when you got that prompt?

---

### Post by Amateur_Linux on 2011-11-16
> **Silent Warrior said:**
> Live CDs aren't normally supposed to do that, at least Ubuntu's... What did you do when you got that prompt?
Well... I tried to login with the previous password and username and failed resulting in the same screen appearing again and again....

---

### Post by Silent Warrior on 2011-11-16
I'm not sure I understand, but when you're using a live CD you're not supposed to use any username or password - just stick it in and go. I wasn't even aware Ubuntu's live CD ever asked for username/password...

---

### Post by Amateur_Linux on 2011-11-19
> **Silent Warrior said:**
> I'm not sure I understand, but when you're using a live CD you're not supposed to use any username or password - just stick it in and go. I wasn't even aware Ubuntu's live CD ever asked for username/password...
I get this login screen normally when i use the live CD(which i've never got before) ... I did nothing else... I used try ubuntu without installing option...

---

### Post by Silent Warrior on 2011-11-19
This just doesn't sound good... Have you checked the CD for errors? It should be another option at boot.

---

### Post by Amateur_Linux on 2011-11-21
> **Silent Warrior said:**
> This just doesn't sound good... Have you checked the CD for errors? It should be another option at boot.
It works fine on other computers... Just mine shows this problem....

---

### Post by Amateur_Linux on 2011-11-27
I tried other with new CDs too... the same problem occurs.... And i found a solution for the file recovery... I just copied the encrypted files and imported to newly installed ubuntu's cryptkeepr.... got 'em... And thanks for all your help silent warrior.... hope we meet in some other problem...:lolflag::lolflag::lolflag:

---

