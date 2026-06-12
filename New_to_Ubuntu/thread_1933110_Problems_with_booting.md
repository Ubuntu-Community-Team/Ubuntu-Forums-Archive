---
title: "Problems with booting"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by ericbn2011 on 2012-02-28
Hi everyone.  I have a Compaq Armada E500.  I'm trying to install Ubuntu 11.04.  I already have Windows XP installed.  I made a floppy disk using sbm.bin and ntrawrite because I cannot boot from a CD on this computer. 

The first thing I did was change the boot sequence in the BIOS so the Floppy is first.  Then I accepted it and rebooted.  I didn't touch any keys but it then loaded into a screen called "Boot Menu" (in the pictures attached).

I don't know what to do from here.  Any ideas?  And no I did not partition the hard drive if that's important.

Thanks
Eric

---

### Post by joetait on 2012-02-28
You didn't add the pictures - doing that or giving a description would be useful.

---

### Post by Double.J on 2012-02-28
Hi ericbn2011, welcome to the forums!

joetait is correct, pictures would be useful; You can either attach an image by clicking edit under your original post and then clicking the paperclip icon next to the smiley face, or if you have an online place for pictures such as photobucket, you can upload the pictures to there and link the url of the image to you post by clicking the icon that looks like mountains (this option is best for ubuntu's server space ;)

In any road, did you follow the Ubuntu guide [here]("https://help.ubuntu.com/community/SmartBootManager")?

Am I correct in thinking that the floppy disk boots fine and you are given a list of things to boot? You are looking to boot the CD, so make sure it's in your CD drive before booting and it should appear in the list under boot menu? You then choose your ubuntu boot CD to boot from, and then the ubuntu CD should load.

Hope it helps?

---

### Post by gordintoronto on 2012-02-28
It's admirable that you are trying to get some use out of a 9-year-old computer, but is it realistic? Does the computer meet the minimum specifications of the OS you are trying to install?

I suspect you could get a vastly superior computer for $60 or the equivalent. Depending on where you live, that isn't much money.

---

### Post by ixtok on 2012-02-29
If your computer is still in its original configuration than it comes no where near meeting the system requirements to run the latest ubuntu.

---

### Post by ericbn2011 on 2012-03-01
I'm sorry everyone.  I noticed I had a DVD in the CD drive and since the computer is incredibly old, it's only a CD reader.  Yes, it turns out that Ubuntu is too big for the computer.  Does anyone have any ideas for another OS that I can use with only 256MB RAM, Intel Pentium 3 1GHz Processor, and 30GB HDD?  Are there any older editions of Ubuntu that would work?

Sorry for the trouble
Eric

---

### Post by Double.J on 2012-03-01
> **ericbn2011 said:**
> I'm sorry everyone.  I noticed I had a DVD in the CD drive and since the computer is incredibly old, it's only a CD reader.  Yes, it turns out that Ubuntu is too big for the computer.  Does anyone have any ideas for another OS that I can use with only 256MB RAM, Intel Pentium 3 1GHz Processor, and 30GB HDD?  Are there any older editions of Ubuntu that would work?

Sorry for the trouble
Eric

Hi there Eric, don't worry we've all been there; the first time I put a computer back together I spent ages trying to work out why it wouldn't boot - I had connected the HDD to the wrong SATA port!

Pentium 3's are supported by ubuntu and at 1Ghz, it's not going to be fast, but it is capable of running. The main area to look at is going to be RAM - are you able to get a cheap stick off ebay? 512 would really be recommended.. you can use the [crucial]("http://www.crucial.com/") website to check what you'd need and the maximum it can take. As for the HDD, 30GB is just about enough - ubuntu will need around 7GB for install and swap partition.

In terms of different versions of ubuntu, The usual responses are Xubuntu or Lubuntu - either should be okay at 512MB, but even though you should be able to boot them on a 256, you may encounter problems once you start running essential programs such as a web browser. 

If you can't do anything about the hardware, take a look at crunchbang - it's the lowest RAM using distro I've used.

If you're thinking about improving the hardware, then you may also want to see if you can get a better processor? pentium 3's are dirt cheap - as in a couple of quid nowadays, don't forget to check the socket and motherboard support first though ;)

Hope it helps!

---

