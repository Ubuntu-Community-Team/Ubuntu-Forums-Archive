---
title: "Cannot get write permission for lightdm.conf"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by mustrumridcully on 2013-05-02
I edited lightdm.conf to add allow-guest=false, but like an idiot typed allow-guest-false with a hyphen instead of an equal sign. On restart Ubuntu cannot detect graphics and prompts to start in low graphics mode. Choosing this or exit to console results in an infinite loading splash screen. I have booted to command line to try to edit the file that way but I cannot get write permission to the file. So far I have tried:

sudo pico lightdm.conf 

And 

sudo chmod u+w lightdm.conf

Both return 'file system is read only'

So I then tried 


su -

...but this doesn't alter outcome of above. 
Thanks in advance, I'm new to Linux / Ubuntu and I bloody love it.

---

### Post by Cheesemill on 2013-05-02
When you boot in recovery mode your entire root partition is mounted as read-only. To remount it as read-write use the following command...
```
mount -o rw,remount /
```

You should now be able to edit the file using...
```
nano /etc/lightdm/lightdm.conf
```
You don't need to use sudo in recovery mode as you are already logged in as root.

---

### Post by mustrumridcully on 2013-05-02
Thank you so much, this worked like a charm.

---

