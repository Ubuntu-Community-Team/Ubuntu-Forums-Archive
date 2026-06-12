---
title: "Hard drive &quot;Not Initialized&quot;"
date: 2009-01-02
forum: Other OS Talk
---

### Post by The New Guy on 2009-01-02
Today I think I have done one the most stupidest thing I could ever done. I was formating a 40 GB hard drive, I was using Vista, and for some reason it got stock on 80% but I decided to stop it, haaaaaaaaaaaaaaaaaaaaaah bad mistake, so I restart my computer and when it got back to the system the hard drive did not showed up on "Disk Management" I restart it a couple of more times and finally showed up. Here is what it looks like this
[IMG]http://thegabfather.files.wordpress.com/2009/01/untitled.jpg?w=650&h=488[/IMG]
Now I don't know what to do when I click on the "initialize Disk" it give me two options "MBR(Master Boot Record" and "GTP(GUID Partition Table)" I chose MBR but nothing happens a little box appear saying "restart Disk Management and restart the computer. Please I would really appreciate if I get some help on this.

PS My Default OS is Windows XP, I have another master hard drive where I have Vista and Ubuntu, this hard drive that I have problems with is an IDE slave hard drive but I do not want to mess XP up. Thanks again. Cheers! It also when I use the XP it does not recognize the hard drive.

---

### Post by zmjjmz on 2009-01-03
Why not try reformatting the drive again?

---

### Post by handy on 2009-01-03
> **The New Guy said:**
> Today I think I have done one the most stupidest thing I could ever done. 

That is great, it is all up from here. :-D

---

### Post by The New Guy on 2009-01-03
> **zmjjmz said:**
> Why not try reformatting the drive again?
Because when I go to "Disk Management" and right click the disk it does not give the option to do anything, it just give me properties and help.

---

### Post by Raffles10 on 2009-01-03
Try formatting with [Gparted Live]("http://gparted.sourceforge.net/livecd.php").

You can boot from it just like a live cd, if it can see your drive you can reformat as ntfs or fat32 then maybe windows will read it at next boot.

---

### Post by The New Guy on 2009-01-04
> **Raffles10 said:**
> Try formatting with [Gparted Live]("http://gparted.sourceforge.net/livecd.php").

You can boot from it just like a live cd, if it can see your drive you can reformat as ntfs or fat32 then maybe windows will read it at next boot.

I tried it with Ubuntu Live Cd, try to install Windows Vista, XP and even Windows 7 but everytime I try to format it it gives me an error. Ubuntu disk was my hope because I have installed Ubuntu many times in my PC but it just didn't work.

---

### Post by zmjjmz on 2009-01-04
What error does it give you?

---

### Post by Bungo Pony on 2009-01-04
One of the first lessons I learned while using Windows was NEVER use Microsoft's tools when working with drives. Doesn't surprise me that it got stuck at 80%.

Try using the Gparted live CD. It never fails me.

---

