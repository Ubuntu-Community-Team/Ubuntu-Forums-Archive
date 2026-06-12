---
title: "Need to get into recover mode"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by ABCraine on 2012-05-07
Today I discovered that both admin accounts, on my unbuntu 11.10 machine, no longer have sudo privileges.
I found a clear site that discussed how to fix it ([http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo))

I can't get into recovery mode.
I hold shift from the beginning, I hold shift as soon as I see the motherboard/bios logo,  
... 

Is there a proper/improper time to push the shift key???

Also, any suggestions as to how this might have happened? I've never used the chmod number system, what should the read/write listing be (I don't understand 0440, user,group read?) There were 3 options in the tutorial, and I'm not sure how to find out which one is the problem.

Please help.

---

### Post by buzzingrobot on 2012-05-07
Left shift key is the one that works for me.

But.... I regularly use a USB keyboard.  It will not work for that because the code to interact with the keyboard has not been loaded at that point in the boot process.  (Can't get into the BIOS with it, either.) So, I have to dig out an old PS/2 keyboard.

---

### Post by ABCraine on 2012-05-07
OK, I found an old keyboard (unplugged my wireless keyboard), and held down 
LEFT Shift.  That still didn't work.

It did occur to me that the keyboard might be a problem, since I have a wireless/usb keyboard, but I only have one slot for the old keyboard, so if I have that one plugged in, I don't have a mouse. I'm not comfortable with unplugging/plugging each in just to shut down so I can restart.

Any other suggestions?

---

### Post by jerome1232 on 2012-05-07
Don't hold it down. Tap it repeatedly, I still don't know why everyone says hold it down. Also start as soon as the bios logo, some bioses (bios's? I just woke up and my English is lacking atm) will think you have a stuck key and disable it, I've only seen this one, but thought it might be worth mentioning.

---

### Post by ABCraine on 2012-05-07
Many thanks.  By tapping the left shift I have gotten in.  I noticed that the two logins that were supposed to be admins were listed as "standard".  so following the instructions in the tutorial I type (and get):

root@ubuntuComputer:~# adduser name admin
Adding user 'name' to group 'admin' ...
Adding user name to group admin
gpasswd: cannot lock /etc/group; try again later
adduser:  '/usr/bin/gpasswd -a name admin' returned error code 1 Exiting 


I even tried sudo before the adduser.

Do I need to post this to a new thread now?

---

### Post by jerome1232 on 2012-05-07
perhaps your / was mounted read only?

From recovery mode:
```
mount / -o remount,rw
```

Then try again.

---

### Post by ABCraine on 2012-05-07
Thank you very much.

The tutorial said I would have to remount, but the command was different than the one suggested here (don't know who maintains the tutorial).

The one suggested here worked.

Thanks a lot.

---

