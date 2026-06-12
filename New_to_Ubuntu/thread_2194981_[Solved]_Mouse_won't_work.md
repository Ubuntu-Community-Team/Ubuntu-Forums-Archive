---
title: "[Solved] Mouse won't work"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by the.z.cuber on 2013-12-21
Hello. I'm new to Ubuntu, but when I tried to load it off a USB drive, my trackpad won't work, nor will the buttons. I've tried to look it up, but nothing has worked so far. If I need to get into a folder, it has to be accessible from the terminal, since I don't have access to an external mouse. Any and all help is appreciated.

---

### Post by varunendra on 2013-12-22
Welcome to the forums the.z.cuber !

Please try what has been suggested in this post [http://ubuntuforums.org/showthread.php?t=2188781&p=12880188#post12880188](http://ubuntuforums.org/showthread.php?t=2188781&p=12880188#post12880188)

Of course replace the "PS/2 Elantech Touchpad" part with whatever name your trackpad comes up with in the output of "xinput", if the first two command sets don't work and you need to try the "xinput float..." commands.

---

### Post by the.z.cuber on 2013-12-22
My mouse is PS/2 Synaptics TouchPad. I tried the first, which did not work. Adding proto worked, but only for about a second. The last did nothing as well.

---

### Post by varunendra on 2013-12-23
Please open 3 terminals at the same time, one will be for entering commands, other two will be for monitoring the effects.

In one terminal, enter -
```
tail -f /var/log/Xorg.0.log > Desktop/Xorg.txt
```
In the other one -
```
tail -f /var/log/syslog > Desktop syslog.txt
```
These will keep monitoring the Xorg.0.log and syslog files for any new messages and redirect their outputs to Xorg.txt and syslog.txt files on your desktop. Keep these running.

Now in the third terminal, run all the three workarounds one-by-one (first the "xinput" one, then reloading the module without parameter, and last, reloading it with "proto=imps" parameter). After these, run these commands -
```
synclient > Desktop/synclient.txt
lsmod > Desktop/lsmod.txt
```
After all five commands including the above ones have been run, highlight the monitoring terminals with 'Alt-Tab' and stop the monitoring with 'Ctrl-Z'. Highlight the four newly created files on the desktop using arrow keys, and copy them with 'Ctrl-C'. Now plug in a pen drive > let it open automatically and paste the files into it with 'Ctrl-V'.

Attach these files into your next post here.

**PS:**
If the usb drive doesn't open automatically, you can copy the files using command line -
```
cp Desktop/*.txt *<mount-point of the usb drive>*
```
where *<mount-point of the usb drive>* has to be replaced by the drive's mount point (e.g. sdb1, sdc1 etc.). You can determine that with "mount" command.

---

### Post by the.z.cuber on 2013-12-23
I don't see any filed created on the desktop for whatever reason.  Is this because I had to close the terminal in order to get to the other one?

---

### Post by varunendra on 2013-12-24
It must have been created even if you closed the terminal but entered the command correctly before that. Make sure you entered the command exactly as I posted above (if you can copy it somehow, you can paste it in terminal with 'Ctrl-Shift-V').

Sometimes you need to 'Refresh' the desktop in Live session to be able to see newly created files. Press "F5" for that. The command "ls Desktop" will also show the contents of the desktop.

By the way, you don't need to close a terminal to get a new one. Just press 'Ctrl-Alt-T' again and you can open as many terminal with this as you need. Keep all the three terminals open until the commands are finished.

---

### Post by the.z.cuber on 2013-12-24
Since I'm using my iPod to access this website, I can't attach files. I took a picture of the 3 filed that had contents (the 4th was empty). I can't find a way to attach pictutes on the mobile site; is there an email I could send them to? If you don't want to post it, just email me at [email].  Thanks!

---

### Post by the.z.cuber on 2013-12-25
Apparently the email forward I have set up does not. Try [email]

---

### Post by varunendra on 2013-12-26
I didn't try any of the email addresses you posted. And unless you don't mind spams, it is best to remove them from your posts above. :)

It would be much better to upload the images at some image hosting site like imagebin.org (deletes images after some days) or photobucket.com (for permanent link) etc., then post its link here.

---

### Post by the.z.cuber on 2013-12-26
[syslog.txt](http://i1336.photobucket.com/albums/o650/jpr15/452709FB-8FAC-40D5-BDC2-CFC468E5BB9B_zpsdmuu2in5.jpg)
[Xorg.txt](http://i1336.photobucket.com/albums/o650/jpr15/23B7756E-3E6C-44B3-B51A-7BEE0B4FD7C2_zpsi3cskawf.jpg)
[lsmod.txt [1]](http://i1336.photobucket.com/albums/o650/jpr15/AAAD8725-B1BC-4883-8C76-ADD4D5CF2B4C_zpshkivju8b.jpg)
[lsmod.txt[2]](http://i1336.photobucket.com/albums/o650/jpr15/18209E35-9010-467C-81D0-4CEACE63848A_zpsf0ovvf5v.jpg)
[lsmod.txt[3]](http://i1336.photobucket.com/albums/o650/jpr15/CE9BA593-62F8-49F0-B316-CEB90E3D1C15_zpsywasnhlq.jpg)

Whatever the missing file is was empty.

---

### Post by the.z.cuber on 2013-12-29
I'd just like to check up on this as it's been two days with no reply. Thanks for all your help!

---

### Post by varunendra on 2013-12-30
Sorry for not being able to respond in a reasonable time, the opportunity to be on the forums and reply back has become a luxury I rarely get these days.

On to the problem -

Did you take the pictures AFTER running the workarounds from the post I linked to? Because there seems no such activity in the logs that has the tiniest hint that you ran those commands before taking the snaps. If you did, it can mean that your touchpad wasn't even recognized by the OS.

Do you have another OS currently running on the laptop/netbook ? If yes, does the touchpad work there?

It would make our job a lot more easier if you have or can temporary get an external mouse that works. If that is not possible, then perhaps the last thing we can try just to get a hint of the problem is to copy your syslog and Xorg.0.log files from /var/log/ directory to an existing partition on your hard disk > upload them to [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) from your working OS, then post the pastebin links here for us. And of course copy the files AFTER running these workarounds from this post as originally suggested : [http://ubuntuforums.org/showthread.php?t=2188781&p=12880188#post12880188](http://ubuntuforums.org/showthread.php?t=2188781&p=12880188#post12880188)

---

### Post by the.z.cuber on 2013-12-30
I ran all 3 commands in the order provided while the trackers were running. Ubuntu does recognize it; it works for about a second after I add the proto=imps onto it. I can't currently run the windows that I have installed (grub error no partition for Ubuntu), but it worked last time I tried.
 If it's possible, the only thing I truly need is to fix the grub error in order to access Windows; I should be able to fix the rest from there. 

Thanks!

---

### Post by the.z.cuber on 2013-12-30
I just looked a bit farther, and it actually looks like it's a windows error (the boot problem). Would this be correct?

Edit: No, it apprars to be Ubuntu after looking again. If it's possible to fix it without installing, even better. I am looking at another hard drive, so that would fix the problem anyway, but I'd still need to access the Windows files somehow.

---

### Post by varunendra on 2014-01-01
> **the.z.cuber said:**
> I am looking at another hard drive, so that would fix the problem anyway, but I'd still need to access the Windows files somehow.

Have you tried an external mouse yet? To me it looks like the quickest, and most promising option at the moment, although certainly not a fix to the problem you are having.

For the touchpad issue, I couldn't get any hint from the logs in the screenshot and so a full syslog and Xorg.0.log can be a great help. If you don't have an external mouse and copying these logs with commandline is the only way, you can copy them with -
```
cp /var/log/syslog /media/*<mount point of your Pen Drive>*/
cp /var/log/Xorg.0.log /media/*<mount point of your Pen Drive>*/
```
..where "*<mount point of your Pen Drive>*" is the path of the directory where your pen drive gets mounted when plugged in. Usually, in Ubuntu, it is "/media/<user id>/<pen drive's Label or Name>/".

So, for example, if your user id is "zcuber" and the label of the pen drive *(the name by which it shows up in the computer)* is "Kingston", the commands will be -
```
cp /var/log/syslog /media/zcuber/Kingston/
cp /var/log/Xorg.0.log /media/zcuber/Kingston/
```

You can confirm the mount point of the pen drive (after it is plugged in) with the 'mount' command -
```
mount
```

Once the files are copied to the pen drive, you can post the log files from another computer which has internet access.

**PS:**
In the meanwhile, you should also try various available boot options, especially those related to acpi, as listed here : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
The 'How To' on using them while booting is given at the top of the same page.

---

### Post by the.z.cuber on 2014-01-02
I had tested with an externl mouse and keyboard to no avail. I don't believe I mentioned this, but I actually work on computers quite a bit. I easily knew this was a motherboard error, not OS. I just got my new motherboard and it works great. 

Thanks for your help; sorry for the hassle. My problem has been solved (motherboard failure).

---

### Post by chkneater on 2014-01-02
Sometimes the USB plugin for the mouse just needs to be placed in a different port.

---

### Post by the.z.cuber on 2014-01-02
That was part of the problem; 2 of the 3 USB ports did not work, nor did the speakers. As I said, it was fairly easy to determine it was a motherboard failure.

---

