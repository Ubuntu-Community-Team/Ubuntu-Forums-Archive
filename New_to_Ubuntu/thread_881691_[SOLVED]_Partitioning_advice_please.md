---
title: "[SOLVED] Partitioning advice please?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by mariane_08 on 2008-08-06
OK I've got Hardy 8.04 running nicely on my laptop and ever so slowly getting used to. I feel a sense of liberation not being tied to MS anymore!

So I think I'll try it on my desktop which has a much bigger HD most of which is unused. I probably will reinstall Win XP and dual boot at some point but for now I'd like to move the windows partition and create one for Ubuntu. I'm a bit concerned about doing this! Any tips on how to do it safely and what tool (s) to use?

Mariane

---

### Post by JoneYee on 2008-08-06
> **mariane_08 said:**
> OK I've got Hardy 8.04 running nicely on my laptop and ever so slowly getting used to. I feel a sense of liberation not being tied to MS anymore!

So I think I'll try it on my desktop which has a much bigger HD most of which is unused. I probably will reinstall Win XP and dual boot at some point but for now I'd like to move the windows partition and create one for Ubuntu. I'm a bit concerned about doing this! Any tips on how to do it safely and what tool (s) to use?

Mariane

If your hard drive is not already partitioned, you can do what I did.

Download Knoppix Live CD - use the [qtparted command]("http://simonwillison.net/2003/Nov/30/repartitioning/") from terminal and partition your HDD.

More Information:

[http://www.pcmag.com/article2/0,1759,1902337,00.asp](http://www.pcmag.com/article2/0,1759,1902337,00.asp)

Oh - Always backup before edition partition tables, or making any major system change.

---

### Post by Elfy on 2008-08-06
Make sure it's been defragged a couple of times I actually use Auslogics defrag tool rather than the win one - [http://www.auslogics.com/disk-defrag](http://www.auslogics.com/disk-defrag)

I would use either the partition editor that come son the livecd or download and burn partedmagic - as an image, iso so you can boot with it.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

Resize the win partition to give enough room for hardy, don't format it and then the installer should have the option to use the unallocated space.


Edit - > Download Knoppix Live CD why download 650Mb just to use a partition editor?

---

### Post by PCessna on 2008-08-06
> **mariane_08 said:**
> OK I've got Hardy 8.04 running nicely on my laptop and ever so slowly getting used to. I feel a sense of liberation not being tied to MS anymore!

So I think I'll try it on my desktop which has a much bigger HD most of which is unused. I probably will reinstall Win XP and dual boot at some point but for now I'd like to move the windows partition and create one for Ubuntu. I'm a bit concerned about doing this! Any tips on how to do it safely and what tool (s) to use?

Mariane

If you're more of a nuub, and need only 15-20GB, try 
[http://www.wubi-installer.org](http://www.wubi-installer.org)
```

Wubi is Safe

You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.

```
Otherwise, if you don't want to give that a try, stick around.

p.s. as advanced as I can possibly be, I used wubi too :-)

---

### Post by JoneYee on 2008-08-06
> **forestpixie said:**
> Edit -  why download 650Mb just to use a partition editor?


1. I've never had Knoppix eat anything on over 500 repartitions with customers. (I've had trouble with gparted twice)

2. Its nice to carry around a live CD that is works with RHEL packages for work.

It was just one suggestion of many that will be offered, it works for me.

---

### Post by mariane_08 on 2008-08-06
> **forestpixie said:**
> Make sure it's been defragged a couple of times I actually use Auslogics defrag tool rather than the win one - [http://www.auslogics.com/disk-defrag](http://www.auslogics.com/disk-defrag)

I would use either the partition editor that come son the livecd or download and burn partedmagic - as an image, iso so you can boot with it.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

Resize the win partition to give enough room for hardy, don't format it and then the installer should have the option to use the unallocated space.


Edit -  why download 650Mb just to use a partition editor?

You mean there's a partition editor on the Hardy instalation disk? I didn't notice that but was concentrating on getting it installed right for the first time (I decided to reinstal XP and set up partitions from scratch) For that matter I also made live CD's for Kubuntu, Mandriva and Suse.

Also curious to why you prefer the Auslogics partioning tool?

---

### Post by halitech on 2008-08-06
some people pooh pooh on wubi as it doesn't do a true install of Ubuntu but I think it is a good way of introducing users to using Ubuntu. I would give it a shot first and just select the amount of room you want to give Ubuntu.

It will be slightly slower then a "real" install becuase it will be running in a windows partition and not native linux partition.

---

### Post by Elfy on 2008-08-06
> (I've had trouble with gparted twice) I stopped using it myself earlier in the year and use partedmagic.

I understand it was a suggestion amongst many others that will appear - just a big download for a partition editor is all I was saying :)

> Also curious to why you prefer the Auslogics partioning tool?When I used it the tool defragged files the win defrag had not. 

The partition editor is in sthe sys - admin menu.

---

### Post by JoneYee on 2008-08-06
> **halitech said:**
> some people pooh pooh on wubi as it doesn't do a true install of Ubuntu but I think it is a good way of introducing users to using Ubuntu. I would give it a shot first and just select the amount of room you want to give Ubuntu.

It will be slightly slower then a "real" install becuase it will be running in a windows partition and not native linux partition.

There is a noticeable slowness when virtualizing anything that wasn't designed for it.  Wubi/VMWare, or whatever you choose.

---

### Post by PCessna on 2008-08-06
> **JoneYee said:**
> There is a noticeable slowness when virtualizing anything that wasn't designed for it.  Wubi/VMWare, or whatever you choose.
Wubi is not a virtualizer, It installs on the Windows partition and lets you boot from there, the isnt a huge different in performance, I find it extremely fast.

---

### Post by halitech on 2008-08-06
> **JoneYee said:**
> There is a noticeable slowness when virtualizing anything that wasn't designed for it.  Wubi/VMWare, or whatever you choose.

depending on their system they may or may not really notice it but I agree, there will be a slowness to it

---

### Post by MrPatton84 on 2008-08-06
I'm looking to install Ubuntu on my Samsung R60 Plus. I've read beN..87's guide on doing this [here]("http://ubuntuforums.org/showthread.php?p=5527348#post5527348") but I'm unsure about the partitioning bit. 

The laptop already seems to have a partition (the two drives C and D). Can I just use the D drive to install Ubuntu, or do I need to create a new partition?

Thanks in advance :)

---

### Post by halitech on 2008-08-06
if there is nothing on the partition that windows is calling D: then yes you can tell Ubuntu to use that partition

---

### Post by MrPatton84 on 2008-08-06
No, there's nothing on it :) Thanks very much Halitech!

---

### Post by halitech on 2008-08-06
very welcome MrPatton. Any other problems you may want to start a new thread to deal with :)

---

### Post by MrPatton84 on 2008-08-07
Thanks Halitech - that does seem to be the way to do things around here! :D

---

