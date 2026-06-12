---
title: "update stopped by power cut, now disaster"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by achikserei on 2012-04-09
I was updating to Ubuntu 11.10 when the power was cut about 75% thro'.
Now the machine, my wife's, (Athlon 2000+ on Epox 8KRA2, with two 100 GiB PATA discs) refuses to boot.  Just said something about grub failing.  There was no data worth having to lose, so a clean install seemed best.  So I downloaded Ubuntu 11.10 (on my Kubuntu machine), burned the CD and tried booting off it.    Seemed to go OK, if slowly, until it stopped (for 1/2 an hour) with the following on the screen:

                                  Ubuntu 11.10
 

         . . . . * Stopping System V runlevel compatabilitytpted block devices
 
[LIST]
[*]*         Stopping Mount     network filesystemson                                                                    [ OK }
*         Starting enable     remaining boot-time encryted block devices                                    [ OK ]
*    Starting configure     network device security                                                                [ OK ]
[/LIST]
 
[LIST]
[*]*    Starting save udev     log and update rules                                                                     [ OK
*    Stopping save udev     log and update rules                                                                   [ OK ]
[/LIST]
 saned disabled;  edit /etc/default/saned
  
 What does it mean?  Did the power cut ruin the hardware, or what?,  Or is the OS in a tangle?  I am confused. What do I do now?  Please!

(Sorry if the formatting is rubbish.  I had to physically copy the messages into here.)

---

### Post by TheBlueCat on 2012-04-09
> **achikserei said:**
> I was updating to Ubuntu 11.10 when the power was cut about 75% thro'.
Now the machine, my wife's, (Athlon 2000+ on Epox 8KRA2, with two 100 GiB PATA discs) refuses to boot.  Just said something about grub failing.  There was no data worth having to lose, so a clean install seemed best.  So I downloaded Ubuntu 11.10 (on my Kubuntu machine), burned the CD and tried booting off it.    Seemed to go OK, if slowly, until it stopped (for 1/2 an hour) with the following on the screen:

                                  Ubuntu 11.10
 

         . . . . * Stopping System V runlevel compatabilitytpted block devices
 
[LIST]
[*]*         Stopping Mount     network filesystemson                                                                    [ OK }
*         Starting enable     remaining boot-time encryted block devices                                    [ OK ]
*    Starting configure     network device security                                                                [ OK ]
[/LIST]
 
[LIST]
[*]*    Starting save udev     log and update rules                                                                     [ OK
*    Stopping save udev     log and update rules                                                                   [ OK ]
[/LIST]
 saned disabled;  edit /etc/default/saned
  
 What does it mean?  Did the power cut ruin the hardware, or what?,  Or is the OS in a tangle?  I am confused. What do I do now?  Please!

(Sorry if the formatting is rubbish.  I had to physically copy the messages into here.)

I'm not sure if anyone can fix your install, I'm quite new to Linux myself. Anyway, you can always nuke your hard-drives.

Burn this to a USB and boot from the USB in the BIOS.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by PhantomTurtle on 2012-04-09
Try going into Recovery Mode and repairing the packages. To go into recovery mode you have to select it in the grub menu. If the grub menu doesn't show up, wait till you see: Grub loading stage1.5  Grub loading, please wait...  Press ESC to enter the menu and press ESC. Then select dpkg        repair broken packages. If this doesn't work, you can boot into a live cd to recover any important files in the installation by mounting the partition with the current Ubuntu install. Just install over it using the live cd then.

---

### Post by pjman on 2012-04-09
A couple of things to try. 

1) You mentioned you were upgrading to 11.10. I would download the ISO for the version you were on (11.04?) and try booting. If it worked in the past, it should work now. If the old version boots fine and 11.10 doesn't, then something new in 11.10 doesn't work with your hardware. 

2) Try the alternate ISO (text based) of 11.10 to see if you can install that way. I've been in situations where the alternate ISO worked and the desktop one didn't.

---

### Post by achikserei on 2012-04-12
Thank you for all the replies.  The solution was, in fact, silly, so I think I should apologise for asking the original question.  All I had to do was change the DVD drive.  I retried with 11.04 and it was obvious that the drive was misbehaving (clonk, clonk!).  So I swapped it out for an old CD drive I had.  Then I tried a clean install with 11.10 again.  Worked perfectly.  I guess the old DVD drive was on its last legs and maybe the power out finished it off.

Just to put icing on the cake, I then disconnected the 2 PATA drives and put in a 500 GiB SATA drive (having swapped that out of my Kubuntu machine for an even bigger drive - oh! the woes of being an amateur photographer) and started again.

Now it all works wonderfully and I have even managed to replace my wife's old Thunderbird email records, which I had carefully saved onto an old but effective USB drive before trying the upgrade.  Now I have to learn how to use Samba so I can simply save things to my Kubuntu machine. And I should reconnect the PATA drives so as to make a place for archiving etc.  That too will be fun, because I know how to repartition etc., but I have yet to get my head round "mount".

Thank you all again for the replies.  I am truly grateful.  I especially like Phantom Turtle's suggestion about going into recovery mode and using dpkg        repair broken packages.  I had no idea that one could.  I did not have to try it this time, but It is definitely in my mind for next time.

---

