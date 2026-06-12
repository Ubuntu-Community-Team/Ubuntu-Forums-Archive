---
title: "System dead get a file back?"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by bonedriven on 2012-02-23
Hi forum.
 
I have a live bootable ubuntu(latest version) on my usb drive (persistent mode). Today it can't boot up. My screen is flushed with some kind of a "deleted inode reference" errors. Boot to live mode still gave me the same errors.
 
I worked on my thesis yesterday afternoon with it. Now my 3 hours of work is gone. I don't care about this os at the moment. I just want that single file back. 
 
Yeah I know I should have backed up the file like in ubuntu one or dropbox. But for some reason it didn't work well so...
 
Thanks a lot in advance.
 
 
p.s. ctrl+alt+f2 only brought me more errors not a comman line??!!

---

### Post by jtarin on 2012-02-23
Can you boot from the Live CD? Then you might be able to use Chroot to access your files on the USB.

---

### Post by sadaruwan12 on 2012-02-23
What you can do is use a bootable CD and boot into the live system then use

```
$ gksudo nautilus
```

after that you'll be able to browse the USB drive and hopefully recover your theses.

But recommends that not to do important jobs in live environments or in a persistent system 'cos they have the tendency of crashing also getting corrupted.

---

### Post by bonedriven on 2012-02-23
Hi jtarin, the live cd gave me the same error. 

I hope I can show you the errors but my screen flashes with all kinds of erros at first. "Generating psa or rsa code sth" and then my screen is full of "deleted inode referenced (random number)"

I really dont know why. I didn't do nothing to my system except typed in a document. I didn't install nothing, changed nothing and I'm working on a same computer it just suddenly dies on me. I know the OS is extremely fragile so after I had struggled a week to build it, I was so careful not to break it. Whenever I want to install sth I tested in my virtual machine first. 

Still, it dies randomly. And I don't know when I should push the "shift" button enter recovery mode, so I start spamming it when I enter the unetbootin, but no recovery mode appear. I then got in the screen full of errors. I hit ctrl+alt+f2, I still don't get a command line. And I don't even know what's the error causing the problem.

I just want my file back now.

---

### Post by bonedriven on 2012-02-23
> **sadaruwan12 said:**
> What you can do is use a bootable CD and boot into the live system then use

```
$ gksudo nautilus
```

after that you'll be able to browse the USB drive and hopefully recover your theses.

But recommends that not to do important jobs in live environments or in a persistent system 'cos they have the tendency of crashing also getting corrupted.

Hi sadaruwan12,

I have an almost same copy of the system in my virtual machine. I started the virtual ubuntu, and plugged in my usb drive. I can see the usb drive in my virutal machine. Now what do I do? Thank you!

---

### Post by sadaruwan12 on 2012-02-23
Do you have a OS on your computers hard drive if you do you can use that. And I don't think what you're getting is a software error I think it's due to a hardware device fault.

I got the same type of issue when my TV card went bad I was unable to boot in to the os only errors just like you have. Had to check one by one till I found the cause.

This not because of your pen drive went bad if you use the same pendrive on a different system it might work.

Sorry for the reply I didn't saw your reply to my post. You can use the command I've posted in my earlier post. Open the terminal and type that and press enter.

You'll get the browser with root rights brows to the pen drive and see whether you can get the file you want.

---

### Post by sadaruwan12 on 2012-02-23
> **bonedriven said:**
> Hi sadaruwan12,

I have an almost same copy of the system in my virtual machine. I started the virtual ubuntu, and plugged in my usb drive. I can see the usb drive in my virutal machine. Now what do I do? Thank you!

Sorry for the reply I didn't saw your reply to my post. You can use the command I've posted in my earlier post. Open the terminal and type that and press enter.

You'll get the browser with root rights brows to the pen drive and see whether you can get the file you want.

---

### Post by jtarin on 2012-02-23
Make sure your CD is set to be first bootable. Then when you boot run a ["FSCK".]("http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html"). If you made your USB from the Live CD it might be corrupted itself.Maybe download and burn another.

---

### Post by bonedriven on 2012-02-23
Yes of course I can browse my pendrive. But it's like [this]("http://imageshack.us/photo/my-images/685/fffgl.png/"): I'm noob but I guess the file is in the casper-rw file, which I can't open.

---

### Post by sadaruwan12 on 2012-02-23
> **bonedriven said:**
> Yes of course I can browse my pendrive. But it's like [this]("http://imageshack.us/photo/my-images/685/fffgl.png/"):[IMG]http://imageshack.us/photo/my-images/685/fffgl.png/[/IMG] I'm noob but I guess the file is in the casper-rw file, which I can't open.

Did you tried the command I gave you?

and I don't think with normal user right you'll be able to access the folder. Give the root rights to it and then try it.

Use the command I gave you to get the root access.

---

### Post by bonedriven on 2012-02-23
> **jtarin said:**
> Make sure your CD is set to be first bootable. Then when you boot run a ["FSCK".]("http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html"). If you made your USB from the Live CD it might be corrupted itself.Maybe download and burn another.

jtarin, I can't boot into live mode, same errors. I am now on my laptop, still same errors.

---

### Post by bonedriven on 2012-02-23
> **sadaruwan12 said:**
> Did you tried the command I gave you?

and I don't think with normal user right you'll be able to access the folder. Give the root rights to it and then try it.

Use the command I gave you to get the root access.

It's like this after that command:
[IMG]http://img576.imageshack.us/img576/7391/69693044.png[/IMG]

---

### Post by sadaruwan12 on 2012-02-23
OK, But normally a file doesn't get written in to another file where did you save the file.

---

### Post by bonedriven on 2012-02-23
> **sadaruwan12 said:**
> OK, But normally a file doesn't get written in to another file where did you save the file.

Home/downloads  But I guess it stores in the persistent file, namely casper-rw.

---

### Post by sadaruwan12 on 2012-02-23
WoW O_o thats a bummer.

OK, Try this then bakup your current casper-rw and create a whole new persistent usb drive after making sure it works replace the new casper-rw with the old one.

This might work please try it 'cos I don't this there is a way to extract a file form another type of a file except a compressed one.

---

### Post by bonedriven on 2012-02-23
> **sadaruwan12 said:**
> WoW O_o thats a bummer.

OK, Try this then bakup your current casper-rw and create a whole new persistent usb drive after making sure it works replace the new casper-rw with the old one.

This might work please try it 'cos I don't this there is a way to extract a file form another type of a file except a compressed one.

Yes, I am thinking about it. But I really doubt it can work. Will try it. 

Well, thank god it is just 3 hours of work. So the worst situation is I do 3 hours of repeat work.

So linux filesystem is build like this? When your system dies, your files die along?

---

### Post by sadaruwan12 on 2012-02-23
> **bonedriven said:**
> Yes, I am thinking about it. But I really doubt it can work. Will try it. 

Well, thank god it is just 3 hours of work. So the worst situation is I do 3 hours of repeat work.

So linux filesystem is build like this? When your system dies, your files die along?

No, No it's not like that in your case it's a totally different situation what you're using is a system that runs on file structure and persistent USB pen drive is not like the actual Linux installation.

Compared to many OS's we have the most data recoverable file system when one installs a new system it's advised to create a separate /home partition where all your private data and thesis's get saved.

And we created another partition called the root "/" this contains all the system files. If something happens to your system files and your OS get corrupted you can back up or keep your private data unharmed.

But in your current case it's totally different all the files are in a single file that's why they have folder saying save all here.

Our file systems are not built keep or destroy your data but to protect them and make them easier to get back up.

---

