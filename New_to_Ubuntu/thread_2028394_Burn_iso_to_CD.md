---
title: "Burn iso to CD?"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by Dafni on 2012-07-18
So, this might be a really dumb question - but I have downloaded the 12.04 iso and need to burn it to a CD as the pc I want to install on does not have a DVD. -- BUT - the iso is 701Mb and CD's don't come any bigger than 700Mb.
Any thoughts?
:confused:

---

### Post by Grenage on 2012-07-18
> **Dafni said:**
> CD's don't come any bigger than 700Mb.

You can get 800Mb CDs.  Regardless, the 701MB image will fit on a 700MB CD, there's a bit extra. ;)

---

### Post by Dafni on 2012-07-18
Thanks Grenage - but I can't seem to find a supplier for 800Mb CD's. I did try to put it onto a 700Mb disc using Nero thinking it might just fit, but the burn failed.
I'll get another ISO burner and try again.

---

### Post by Grenage on 2012-07-18
Back in the day, it was common to 'overburn', which I think allowed up to 12-20MB extra on the disc; that may or may not be built in as standard on modern writing software.

Given that it's an Ubuntu ISO, and no doubt heavily used at this point, it could just have been a bad disc?

---

### Post by Dafni on 2012-07-18
Tried more than 1 disc. I did think it was a bit strange that Ubuntu would release an ISO that was too big to burn on to a standard CD, so with your confirmation that it should actually fit on to a 700Mb disc I will go away and try on another PC with a different burner.
Thanks for your quick response.

---

### Post by Paqman on 2012-07-18
The problem might be Nero, try the instructions here:
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

---

### Post by audiomick on 2012-07-18
Are you able to use a USB stick instead of a CD?

[https://help.ubuntu.com/community/Installation/FromUSBStick/]("https://help.ubuntu.com/community/Installation/FromUSBStick/")

---

### Post by Dafni on 2012-07-18
Solved - :P
Looks like it was Nero. Went to a friends pc and used Roxio which, after reporting that my blank cd actually had 703Mb available space, burned the ISO with no problem.
All I have to do now is install it onto my ancient old p.
Many Thanks to all for your swift replies.

---

### Post by mastablasta on 2012-07-18
aside from the mentioned very good option of using a USB stick (1GB is enough) rather than CD
 
the 701 MB is on hard disk file system. this amount should be reduced on cd ISO system. so 701Mb should easilly fit on 700MB cd. if not as mentioned the overburn funciton can be used.
 
also make sure you burn the disk as iso image not as data.

---

### Post by sanderj on 2012-07-18
> **Dafni said:**
> Thanks Grenage - but I can't seem to find a supplier for 800Mb CD's. 

Here are some examples of suppliers with 800MB CD-R's, also known as 90min CD-Rs ("CD-R 90Min, 800Mb"):

[http://www.amazon.com/Verbatim-CDR90-40x-Spindle-43586/dp/B000HP9NIS/ref=sr_1_1?ie=UTF8&qid=1342605755&sr=8-1&keywords=800mb+cd-r](http://www.amazon.com/Verbatim-CDR90-40x-Spindle-43586/dp/B000HP9NIS/ref=sr_1_1?ie=UTF8&qid=1342605755&sr=8-1&keywords=800mb+cd-r)

[http://www.informatique.nl/890099/philips-cd-r-90min-800mb-40x-10-pack.html](http://www.informatique.nl/890099/philips-cd-r-90min-800mb-40x-10-pack.html)

[http://www.bigdennis.com/cd-dvd-blu-ray/cd-r.html#!/p=clear&knmrk_capaciteit=118&order=name&dir=asc](http://www.bigdennis.com/cd-dvd-blu-ray/cd-r.html#!/p=clear&knmrk_capaciteit=118&order=name&dir=asc)


HTH

---

### Post by pakguru on 2012-09-10
12.04 Ubuntu should fit, just!, on a 700Mb CD. It would seem that your 'burner' programme is the issue.
The best way I have found  to burn a downloaded, Ubuntu operating system iso file to a blank CD is  not to use Brasero, it never seems to work and always tells me that my  blank disc has insufficient space. 
  I use GnomeBaker CD Writer/Burner, which can be installed from Ubuntu  Download Centre. After opening GnomeBaker be careful NOT to select one of the three tabs  in the 'Make new project' section - otherwise you will just copy the iso  file. You need to go to 'Tools' in the top menu bar and select 'Burn CD  Image' - that way you will get all the other files that you need to  install your new version of Ubuntu.
  Good Luck

---

