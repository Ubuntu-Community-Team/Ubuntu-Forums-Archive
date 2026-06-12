---
title: "[SOLVED] undate to 8.04 broke my install"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by wog on 2008-05-19
Updating from Gutsy (7.10) to Hardy (8.04).

When I first rebooted after the install I got an fsck error (number 8, if that means anything to anyone). However, Ctrl-D got the installer going again and I thought it was fixed. Little did I suspect.

Then I found I couldn't get into XWindows. I couldn't even get to a shell, even with either of the failsafes. I got (approximately) this error in a box:
couldn't access xml:readwrite:/home/james/.gconf
in /etc/gconf/2/path
could not make /home/james/.gconf

So I figured I was toast and got out the LiveCD and rebooted.
I got a wall full of language options in front of the usual options you get, and my keyboard (usb) is being ignored when I try to select English so I can get to the options before the timer runs out. No good, the first option is chosen (whatever it was) and now I'm getting (mostly) this error:
[numbers] SQUASHFS error unable to read fragment cache block [hex code]

and there's this line which is reading as fast as it can:
sb_bread failed reading block

Now, here's what I *think* is happening. I have my home directory on a physically different drive. I figure the update process somehow lost the info in grub (I don't know how to be prepared for losing this), and then tried to find a home directory and failed in that also. That's why I couldn't login to X.

But I don't know what to do next. I can't remember enough of how to use the mount command to access the drive which has my home directory in it, and I can't find my notes to copy past solutions. 

So I am effectively a newbie once again. Can anyone help me?

---

### Post by Zacariaz on 2008-05-19
I'm rather noob however I think I can get you some of the way:
```
sudo mount -t etx3 /dev/"yoour device here" /mnt/"your mount point here"
```

---

### Post by wog on 2008-05-19
Do you know if there's a way to find other drives besides the one you're on from the command line?

---

### Post by Zacariaz on 2008-05-19
I don't quite understand your question.
Which other drives? Do you mean harddrives? I that case you need to know the device name or whatever it's called and the partition number. usually something like hdb1 or sdb1 for secondary drive.

fx. I have a ntfs partition mount on my computer. I crated a directory in /mnt/ called winroot and from there it's simply sudo mount -t ntfs /dev/sda1 /mnt/winroot

If it had been on another hardrive it would probably have been called hdb1 or sdb1, but the method would have been the same.

---

### Post by wog on 2008-05-19
Next problem: the system isn't letting me use sudo, nor anything else in the /usr/bin directory because they aren't in the PATH variable. And I can't remember how to set variables.

---

### Post by Zacariaz on 2008-05-19
this should help to append the needed path, which i do not now what is.
```
export PATH=$PATH:/add/your/path
```

Of course you will have to do this again if you reboot.

edit:
I don't believe how stupid I am, of course the path is /usr/bin/ (asuming you are right) maybe i need new glasses ;)
So:
```
export PATH=$PATH:/usr/bin
```

---

### Post by wog on 2008-05-19
It's okay, I understood anyway. :)

the mount command can't seem to find the second drive, where my home stuff is. This probably either means I have the file type wrong (not ext3), or else something worse is wrong.

gparted claims it can't display, so I'm without my best tool for information collection.

Also, the shell is apparently not stable. It keeps giving me this error every now and then:

/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint

I suspect it's the system trying to cope with the usb connection of the keyboard and mouse. This is looking more and more like the only solution is to wipe the drive and start over.

Any suggestions? Advice? Impressions?

---

### Post by Zacariaz on 2008-05-19
It could of course be ext2 try it a cross your fingers ;)
I would ask which error you get when trying to mount it, but i probably wouldn't understand anyway.

there is also the posibility that you still don't know the name of your partition and there I can't help cause I can't remember the command to get them listed.

Anyway, I don't think you need to remove your partition in order to reinstall.

---

### Post by wog on 2008-05-19
I think it's fixed, and for that, I thank you.

When I changed everything related to home over to the new drive, I left the old home in a directory called home.old. I changed the name back to home with the 'mv' command, changed the entry in fstab so it stopped looking for the other drive, and now X works again. 

Now it's going to be a matter of finding the missing drive and putting it into fstab properly, but at least I'm somewhere I can deal with. The man pages work again! Yay! :)

---

