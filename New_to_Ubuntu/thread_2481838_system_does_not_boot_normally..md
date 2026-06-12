---
title: "system does not boot normally."
date: 2022-12-10
forum: New to Ubuntu
---

### Post by jiovanyj on 2022-12-10
Greetings, I have lubuntu with windows.


after upgrading lubuntu 22.04 from version 20.04, the computer does not boot normally.


When I press the power button, it pretends to load grub but it doesn't finish loading the default time, the screen flashes and goes to the lubuntu logo, which appears before loading users to enter, before the user appears. The screen goes black, for it to work I have to press the reset button and then if grub loads normally, the default time passes, then the lubuntu logo and at the end the screen to enter the user where the password is placed.


my pc is a T. Mother ASRock H61M-VG3, with 4GB memory, intel i5 processor.


What commands or tests do I have to do to solve this error, thank you.

---

### Post by tshade on 2022-12-11
You might have to reinstall grub from a rescue system,  like systemrescuecd. You can also try super grub disk, which might allow you to boot and reinstall grub. It's difficult, but not impossible, to diagnose this problem.

The key commands are 'sudo update-grub' and 'sudo grub-install [/dev/sda]

Things also depend of you're using old boot or uefi.

---

### Post by jiovanyj on 2022-12-11
Thanks for answering, I'm going to take some screenshots of when it starts and the bios where I check, thanks.[https://i.postimg.cc/BQn1gZfD/inicio1.jpg](https://i.postimg.cc/BQn1gZfD/inicio1.jpg)

and
[https://i.postimg.cc/HxJTxNqr/asroock.jpg](https://i.postimg.cc/HxJTxNqr/asroock.jpg)

---

### Post by jiovanyj on 2022-12-13
you to boot and reinstall grub. It's difficult, but not impossible, to diagnose this problem.

The key commands are '[COLOR=#008000]*sudo update-grub*[/COLOR]' and [COLOR=#00ff00]*'*[/COLOR][COLOR=#008000]*sudo grub-install [/dev/sda]*[/COLOR][COLOR=#00ff00][/COLOR]

Greetings, I have to apply those commands, or what should I do first.
I don't have much experience with Gnu Linux, I use more graphics because I don't know much about the commands.

---

### Post by grahammechanical on 2022-12-14
First of all, those ACPI errors are not relevant to your problem. I get those same errors on my install of Ubuntu 20.04. On this machine I also have an install of Ubuntu 22.04 and when I boot into 22.04 I do not see those errors.

Do you get a Grub boot menu that offers the choice of loading Lubuntu or Windows? If you do then select Advanced Options for Lubuntu. Then select a Linux kernel with recovery mode. Linux will load and a menu will appear. Select Grub - Update Grub bootloader. Then when that is finished and you are back at the menu select Resume - Resume normal boot. That should load Lubuntu with an open source video driver. Shutdown and reboot. See if that changes anything.

What video adapter do you have? Intel? Nvidia? AMD?

Regards

---

### Post by DuckHook on 2022-12-14
Please don't post large images to the thread. Attach them as image files instead by using the paperclip icon in Adv Reply.

Large images do not display well on mobile devices and use up valuable bandwidth for those on metered connections.

---

### Post by jiovanyj on 2022-12-18
Integrated Video
Video Does not include integrated video
A processor with Intel HD Graphics is required to enable video output.

I don't have a video card, according to the characteristics of the processor it does the job.
I do not know if it is ok
df -h
S.files Size Used Disp Usage% Mounted on
tmpfs 363M 1.5M 362M 1% /run
/dev/sda6 20G 16G 3.4G 82% /
tmpfs 1.8G 25M 1.8G 2% /dev/shm
tmpfs 5.0M 4.0K 5.0M 1% /run/lock
/dev/sda7 254G 205G 48G 82% /home
tmpfs 363M 80K 363M 1% /run/user/1000



I don't know if it is necessary to show this result.
dmesg --level=err,warning -T
I hope you confirm but to do what you tell me about grub.

---

### Post by jiovanyj on 2022-12-29
Regards, perform advanced grub to repair it, but the same error continues, thanks. I don't know what to do because it makes a failed boot.
 desde lubuntu 22.04 jammy jellyfish, 
add-apt-repository ppa:n-muench/burg[COLOR=#000000].[/COLOR]

---

### Post by jiovanyj on 2023-01-12
Greetings brother, I already made a recovery from grub, my fault is when I turn on the pc the grub is shown for a second the screen flashes then the image with the lubuntu logo flashes the screen again, the red led shows that it is reading the disk but nothing happens, I have to press the reset button once or twice for the system to load normally after that I can use the pc without apparent problem.
I don't know if there are any other grub files besides the one in $cat /etc/grub.conf. In catfish many appear in my case.
What can I do to identify which one is correct and eliminate the others, in case it is generating a boot failure, thank you.[IMG][[IMG]https://i.postimg.cc/3Wf7Frsx/screen1.jpg[/IMG]]("https://postimg.cc/3Wf7Frsx")[/IMG]

---

### Post by tea for one on 2023-01-12
> **jiovanyj said:**
> add-apt-repository ppa:n-muench/burg
Have you added this repository and installed the software?
As far as I can see, this is not suitable for Lubuntu 22.04.

Can you boot into an Ubuntu (or Lubuntu) live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

---

### Post by grahammechanical on 2023-01-12
> What can I do to identify which one is correct and eliminate the others, in case it is generating a boot failure

Please do not delete files. That could produce other problems.

> I don't know if there are any other grub files besides the one in $cat /etc/grub.conf.

Please confirm that you have a grub.conf in /etc. I am confused. Ubuntu uses a file called grub.cfg and not grub.conf. According to my research on the internet the file grub.conf is a Redhat/Fedora file and not a Ubuntu file. And it found in /boot/grub/ and not /etc.

[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/installation_guide/s1-grub-configfile](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/installation_guide/s1-grub-configfile)

Regards

---

