---
title: "Lubuntu won't boot anymore..."
date: 2013-05-15
forum: New to Ubuntu
---

### Post by Strat1290 on 2013-05-15
Hello, I recently installed Lubuntu 13.04 on my old eMac PPC and it was working wonderfully for a few days.  Really breathed life into this old machine... and I need it to get me through the next couple of months!  I don't know if this had something to do with it, but yesterday Lubuntu downloaded some updates.  When I went to boot up the machine today, it will not get past the "fixing recursive faults, but reboot is needed" 

Now, I've searched around, and I can find plenty of info about receiving this error when installing from a disk, however Lubuntu has already been installed as my primary OS.  I received this error when installing and was able to boot with the following parameters 'live video=radeonfb:1024x768-32@60 snd-powermac.blacklist=yes'  this worked only for the initial install from disk, it does not recognize any of these commands now that Lubuntu has already been successfully installed.  

Can anyone help?  I was even going to reinstall the OS but A) I don't want to find myself here again in a few days and B) I cnn't because the disk drive won't open without the machine booted up..

Thanks in advance, looking forward to learning more about Linux!

---

### Post by DuckHook on 2013-05-15
A little bit out of my depth here because you are using a PPC-based Mac, but will try. You can still add these parameters to your boot if you hold down the <Shift>  key (it may be <Esc>  on a Mac) as system is booting. This will bring up the GRUB menu. Type <e> to edit and then add your parameters to the end of the line that begins:```
/boot/vmlinuz...quiet splash $vt_handoff
```You may find more expert help in the subforum "Apple Users".

---

### Post by Strat1290 on 2013-05-15
thanks for the reply, duck.  I've posted in the Apple forum as well to see who bites.  I'm new to both lubuntu and mac, I'd like to try your suggestion however i don't see the line you mentioned.  which key to hold down were you referring to?

---

### Post by DuckHook on 2013-05-15
...this is weird. It seems my postings were stripped of the <> characters. It's the <Shift> key or <Esc> key.

---

