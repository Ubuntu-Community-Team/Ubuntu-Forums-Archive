---
title: "Cant install on Vista 64-bit Dell Studio 540"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by gacostac on 2008-10-26
Hi everyone
I just bought a Dell Studio 540 that has a Quad Core 2.3 HZ intel Chip and windows Vista 64 bit on it. 6Gb of ram. 
I used ubuntu some years ago and wanted to to get back on it but can'd get it to work.
I downloaded de 64 bit Ubuntu 8.4, burned the image on a disk, used the checksums software to search for errors, and installed it using Wubi...
then when i restarted the computer, i got a screen asking me to choose between Vista or two options of Ubuntu. 
when I chose ubuntu it loads the kernel and the red bar starts running, after a minute or so it freezes and gives me an error (I will try to post the error in a next post after i restart my computer). So it never worked.
Then I tried the normal installation booting the computer from the cd and the same thing happened. It loaded the kernel and the red bar started running, after a minute or so it froze again  and gave me the same error....
I can't even check the cd for errors. 
I have downloaded ubuntu like 4 times thinking I got a bad download or a bad CD burn...

Please any help is appreciated, i want out of Vista!!!

---

### Post by inxygnuu on 2008-10-26
I have a couple things to say:

1) don't completely delete vista, just in case of compatibility or some other problem. Unless you wasted $400, just wanting to access email, edit pictures, and go online.

2) the thing is probably freezing because you have a 23 Hz processor,Ubuntu needs more than that.:lolflag:

3) Try holding the ctrl (control) button. I use 8.10, and If I don't or stop holding the control button, then the loading freezes.

---

### Post by inxygnuu on 2008-10-26
and make sure that You use i386, I think that might be the prob, and if you are using the i386, then try amd64.;)

---

### Post by Paqman on 2008-10-26
That error message would be very useful. Once we have that we should be able to start steering you in the right direction.

In the meantime, can you log into recovery mode and get to the command line? If so we can get you to pull out the boot logs and see where it's going awry. What about safe graphics mode?

---

### Post by gacostac on 2008-10-26
Thanks for your replies

here goes the error:
"
BusyBox V1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in shell (ash)
Enter 'help' for a list of buit-in commands.

(iniframfs)
"

---

### Post by gacostac on 2008-10-26
> **Paqman said:**
> That error message would be very useful. Once we have that we should be able to start steering you in the right direction.

In the meantime, can you log into recovery mode and get to the command line? If so we can get you to pull out the boot logs and see where it's going awry. What about safe graphics mode?

I tried safe graphics mode (as well as holding down the Ctrl button...) and it didn't help. Got the same message

I don't understand how to log into recovery mode and go to the command line, can you explain me how? thanks, Im very new to all this.

---

### Post by eolson on 2008-10-27
You might want to try the Dell support forum. 

[http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

---

### Post by gacostac on 2008-10-29
Im posting using Ubuntu 8.10 :)

Apparently the problem was with Ubuntu 8.4 .... I downloaded 8.10 last night and installed it today and it runs great! 

Thank you all for your help anyway :)

---

### Post by blackpaperk on 2009-12-08
I got the same issue using, though I had Win7 preinstalled and trying v 9 worked instead.

---

