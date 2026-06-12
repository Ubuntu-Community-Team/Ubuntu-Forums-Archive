---
title: "cloning drive/partition"
date: 2014-12-27
forum: New to Ubuntu
---

### Post by prle99 on 2014-12-27
Hi all,
im complete noob not only for ubuntu but for technicall maters concerning Pc so i need help in a problem i have .

So because i had some hardware changes i needed to reinstal my windows  a few times ,and now i finaly have stable version of it and all this reinstaling is making my head hurst,few times i messed my linux instalation while i was reinstaling windows:(
Now i have stable linux instalation on one drive and stable windows on other HD.

I done want to make image of a HD since i cant add files  to it later ,so i want to  make clone of my HD on my external hd,i tried clonezilla live but then i discovered that my external dirive is some 104 clusters or was it bites smaller than original and clonezilla aborts operation and  mbr section on external drive is also smaller than mbr(hidden system ) of my original drive
(it is not recomended to clone  to smaler drive so i abort it)

Also if i resize partition with garted from ubuntu enviorment will it mess my widows boot files or will it keep it as they are?i was thinking if i resize  my Hd where i keep windows i can then make clone of that partiotion on my hd but thne im nort sure if i will be able to boot  form that external drive?



So what i need is to make 
1.bootable clone of my HD  on my external disk  
2.on which i can add files i need to safe guard 
3.and in case of emergency be able to boot my system from this external drive
4.is it posible to make  a second bootable clone  of my linux drive on same external hd???(i think i saw an option of  instaling ubuntu on external drive so  i was thinking of doing this after i cloned my  w7 on external drive and  so have  clean version of ubuntu also )

all my HD are 500gb in size so i need to save :
 hda ubuntu (500g)  effectivly only about 10g data worth for saving 
 w7 hdb (500g)  about 170g data needed to clone
- on one external hdc(500g)

So can some one please advise me how to do this?

Thanks for help

---

### Post by Mark Phelps on 2014-12-27
> ,so i want to make clone of my HD on my external hd,i

Cloning a drive is making an EXACT copy -- that's what it means, so it makes sense that it requires the same size drive or larger.

If you can shrink down the size of the partition, you could clone that partition to an external drive.

---

### Post by Jonathan Precise on 2014-12-27
Hello prle99.

Yes, you can shrink the drive, but be sure to shrink Windows using the partitioning tool in Windows, and then REBOOT TWICE and run chkdsk for Windows to be aware of that change. You should shrink the Ubuntu partition though from GParted, be it on the GParted live DVD, or Ubuntu live DVD with GParted installed. Just make sure to be careful there, as you might not be able to boot there again.

---

### Post by monkeybrain20122 on 2014-12-29
Don't know about Windows, for Linux the best tool is fsarchiver
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

Note: doesn't work with gpt.

---

### Post by Mark Phelps on 2014-12-29
BTW, Windows does not BOOT from an external drive.  So, if your cloning plan was to copy Windows to an external drive so you could boot from it, that plan will not work.

Which is why, those of us who regularly backup their Windows installs to external drive use Imaging, not Cloning.  The Imaging does compression, thus reducing the space needed (often by less than 1/2), and the images can be used to Restore a working version of Windows.

---

### Post by Bucky Ball on 2014-12-29
Welcome. For cloning any OS or paritition, [Clonezilla]("http://clonezilla.org/") is your friend. These links might be helpful:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Hope that helps and good luck.

---

### Post by prle99 on 2014-12-30
First tnx every1 for help
FS archiver is way beyond my understanding of files and pcs  so i tried clonezilla again this time to make an Iso  with live usb.
(yes my plan was to run win7 from external Hd in case something happens and i need to restore it,i cant add files to iso thats why i tought this could work)tnx for info on this it seams im doomed to make iso...
Problem is everything goes great  but after some 10min my pc just shts dwon .
its same with  any live softwer operation so i cant make image:( or anything
If i try to instal something be it windos or any linux distro(i sucessfuly instaled win ubuntu ,mint fedora with out power failure) this doesnt happen instalation goes with out problem only if i run  live back up softwer  like clonezila-redo-or minitoolwizard ,
pc shuts down.
I have it pluged in power supply, but batery is always at 50% and nor recharging,i have all power save options turned of so im at loss why this hapeneds,when in OS linux or win7  laptop runs with out any problems(just batery not recharging)
Is there some bios modification for power shut down after about 10-15 min? shoul i take batery out completely?
Tnx again

---

### Post by Bucky Ball on 2014-12-30
Welcome. This sounds nuts, but shutdown the machine completely, take the battery out, plug the machine in, boot from the Live disk/USB again.

I know, but it has worked in the past, and for someone just recently. Batteries die, and the effect that has on the laptop can vary. I had a HP and dead battery didn't matter. My current Toshiba didn't cope, wouldn't even boot. Was giving me issues similar to yours. Took battery out and I'm posting from that machine now with dual monitors, faultless for a couple of years at least.

Laptop batteries should be run down regularly. Once every few months if you are running the lappy from wall socket. Think about it: the battery is full but is constantly charging. Something's gotta give. 

Anyhow, could be barking up the wrong tree, but shutdown, pull the battery and reboot. I am guessing, but worked for me a few years ago, worked for someone else I helped here recently. ;)

* If you are not using a laptop, the above is irrelevant, obviously. If a desktop it could still involve the battery. If the desktop is fairly old, then the small round battery on the motherboard could be causing a problem. Try replacing.

---

### Post by monkeybrain20122 on 2014-12-30
Fsarchiver is actually way easier than clonzilla, there are only two commands(one to save the other to restore) and more flexible as it only 'clones' the file system so you can restore to any drive large enough to hold the restored files. Clonzilla requires the targeted partition to be larger than the original one even the original one may be mostly empty, so you would have to do the slow and risky operation of shrinking the original partition with gparted first before cloning if the targeted drive/partition is smaller. This is a show stopper for my purpose.

---

