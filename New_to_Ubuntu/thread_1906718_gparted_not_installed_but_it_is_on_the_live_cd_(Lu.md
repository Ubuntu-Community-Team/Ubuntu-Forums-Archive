---
title: "gparted not installed but it is on the live cd (Lucid)"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-01-09
:confused: No doubt someone may give me an answer faster than I can work it out.

I am not sure whether I have inadvertently uninstalled gparted, or whether it is not present for a good reason on this system. I do have Disk Utility, and from the Gnome terminal I have fdisk & cfdisk
I feel rather reluctant to just install gparted, as I do not recall uninstalling it and wondered if for some reason it is likely to be inappropriate for use on my system

I am at the moment using 

[LIST]
[*] 64 bit AMD laptop with  integral HDD & CD/DVD
[*]LTS Lucid 10.04 i86 installed on a HDD partition
[*]I have external USB memory sticks and HDD that will mount
[/LIST]

---

### Post by lechien73 on 2012-01-09
No...you're not going mad :P It's not present in a standard install, because the assumption is that most people will do their partitioning on install, and won't need it afterwards.

You can install it from the repositories easily enough :)

---

### Post by HappySmack on 2012-01-09
I believe they are trying to get people to use the "Disk Utlity" in an effort to make things easy for anyone to use. It is the first program I install after an installation.

Time for a:
```
sudo apt-get install gparted
```

---

### Post by Double.J on 2012-01-09
> **aka-John99 said:**
> :confused: No doubt someone may give me an answer faster than I can work it out.

I am not sure whether I have inadvertently uninstalled gparted, or whether it is not present for a good reason on this system. I do have Disk Utility, and from the Gnome terminal I have fdisk & cfdisk
I feel rather reluctant to just install gparted, as I do not recall uninstalling it and wondered if for some reason it is likely to be inappropriate for use on my system

I am at the moment using 

[LIST]
[*] 64 bit AMD laptop with  integral HDD & CD/DVD
[*]LTS Lucid 10.04 i86 installed on a HDD partition
[*]I have external USB memory sticks and HDD that will mount
[/LIST]

Hi there!

No no your quite right gparted is one of the tools that is on the live cd but not the main system - absolutely no reason no to add it again  most of us do. Just remember you won't be able to make changes to any partitions mounted by ubuntu, and you can't unmount your root partition - to make changes to ubuntu partitions you should use the live cd.

That said it's very useful for editing usb sticks, other partitions and drives. Either get it from the software centre or

```

sudo apt-get install gparted

```

it won't be on your desktop this time, I think it's in system tools>gparted... or just type 'gp' in unity's launcher if 11.x

enjoy :)

---

### Post by Double.J on 2012-01-09
> **lechien73 said:**
> No...you're not going mad :P It's not present in a standard install, because the assumption is that most people will do their partitioning on install, and won't need it afterwards.

You can install it from the repositories easily enough :)
> **HappySmack said:**
> I believe they are trying to get people to use the "Disk Utlity" in an effort to make things easy for anyone to use. It is the first program I install after an installation.

Time for a:
```
sudo apt-get install gparted
```

Beat me to it ):P

---

### Post by rgrauer on 2012-01-09
Go to synaptic package manager and type in gparted, it will show if it is installed. It is on the CD but not installed on your hard drive.


You guys are fast!!!!

---

### Post by aka-John99 on 2012-01-09
> **rgrauer said:**
> Go to synaptic package manager and type in gparted, it will show if it is installed. It is on the CD but not installed on your hard drive.


You guys are fast!!!!

Thanks for all the replies everyone. 

John :popcorn:

---

### Post by BlinkinCat on 2012-01-09
Don't forget to mark as "solved" John with the thread tools at top of page - :)

---

### Post by aka-John99 on 2012-01-09
Thanks, I did mark it as solved, I was just reading all the replies.

---

