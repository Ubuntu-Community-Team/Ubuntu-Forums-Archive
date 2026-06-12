---
title: "Cman not loading"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by foca on 2008-10-26
I just upgraded to 8.10 from 8.04. After flollowing the whole process it arrived up to a point that it needed to reboot, which I did. Aftewr that i recieved a message that says 

"fence tool  waiting to cman to start" and 
CCS [4353[ unable to conect to cluster infraestracture. 

I am not able to pass that point.

what should I do?

than you very much.

santiago

---

### Post by cube3x3 on 2008-10-27
I had the same problem.

Here how to fix it: 

1. Get a Live CD of Ubuntu 8.10 (I think any linux live CD should work though)
2. Boot with that live cd
3. After booting, mount your computer's root partition to /mnt/repair using following command (assuming your root partition is in /dev/sda1
```
sudo mount /dev/sda1 /mnt/repair
```
[INDENT]If you have separate /home partition then mount it also to /mnt/repair/home[/INDENT]
4. Next give following command
```
sudo chroot /mnt/repair
```
5. Then change to your computer user using su [your_username]
6. Then remove the cman and libfence3 packages using,
```
sudo apt-get remove cman libfence3
```
7. Then 'exit' and reboot.
8. Enjoy Intrepid

This steps solved my problem, hope also solves yours.

---

### Post by foca on 2008-11-04
Thank you very much. it worked very well

regards
santiago

---

### Post by simontaylor on 2008-11-04
I'm currently experiencing the same problem. I tried booting from an old Feisty disc and received this:

> mount point /mnt/repair does not exist

Perhaps I've not got to root?

Please help. Am newby // so posted a new thread to Absolute Beginners Forum... But any additional help would be greatly appreciated.

Best,

Simon

---

### Post by foca on 2008-11-05
The same thing happened to me.

I had tocreate the dir first name /mnt/repair and the I mounted it to that dir. then it asked if I wanted to erase everything and i did it.  I don't know if was ok but it worked.

---

### Post by simontaylor on 2008-11-05
I have tried mkdir -- can you please tell me how you exactly what you put into terminal? (I'm afraid I'm not as conversant with terminal use as I should be.) 

And does it make a difference where you get into the terminal from? I'm on a Hda6 back up of Feisty at present. 8.10 has locked me out. Both recovery versions and generics return this: fence_tool: waiting for cman to start ... etc. etc.

then CCS [4394]: [CCS ] Unable to connect to cluster infrastructure ... a new attempt every 30 seconds.

Your help is greatly appreciated.
Thanks,

Simon

---

### Post by sdudley on 2008-11-05
Similar issue with a clean install of 8.10/x86.64. I did notice that after waiting five minutes, the cman error prompt appeared to time out and Ubuntu resumed booting as usual. Not sure what the cman thing is all about however given the symptoms, the point in the boot process and the series of error messages I'm wondering if it has something to do with mount points. I did notice a few messages fly by before the cman error...something about Red Hat GFS as if a series of drivers were being loaded.

Update: Waited the customary five minutes or so time out period and then logged into the GUI and using a terminal session removed the cman and libfence3 packages with the sudo apt-get remove cman libfence3 statement per Cube3x3's advice minus the disk partition items. Restarted and all is well. Apparently cman is some sort of cluster manager. I don't know if I opted for this during the install or it was inherited from a package I selected during the installation of 8.10. Here's the man page link for cman [http://manpages.ubuntu.com/manpages/intrepid/man5/cman.html]("http://manpages.ubuntu.com/manpages/intrepid/man5/cman.html")

---

### Post by simontaylor on 2008-11-06
sdudley - great. That's what I'd surmised. I'm simply all thumbs/dumb when it comes to discovering where things are or how to get at them. 

If you can bear to dole out a little more downhome advice: I don't know what you mean by a customary 5 minutes; how did you log in to the GUI? what exactly in Terminal? 

In the past I've had trouble finding root partition. Here's a list of my partitions (all ATA):


> 
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612       26485   191767905    7  HPFS/NTFS
/dev/hda3           26486       28562    16683502+  83  Linux
/dev/hda4           28563       30401    14771767+   5  Extended
/dev/hda5           30235       30401     1341396   82  Linux swap / Solaris
/dev/hda6   *       28563       30158    12819807   83  Linux
/dev/hda7           30159       30234      610438+  82  Linux swap / Solaris  

I seem to be in hda6 writing this: an early backup of Feisty 7.04 which is actually quite functional. Still - I'm missing some handy things - like full address books - somewhere inside the above partitions. 

Thanks sdudley,

Best,
Simon

---

### Post by simontaylor on 2008-11-06
I exaggerated in the previous post. Feisty does not give me access to full home folder. I'm missing every document and folder I've added over the last year - in other words, a year's work - and can't seem to gain access to them through the other partitions.

---

### Post by simontaylor on 2008-11-06
small correction - inside cited partition list I'm writing this from hda3 not hda6.

---

### Post by sdudley on 2008-11-06
The 5 minute time out period referenced earlier is an approximation. When booting up after a restart, I simply left it alone until the cman error message cycle went away and the boot process completed. I logged in and used a terminal session to remove the offending applications which seemed to be the root cause for the cman error message as the error message and issue has disappeared with subsequent restarts. My symptoms may indeed be unique although employing some sort of mount point repair process seems a little draconion and not something one would have to accomplish with Linux.

---

### Post by simontaylor on 2008-11-06
I presume it would be a breach in netiquette to ...  UNbleepinBELIEVABLE! 

sdudley is right. The cman message does not carry on ad infinitum. After 5 min.s the GUI loads. 

Whence, head directly to Terminal. And -

> sudo apt-get remove cman libfence3

Answer yes to removing all of cman (for link to what this is see sdudley's post above).

I've thanked sdudley before but THANKS AGAIN.

8.10 is up and running. 

I'm surprised this small glitch is not more widely published. And thankful I can look back and claim, albeit belatedly, with a superior air, patience is a virtue. Even with Ubuntu.

Not only this ----- but after many months of 8.04 unable to raise MEMLOCK limits - so unable to burn cds or dvds - K3b works again! 

I can resume my bean-imbibing penguindom - as an Ibex.

Simon

---

### Post by simontaylor on 2008-11-06
Now I can't find how to mark this THREAD AS SOLVED.

---

### Post by peppermonkey on 2008-12-18
Hey, 
you can avoid the 5 min. wait, and having to use the boot cd all together. the magic password is cntrl+Alt+delete when you get the error message.   ;p

---

