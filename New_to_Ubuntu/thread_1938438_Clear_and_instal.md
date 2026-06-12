---
title: "Clear and instal"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by No sae daft on 2012-03-09
I have an elderly laptop.  512 Mb Ram  30 Gb hard Drive Mobile Athlon 4 1.2 Ghz.  Currently has Windows XP SP2.  In perfect working order.  

This post is coming from my other PC which will be replaced fairly soon.

What I want to do is to clear the hard drive on the laptop completely - remove everything.  Then I want to instal Ubuntu plus Libre Office, Gimp and UFRaw.  Nothing else.  It will not be connected to the Internet - ever.  Assuming success and a good experience my new PC will use Ubuntu.

My computer expertise is limited to switching off and on and putting programme discs in the drive.  I can also write to CD/DVD.

How do I do this given my level of knowledge?

---

### Post by critin on 2012-03-09
Download ubuntu and burn it to a CD or download unetbootin if using a flash drive, and create a live OS.  (I prefer the flash drive)  Boot up the laptop with it and let it install on entire disk.  It will erase Windows and format for ubuntu.

It should be able to connect to internet for the purpose of updates.  Even Libre Office updates occasionally.
> 
  Then I want to instal Ubuntu plus Libre Office, Gimp and UFRaw.  Nothing else.

Ubuntu comes with these or variations.  You will need internet to add other programs from the Software Center.

---

### Post by ixtok on 2012-03-09
Your system does not meet the minimum recommended requirements for ubuntu 11.10, although it may work. Ubuntu likes more ram. Lubuntu may be a better option.

---

### Post by critin on 2012-03-09
I've run it on 512 with no problems.  If XP is running perfect, so should ubuntu.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

"A good "rule of thumb" is that machines that could run XP, Vista,  Windows 7 or x86 OS X will almost always be a lot faster with Ubuntu  even if they are lower-spec than described"

---

### Post by grahammechanical on 2012-03-09
Do not forget, you can use the Ubuntu software Centre to remove programs as well. You will not want any games, will you? To simplify installation we do not get any options on what we want installed. Everything deemed as part of the Ubuntu distribution is installed. But you can easily remove unwanted applications.

If this machine is never going to be connected to the Internet then not having security fixes is not much of  a problem is it?

Not connecting to the Internet is a very secure way of using a computer.

Regards.

---

### Post by coldraven on 2012-03-09
Just remember that when you have downloaded the install .iso file you need to select "Burn Image" in your disc burning application. It may also help if you burn it at a slowish speed, say 4x, to make sure you get a perfect copy.

---

### Post by No sae daft on 2012-03-10
I downloaded the file to a finger drive.  When I put it in the old PC and double clicked I was asked what program to use to open it.  Eh?

Properties says it is an ISO file 695 Mb but I can't get any further.  

What should I do next other than give up and stick with what I have that works?

---

### Post by critin on 2012-03-10
> **No sae daft said:**
> I downloaded the file to a finger drive.  When I put it in the old PC and double clicked I was asked what program to use to open it.  Eh?

Properties says it is an ISO file 695 Mb but I can't get any further.  

What should I do next other than give up and stick with what I have that works?

Double clicking won't make the flash drive boot.  With the flash drive in position, restart the machine and  choose the button for 'BOOT' that shows on the BIO page.  It will be escape or a F number.  If the bio page closes too fast to see it, restart again.  The button must be pushed quickly.  It will take you to a page to choose the drive you want to boot--choose flash, usb disk, or however it is worded in your machine.

---

### Post by critin on 2012-03-10
> **No sae daft said:**
>  I[/COLOR] [COLOR=Red]downloaded the file to a finger drive[/COLOR].**  When I put it in the old PC and double clicked I was asked what program to use to open it.  Eh?

Properties says it is an ISO file 695 Mb but I can't get any further.  

What should I do next other than give up and stick with what I have that works?

Did you use something like Unetbootin or Universal Installer to get it onto the usb drive?

---

### Post by No sae daft on 2012-03-10
What has happened now is that I read further and saw that I had to download another program to read the ISO file.  It also downloaded (without asking) another 3 programs including "I want that" and "Babylon".  Fortunately a computer literate friend was visiting and he managed, with great difficulty, to remove the other programs.  "Babylon" is apparently a very nasty piece of work.

His advice to me is to leave well alone.  What I have is working and why do I want to change it?  I can't really give a good reason for wanting to change - it seemed like a good idea at the time.

As he pointed out to me I can walk into a shop and buy a new PC, plug it in and it works.  And if I want to add extra software as long as I can put a disc in a slot and follow the onscreen instructions no damage will be done. 

So I won't be trying Ubuntu - too much trouble.

---

### Post by jfb112697 on 2012-03-10
i suggest following everyone elses instructions but with one difference scince ur pc is so old install lubuntu its very light weight and designed for this kinda thing

---

### Post by critin on 2012-03-10
> **No sae daft said:**
> What has happened now is that I read further and saw that I had to download another program to read the ISO file.  It also downloaded (without asking) another 3 programs including "I want that" and "Babylon".  Fortunately a computer literate friend was visiting and he managed, with great difficulty, to remove the other programs.  "Babylon" is apparently a very nasty piece of work.

His advice to me is to leave well alone.  What I have is working and why do I want to change it?  I can't really give a good reason for wanting to change - it seemed like a good idea at the time.

As he pointed out to me I can walk into a shop and buy a new PC, plug it in and it works.  And if I want to add extra software as long as I can put a disc in a slot and follow the onscreen instructions no damage will be done. 

So I won't be trying Ubuntu - too much trouble.

Apparently the iso wasn't downloaded from the official Ubuntu download page, or/and the program used for burning was malware riddled and not the suggested ones or/and user didn't understand the instructions.  Ubuntu does NOT include anything except the os system.  'I want that'/  Babylon had to have been 'chosen' by the user from something else, NOT a linux install. 

Aren't free choices great?  :P

---

### Post by No sae daft on 2012-03-11
No, it came from the Ubuntu site. After download there's a section "show me how" that advises downloading another program to open.  When I clicked on it I was taken to a site that showed several choices.  I clicked on the recommended one but it still downloaded the other programs.  Why not try it and see?

---

### Post by critin on 2012-03-12
Well then I'm sorry you got spammed.   Is this where you downloaded?  [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I've never seen ads for other programs on the download page, even on 'show me how'.  Only instructions.  the word 'recommended' is shown only once and that's where you choose 32 or 64 bit; you click on it to install.

It really does not download anything except the iso.  Perhaps you thought you were on the official site,  it happens.

Guess I was disappointed that a new  potential user gave up so easily.  :(   It's such a good system idea that I want everyone to enjoy it.  But I realize everyone won't.

---

