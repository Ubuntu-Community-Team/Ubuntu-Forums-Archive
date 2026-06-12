---
title: "What the.......?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by sp00ner on 2008-05-29
I went to boot up my laptop today and it just got stuck at a blank screen and never boots up. I can hit esc during startup and select to boot in recovery mode. It will come up to a command prompt. What do I do from there to see what the problem could be? :confused:

---

### Post by kpkeerthi on 2008-05-29
At recovery mode command prompt, type
```
dpkg-reconfigure -phigh xserver-xorg
```

It should clear things up if it was an X server issue.

---

### Post by sp00ner on 2008-05-29
I ran that command, it asked me to choose a video chipset and a screen resolution to use. I did both, then it gave a message that it is overwritting a "possibly customized" file and gave a backup location and went back to the command prompt. I figured it did what it was supposed to do so I rebooted using the reboot command, but it did not help the problem :( It seems like it is almost booting up because the hard drive light flashes for the normal amount of time for a boot up, but then it stops and it just stays at the blank screen.

---

### Post by ingrid_ozikem on 2008-05-29
When you say it comes to a blank screen, does it not respond to any keystrokes at that point?

How about Ctrl+Alt+Backspace? (Kills the X server.)

And try Ctrl+Alt+F1 or F2 or F3 ... these should take you to a text login screen instead of X (but this is the full mode, not recovery). If this works and you are able to login at the text prompt, the problem is clearly with X.

The previous suggestion with dpkg-reconfigure was given to reset xorg.conf file back to its default setting. But it looks like you still had to specify your video chipset -- are you sure you got that right? Did you choose between Intel and NVidia/ ATI etc as the make of your video card?  With the wrong setting here, it is quite likely things are messed up.


Finally, after running dpkg-reconfigure, you could look at your /etc/X11/xorg.conf file and post it here for people to look at. Also, you can find out what kind of video card you have using the lspci command which will list all PCI devices. Often, the video card seems to be in the 0:2:0 slot.. (but could easily be otherwise I suppose?)

---

### Post by kpkeerthi on 2008-05-29
OK... Are you able to figure out at what stage the boot process stops?

From the GRUB menu, highlight the kernel entry and press 'e' to edit. Use the arrow keys and go the end of the line and delete the words **splash** and **quiet**. Press <enter> and 'b' to boot. This should put you back in textual boot mode and you should be able to see some messages printed on screen. That should give you some clue.

* The GRUB line change will NOT permanently change the boot options. It only affects the current boot session.

---

### Post by sp00ner on 2008-05-29
Ingrid, initialy it did not respond to any of the keystrokes you mentioned. But then I tried kpk's suggestion and got some messages to appear during bootup. I found that it displays a bunch of starting this and starting that lines all with an [ok] to the right of them them. The last one before it stops is "running local boot scripts (/etc/rc.local) and it has the [ok] to the right. I cannot see what the next line is or would be. But then pressing ctrl-alt-f1, I get a  tty1 login prompt and have logged in and am currently at my home folder command prompt.

It is getting pretty late for me and I need to hit the sack so I can get up early and go to work to support WinXP desktops...LOL Please feel free to reply with my next step in trouble shooting and I will check it out tomorrow after work. If I need to post that /etc/X11/xorg.conf file, I will do that tomorrow as well. Thanks for the help, I wish I had started this earlier

---

### Post by kpkeerthi on 2008-05-29
> The last one before it stops is "running local boot scripts (/etc/rc.local) and it has the [ok] to the right. I cannot see what the next line is or would be. But then pressing ctrl-alt-f1, I get a tty1 login prompt and have logged in and am currently at my home folder command prompt.

Login and at the prompt, type **startx** <enter>

That should load your Desktop Environment.

Post back with any errors.

---

