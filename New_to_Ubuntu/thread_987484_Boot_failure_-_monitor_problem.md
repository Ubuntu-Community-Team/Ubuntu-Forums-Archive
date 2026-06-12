---
title: "Boot failure - monitor problem"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by davidtrickett on 2008-11-19
I posted something on this a little while ago re a Samsung 943N monitor - thanks to those who responded.

However things have gone from bad to worse - Ubuntu now won't boot at all - it shows the splash screen but when this disappears it just sits there with a blank screen (I have given it plenty of time to wake up).

I have tried the recovery mode & fix options, but this doesn't help. My guess is that the only way I can get through this is to put something in on the boot command prompt - have tried a couple of things with rdev -v but I'm really just guessing and have got nowhere.

Interestingly when I try to boot from the Ubuntu CD (including the latest version downloaded today) it does exactly the same thing - but I have been able to boot from this by selecting the safe graphics option.

Can anyone help please - this is driving me nuts!

Thank you

---

### Post by jimreynold2nd on 2008-11-19
Can you try to edit the grub entry and remove "quiet splash" from the kernel line of Ubuntu entry you are booting from?
If that doesn't solve the problem, at least it shows you where/what things are going wrong :)

---

### Post by davidtrickett on 2008-11-19
jimreynold2nd - sorry - I may be being dim (or just too new to this thing) but I don't know how to edit the grub entry! But thanks...

---

### Post by davidtrickett on 2008-11-19
jimreynold2nd - sorry - forgot to mention that I have tried this when booting from the CD, but the long list of stuff that appears on the screen - and goes past before I can look at it - is incomprehensible to this bear of very little brain.

---

### Post by win4thebin on 2008-11-19
what are the specs of your computer?

---

### Post by davidtrickett on 2008-11-19
win4thebin - AMD Athlon 64 dual core - Gigabyte m/b - 2GB RAM - onboard video Nvidia GEFORCE 6100 - lots of HDD's - internal & USB (would take me ages to figure out exactly what is in there - system has been cobbled together over the years). If there is any particular bit you would like to know about tell me!

---

### Post by jimreynold2nd on 2008-11-19
> **davidtrickett said:**
> jimreynold2nd - sorry - I may be being dim (or just too new to this thing) but I don't know how to edit the grub entry! But thanks...

Oh, sorry. When you turn on your computer it presents you with a menu of "Ubuntu 8.10 kernel...." and "...safe mode" and "Memtest86+" right? (If not, pres up-down key at boot time to pull it out, assuming you use GrUB to boot, which is default).
Highlight the normal booting line (normally top one), press "e". It brings up a screen with 2 or 3 lines, usually first one is root (hdx,x) one of the others starts with "kernel..." and one other starts with "initrd...".
Highlight the kernel line, press "e" again. You will now be in edit mode. Delete "quiet" and "splash", then press enter, then press "b". It will boot. Look for any "FAIL".
And if you can, try to write down the last lines before everything goes dark.

I have a couple of hypotheses:
1. Your screen resolution is not detected correctly (not likely ince Samsung 943N is relatively new).
2. Your graphic card (also not likely, because I also have the 6100 LE on 410/430 (the onboard card of the desktop on my signature) and it _works_ with the default nv driver).
3. Intrepid has some problem with nvidia drivers - try download Hardy LiveCD to see if it works.

---

### Post by davidtrickett on 2008-11-20
jimreynold2nd - Thanks for that - you learn something new every day!

I'm away for a couple of days but I'll try this at the weekend - watch this space...

---

### Post by davidtrickett on 2008-11-23
jimreynold2nd - Hope you're still there!

Have tried setting GRUB to display progress - unfortunately everything goes past far too fast for me to make anything out for sure,  but my impression is that there is nothing marked "fail" and that the last few lines before the screen goes blank have nothing to do with the display.

I have tried inserting VGA=nnn (I found the table), but with no effect on any setting I used.

I have managed to have a look at the HDD installation from the safe graphics mode of the live cd, and there is a whole bunch of xorg.conf... files there. I thought I'd be clever & replace the latest one (which obviously doesn't work) with a few of the earlier ones, but no luck.

It occurs to me that if I could boot in safe graphics mode from the HDD I might get somewhere, but can't find any way of doing this.

So far I have tried booting from the original Live CD I installed from - Hardy I think - 8.04 anyway, and the latest one (8.10). Both give exactly the same result - blank screen unless I select safe graphics mode.

Any more ideas?

Thanks

---

### Post by jimreynold2nd on 2008-11-23
Try there one by one...
1. Is there a "safe mode" on your grub menu? If there is, try that.

2. If not, try editting the kernel line like you did before, deleting "quiet splash" and add "single". (don't 'esc' all the way to the menu or your editting is lost, just 'esc' till you see the lines kernel, initrd then press 'b' to boot)

3. If that doesn't help, try wait at the black screen till everything settles down (aka no disk activity), then press Ctlr-Alt-F1, it should get you to a command prompt. If it doesn't, then sorry I cannot help you further. If you have a command prompt, login there and install the nvidia drivers using
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-glx
```

4. If still doesn't work, try get back into the command line like in step 4, and do
```
nano /etc/X11/xorg.conf
```
and post the content of the file. (Im doing this assuming you cannot get the xorg.conf out of thta computer any other way, if you can, just post your xorg.conf file). If typing is too tedious and the file is long, just post the *section names*, and the content of Section "Device", Section "Screen", Section "Display"

---

### Post by davidtrickett on 2008-11-23
jimreynold2nd:

Many thanks for that - probably a bit too late to do all that now - will do so tomorrow. As I said earlier I found a flock of xorg.conf... files & will post a selection including those that worked earlier.

I am beginning to think that the problem is even more basic than that however - I did manage to replace the current file with one that worked earlier, but no difference. I have also now tried 4 live CDs - 3 Ubuntu & 1 Mandriva, all with the same result - will only boot if I select safe graphics mode.

My GRUB only has recovery mode - I have of course tried all available options on that without success. It does not appear to have a safe graphics mode.

BTW - I can get to the command prompt when everything stops - problem was I didn't know what to do with it!

I'm learning fast, but I just wish I didn't have to do so just to get the bloody thing going again!

---

### Post by jimreynold2nd on 2008-11-23
Yea, it seems like your graphic card/monitor is not being detected correctly. Even with the correct driver, the monitor resolution is sometimes screwed up (i.e. more than your monitor can handle). That's why you need to make sure you install the right driver and make the correct configuration.

Oh, and in my step 3 earlier, after you do the apt-get's and restarted, I forgot you should also do 'nvidia-xconf' if things didn't work right after reboot.

Yes it helps to post those xorg.conf's too :D

---

### Post by davidtrickett on 2008-11-24
jimreynold2nd:

I have finally managed to boot into Ubuntu - after an awful lot of messing about I tried dpkg-reconfigure xserver-xorg & opted to "Use kernel framebuffer device interface". It then did boot (I haven't dared to try a reboot yet!) - but I am basically now back where I started - 800x600 @ 61Hz is the best it will do. When I tried the apt-get line you sent (BTW it refused to do anything until I put in sudo -i) it did seem to download & update loads of stuff - but finished with "sudo: apt_get: command not found".

I couldn't follow "you should also do 'nvidia-xconf' if things didn't work right after reboot" in your last note - is this in the command line (I tried that but "Command not found") or what?

What I need is res. 800x600 1280x768 (for my TV) & 1280x1024, all at 60Hz.

I'm attaching a few xorg.conf files - ...current is the one now in use, the other two worked to an extent - but none would give me what I need.

Any more help would be much appreciated - but if I am becoming a pest do let me know :biggrin:

---

### Post by jimreynold2nd on 2008-11-24
I am sorry! there's definitely a lot of typos in my post... apt_get should be apt-get, and nvidia-xconf should be nvidia-xconfig.....Im looking at the xorg.conf right now. Will post if I have some insight. Meanwhile, you should try the commands again.
EDIT: just do the bunch of commands again:
```
sudo apt-get install nvidia-glx
```
then
```
sudo nvidia-xconfig
```

---

### Post by jimreynold2nd on 2008-11-24
looks like after doing nvidia-xconfig it will help fix your xorg.conf. You are still using the 'nv' driver, not 'nvidia'

---

### Post by davidtrickett on 2008-11-25
Jim

Thanks for further info - the apt_get typo was mine - sorry.

All done as you suggest - now down to 640x480@54! Can't see text in terminal - but typing blind does work.

Latest xorg.conf is attached - any further suggestions would be much appreciated!

David

---

### Post by Wickd on 2008-11-25
Hey had this problem I little while back. And I found by simply installing the Nvidia driver specific for you series also helps. Do you have the generic driver installed at the moment?

---

### Post by jimreynold2nd on 2008-11-25
whew, looks like you have the right driver loaded ...

So now it's time for the monitor. I had this problem several times before on several computer. I have a trick to fix it (coz I can't make out where to find monitor parameters) but it's kinda involving...

First, do you have a GUI at all? If you do, even if it's at 640x480, you can still go to system->system settings->display (or monitor, or something like that - sorry I'm on openSuSE KDE at the moment), but it's in system setting, there will be a place for you to choose your monitor brand/model. Try to match as closely to your true model as possible, and if you cant, choose "Generic" monitor with your resolution.

If I didn't have a GUI or can't find the place, what I did was make a backup of xorg.conf, then make a syntax error in the xorg.conf so that X can't start and will ask you to reconfigure. Go configure, it will lead you right to the dialog to choose graphic card/monitor brand and model. Choose the monitor as above then let it save.

Restart. Now open the new xorg.conf, copy the section "Monitor" and overwrite the Monitor section in your back-up xorg.conf, **except** for the Identifier, and save that modified backup as your main xorg.conf. It should work.

If this doesn't help, then I'm sorry... I feel like taking up your time experimenting with stuffs.

---

### Post by davidtrickett on 2008-11-27
jimreynold2nd

Jim

Just wanted to say thanks for all your help - I eventually went to the Nvidia forum & largely by accident solved the problem. But you taught me a lot and therefore my thanks.

David T

---

