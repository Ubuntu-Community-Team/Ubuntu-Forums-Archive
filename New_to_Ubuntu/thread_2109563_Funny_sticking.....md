---
title: "Funny sticking...."
date: 2013-01-27
forum: New to Ubuntu
---

### Post by johnnyflips on 2013-01-27
Hi guys, and girls. I'm sure this is going to be one of those "I should have known that" moments, but, about two months ago I installed Ubuntu Studio on my desktop that I use every day. I love it, but the last few days I have developed a problem with scrolling when I'm not trying to. If I'm on a page with a map it zooms out until it can't anymore. And if I'm on a page with text it scrolls to the right of the page. I have considered it being a stuck key on the keyboard or something malfunctioning in the mouse, but they are a cordless set and I ruled them out after realizing it done it even with the batteries pulled on both of them. Has anyone ever heard of anything like this? I would appreciate any help and thoughts I could get. Thanks for reading....

---

### Post by johnnyflips on 2013-01-27
Sorry guys, two things I forgot to mention are that it does this on Firefox and Chrome both. And secondly that it does not do it if I am in text, as I am now writing this. Thanks again, I look forward to hearing your thoughts.

---

### Post by ACubed10 on 2013-01-27
Interesting. Wondering if it isn't a flash/video card driver issue. I personally haven't ever heard of this unless a video driver is incorrect. Hopefully someone will comment with an answer for you

---

### Post by DuckHook on 2013-01-28
This is the sort of problem that is notoriously hard to track down:

1. Did you install/replace/delete any HW/SW just prior?
2. Did you make any config changes, especially to xorg.conf?
3. Any system updates? If so, do you remember which they were?
4. Scroll through your logs, especially dmesg, xorg.0.log and syslog. Does anything look out of the ordinary? We are looking especially for messages like: "key xxxx undefined" where xxxx is a hexadecimal number. If your logs are as lengthy as mine and are making you go cross-eyed, try:

```
dmesg | grep -e undefined -e key
```...and similarly for the other logs.

Also, post output of:

```
lsusb
```

---

### Post by johnnyflips on 2013-01-28
Thanks for your help. I haven't changed anything, I'm a newbie. I do install every update it prompts me to, but I never really look at what it's installing. (it all looks greek to me) The first command yielded no results, and the second yielded this: 
Bus 001 Device 002: ID 03f0:8811 Hewlett-Packard 
Bus 004 Device 002: ID 062a:4101 Creative Labs 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks again for your help, I really appreciate your time..

---

### Post by DuckHook on 2013-01-28
I don't want to get your hopes up. I'm no guru, but perhaps we can solve it by luck or by golly.

I am perplexed--lsusb shows that you have only two usb devices hooked up, "Hewlett-packard" and "Creative Labs". Is the HP device your mouse and keyboard? If so, what is the "Creative Labs" device? If neither are your mouse/keyboard, then tell us what they are and whether you are using a PS/2 mouse and keyboard.

Please provide a complete description of your system. HW and SW including flavour and version of Ubuntu. Please look at *[this]("http://ubuntuforums.org/showthread.php?t=1422475")* sticky at the top of the page for more detailed procedures on how to generate system info and post results back here. Also, try to post code output by highlighting it and using the "code" formatting tool at the top of the Message box.

Did your logs show anything out of the ordinary? Logs will often provide error reports that give us lots to go on. It's very important for you to review them if you want to chase this down.

I am completely unfamiliar with Ubuntu Studio, but their web site says that this is alpha software. Usually, it's only uber-geeks who play with alpha software because its highly unstable and developmental nature causes problems of just this sort. You may wish to send an e-mail or bug report to:

[EMAIL="ubuntu-studio-devel@lists.ubuntu.com"]ubuntu-studio-devel@lists.ubuntu.com[/EMAIL]

asking if others have encountered this problem.

Here are some preliminary steps you can take to play detective work:

1. Assuming that the HP device is your mouse/keyboard try unplugging your Creative Labs device to see if this makes any difference.
2. Run ubuntu studio from the command line. Note any errors that show up on the terminal window. Running from the command line will leave an error trail whereas running from the GUI launcher leaves us little to go by.

---

### Post by johnnyflips on 2013-01-29
Hiya, 
       Actually taking your advise I have decided to go with 12.10. That's what I get for not doing any research before I set it up on my desktop. I guess my question now would be can I make the change by popping in a USB set up with Universal USB installer without having to dual boot? Or am I going to have to save everything and get ready to format the hard drive? I see now that 12.10 is where I need to be, NOT Windows!!  lol I appreciate all the help. 

    Oh and by the way, The HP was my printer and the Creative Labs is the keyboard\mouse combo.

---

### Post by DuckHook on 2013-01-29
Since you are already seeing quirky behaviour with your current install, I would recommend a clean install of 12.10 from scratch. You will have to back up your important data first to a USB key/drive and copy them back to your new system after it has been installed.

If you want to experiment with an upgrade at this point, you can do so quite easily from the Update Manager. You will need to change the setting in the "Updates" tab from only notifying you "For long-term support versions" to "For any new version". After a reboot or a logout/login, the Update Manager should now offer you a choice of Ubuntu 12.10. Alternatively, you can do:

```
sudo do-release-ugrade
```from the command line.

An upgrade may not solve your wonky phantom stuck key problem, so I would think that a clean install is preferable. However, you might decide that it's worth a try. If you do so, it is highly recommended that you do the same backup as you would with the clean install anyway. Backups never harm and will save your keester when it matters most.

Happy Ubuntuing!

---

### Post by williejones on 2013-01-29
[QUOTE=]I guess my question now would be can I make the change by popping in a USB set up with Universal USB installer without having to dual boot? Or am I going to have to save everything and get ready to format the hard drive? I see now that 12.10 is where I need to be, NOT Windows!!  lol I appreciate all the help. [/QUOTE]

I am probably late answering your questions.  Yes you can install without having to dual boot.  Just pay attention to the install instructions to install along side (dual boot) or use the whole disk (only the new install is on your machine)

You can also choose something else in the installer to get more advanced options.

As far as saving everything,  everything will be lost if you only install 12.10.  If you have anything you need to keep, copy it to a cd, dvd, or usb then you can put it on your new install.

---

