---
title: "&quot;Only root can mount&quot; for USB drives"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by pepperlim on 2008-05-02
After upgrading to Xubuntu 8.04, Xubuntu stopped mounting some of my USB drives when I plugged them in. It always gave me this error message "Only root can mount...".

I tried a lot of things inc. reformatting. Funnily, the USB drives all worked without a problem on Kubuntu. 

Here is how I solved it:

I opened a "Terminal" (found in Applications/Accesories), typed "sudo mousepad" and used Mousepad to open "fstab" (etc/fstab). You should see a red bar in Mousepad giving you a warning about the dangers of editing stuff as "root".

I found these 2 lines in "fstab":

/dev/sdb1                                  /media/sdb1     vfat         defaults                    0  0  
/dev/sdd1                                  /media/sdd1     vfat         defaults                    0  0  

From reading other posts, I realise that my USB devices are also called sdb1, sdc1 etc. You can type "sudo fdisk -l" to see what drives are attached where.

Back in Mousepad, I added "#" in front of both those lines.

# /dev/sdb1                                  /media/sdb1     vfat         defaults                    0  0  
# /dev/sdd1                                  /media/sdd1     vfat         defaults 

Save the file (don't worry, putting "#" in front is pretty safe - if you need to revert back to the original, just remove "#" and everything will be as before) and REBOOT. When I plugged in the USB drive, it worked like a charm!

Now, if you get problems with writing to the drive once you plug it in, open a "Terminal" and type "sudo Thunar". Now right-click on the USB drive in Thunar (the drive icon is on the left) and click "Properties". Now change "Permission" to "read & write" for all 3 options.

Note: I am not a programmer nor do I know much about the internal workings of Ubuntu. I am just the average Ubuntu freak who has Ubuntu installed in my office PC, Kubuntu installed in my wife's PC and Xubuntu installed in my notebook.

---

### Post by juanej on 2008-10-06
i know this is an old thread, but thank you, mount is now working for my usb flashdrives on ubuntu eee.

---

