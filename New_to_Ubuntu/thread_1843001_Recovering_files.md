---
title: "Recovering files"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by richard49 on 2011-09-12
I am totally new to Ubuntu, having been used to Windows for many years.

Anyway...

I have an external hard drive attached to my computer that can only be read by Ubuntu.

I wish to attempt to recover lost files from this drive.

I have looked through the Internet but found any help too technical for me so if you can offer any advice please treat me like a 5 year old child.

Some advice recommended using the Synaptic Package Manager; after reading how to use this several times I got completely lost.

Can you offer any advice / help?

Thanks,
Richard

---

### Post by icarus81 on 2011-09-12
the drive is formated as ext3/4 install this 
[http://www.fs-driver.org/](http://www.fs-driver.org/)
 
and windows should be able to see the drive.
 
Then go get rstudio [http://rstudio.org/](http://rstudio.org/) (they have a trial).  This will be the simplist way get the files back.
 
If you want to do it in ubuntu 
[https://www.volatilesystems.com/default/volatility](https://www.volatilesystems.com/default/volatility) is your best bet but it command line only and very technical for you its more likey more effort than the files are worth. But if you are up for the challenge I recommend it.

---

### Post by Paqman on 2011-09-12
> **richard49 said:**
> 
Some advice recommended using the Synaptic Package Manager; after reading how to use this several times I got completely lost.


Synaptic is a package manager, you use it to install software. The best package I've found for recovering data is [testdisk](apt:testdisk), it contains an app called photorec.

[How to use photorec]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/")

---

### Post by haqking on 2011-09-12
> **richard49 said:**
> I am totally new to Ubuntu, having been used to Windows for many years.

Anyway...

I have an external hard drive attached to my computer that can only be read by Ubuntu.

I wish to attempt to recover lost files from this drive.

I have looked through the Internet but found any help too technical for me so if you can offer any advice please treat me like a 5 year old child.

Some advice recommended using the Synaptic Package Manager; after reading how to use this several times I got completely lost.

Can you offer any advice / help?

Thanks,
Richard


you mean you have a external hard drive that was used in Ubuntu and now you want to recover files from it from within windows ?

or you want to recover lost files from the drive due to deletion etc ?

So do you have Ubuntu now or Windows ?

---

### Post by richard49 on 2011-09-12
I had another read through on using Photorec and had a go.

It looks like its found quite a few files.

Thank you... :)

---

### Post by richard49 on 2011-09-12
> **haqking said:**
> you mean you have a external hard drive that was used in Ubuntu and now you want to recover files from it from within windows ?

or you want to recover lost files from the drive due to deletion etc ?

So do you have Ubuntu now or Windows ?

I have Windows 7 and had an external hard drive which was plugged in fail on me and couldn't be recognised my Windows.

I then installed Ubuntu and found that it would read the external hard drive.

I then managed to get nearly all of the files off this drive but there are still a few that I can't see on the drive and was hoping there was some software available that would allow me to recover these files.

The files are all image files by the way, .jpg, .tiff, .nef etc.

Richard

---

### Post by haqking on 2011-09-12
> **richard49 said:**
> I have Windows 7 and had an external hard drive which was plugged in fail on me and couldn't be recognised my Windows.

I then installed Ubuntu and found that it would read the external hard drive.

I then managed to get nearly all of the files off this drive but there are still a few that I can't see on the drive and was hoping there was some software available that would allow me to recover these files.

The files are all image files by the way, .jpg, .tiff, .nef etc.

Richard


ahhh i see.

Depends when and how they were lost really. 

see here [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

