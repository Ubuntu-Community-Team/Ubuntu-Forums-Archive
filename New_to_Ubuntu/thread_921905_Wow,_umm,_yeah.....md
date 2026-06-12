---
title: "Wow, umm, yeah...."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Solais on 2008-09-16
Well I was trying to install xp and it said it couldn't detect any hardware (hard drive) drivers. i checked everything and it detected the hard drive but when i was going to install xp it just wouldn't work so i installed linux first and i went to hard drive and deleted everything that was in there and installed linux, i want to install xp again and dual bot them or however you call it but when i put the xp home cd it wont detect the hard drive :( how can i "install my hard drive as a driver" lol:confused:

---

### Post by dhtseany on 2008-09-16
Any idea if you are running a RAID configuration? Could also be an additional SATA controller or even IDE controller that XP requires drivers for.

---

### Post by Solais on 2008-09-16
> **dhtseany said:**
> Any idea if you are running a RAID configuration? Could also be an additional SATA controller or even IDE controller that XP requires drivers for.

Hmm o.o?:confused:

---

### Post by Zzl1xndd on 2008-09-16
Probably not running a raid, but Windows doesn't often play well with SATA drives. So you might need drivers to install there is an option near that start of the windows installation to install SCSI or SATA drivers I don't remember what key you have to press, but the drive should have come with a disk of some kind for it. 

If you don't mind me asking what is it you do with Windows?

---

### Post by kshane on 2008-09-16
You should have installed Windows first.  It has problems with Linux boxes when it's being installed second.

I dual boot Ubuntu and Vista (gads!  I hate Windows...)  And I have redone this box a million times and set it up to dual boot with Vista.

Otherwise, there's a lot of changes to make to the system, etc...  Not sure how...

Kevin

---

### Post by Solais on 2008-09-16
Ok summary: got bored of xp, wanted to try vista. Tried vista, after 28 days my trial was gonna be over, so I put the XP Home cd and hit Install from the PC Setup thing (boot from cd). it said i couldnt detect my hard drive, so i went to vista and researched it on google, and it edned up saying they do that un purpose so you dont go back to xp, so i used the DBAN, to completelly delete my hard drive. I booted xp home cd again and it said the same thing, i put linux live cd and after a while i could install it, so after i week i try xp again, and it still couldnt detect my hard drive. May anyone help me? I made a thread about this but forgot to put details

---

### Post by technotitclan on 2008-09-16
its F6 to install 3rd party drivers. while setup loads there will be a prompt that will be there for about 2 seconds that says :press F6 to install 3rd party drivers" also if you do have a sata hard drive then you may want to slipstream the sata driver on to it with NLite. XP doesn't have ANY sata drivers built into it. Vista does have sata drivers.

---

### Post by Zzl1xndd on 2008-09-16
> **technotitclan said:**
>  XP doesn't have ANY sata drivers built into it. Vista does have sata drivers.

As does Linux so its a safe bet this is the problem

---

### Post by Solais on 2008-09-16
> **technotitclan said:**
> its F6 to install 3rd party drivers. while setup loads there will be a prompt that will be there for about 2 seconds that says :press F6 to install 3rd party drivers" also if you do have a sata hard drive then you may want to slipstream the sata driver on to it with NLite. XP doesn't have ANY sata drivers built into it. Vista does have sata drivers.

sata?

---

### Post by Zzl1xndd on 2008-09-16
There are Parallel and Serial ATA hard drives PATA and SATA for short. PATA are the older kind connecting with a ribbon or IDE cable, the newer connect with a SATA cable witch is normally a thin red cable, Windows XP doesn't have drivers for this type of drive and they need to be installed during the set up so XP can find the drive.

---

### Post by Solais on 2008-09-16
this? [http://www.nliteos.com/download.html](http://www.nliteos.com/download.html)

---

### Post by Zzl1xndd on 2008-09-16
Nlite is for making slipstream disks so you can place extra drivers, or service packs onto the disk, what is the make/model of your Computer (or preferably your hard drive)?

---

### Post by Solais on 2008-09-16
How can I save a folder from Linux? cause i guess when i install xp ima replace linux for a while, but i have like 20gb of music and others and i want to make a folder so when i install xp just drag it to desktop :confused:

---

### Post by Solais on 2008-09-16
Ok, Im running on Ubuntu, want to run on XP. but I want to keep a folder with me stuff ^^, how do I do this :), cause if I install xp now my hard drive gets formated right?

---

### Post by dhtseany on 2008-09-16
1) Use another XP PC to transfer your music onto for storage
2) Burn a couple of DVDs with your music on it
3) Borrow a friends portable hard drive

---

### Post by Solais on 2008-09-16
> **dhtseany said:**
> 1) Use another XP PC to transfer your music onto for storage
2) Burn a couple of DVDs with your music on it
3) Borrow a friends portable hard drive

OH YEAH! burn into a dvd :P, forgot about that, thanks hun :lolflag:

---

### Post by Dougie187 on 2008-09-16
Do you know if you still have grub installed? I have run into issues like this before when I install linux (wipe hdd) and then try to format the drive and put windows on it. The boot loader sometimes doesn't recognize that its able to write to it. One thing you could try to do.. is wipe the drive with gparted. Or you could try booting onto the windows cd and going into recovery to rebuild the mbr.

---

### Post by Solais on 2008-09-16
> **Dougie187 said:**
> Do you know if you still have grub installed? I have run into issues like this before when I install linux (wipe hdd) and then try to format the drive and put windows on it. The boot loader sometimes doesn't recognize that its able to write to it. One thing you could try to do.. is wipe the drive with gparted. Or you could try booting onto the windows cd and going into recovery to rebuild the mbr.

OK so I insert the cd and boot it, how can i run to recovery o.O, and how do i rebuild the mbr:confused:, what ever mbr is lol :KS

---

### Post by technotitclan on 2008-09-16
if you look at you hard drive inside of you computer, does it have a wide grey cable comming out of it or a red cable thats about half an inch wide?

---

### Post by ctoaun on 2008-09-16
> **tweakedenigma said:**
> There are Parallel and Serial ATA hard drives PATA and SATA for short. PATA are the older kind connecting with a ribbon or IDE cable, the newer connect with a SATA cable witch is normally a thin red cable, Windows XP doesn't have drivers for this type of drive and they need to be installed during the set up so XP can find the drive.

I could not agree more. Also, like someone else said, you need to install xp first. If you install it second, you might install it beyond the 2 gig boundary, in which case it won't boot.

If you decide to create partitions, may I suggest Gparted. I loathe partitioning without it. gparted is free, more user friendly, and in my opinion, it does a much better job than the Linux OS partitioning software. 

 Symantec sells a partitioner "Partition Magic" for ~$70. Symantec acquired "Powerquest."This means that Symantec's "Partition Magic"  is just repackaged (read: old) Powerquest Partition Magic." Not all of the error codes for it show up on their site. Presumably they don't want you to know that it can still be a system wrecker. Over the past five years, I've used it twice (I've weakness for bells & whistles) and I've regretted it every time.

---

### Post by Zzl1xndd on 2008-09-16
OK I think we got this kid going all over the place for a simple problem. First I'm pretty sure he said that he wiped the drive with Dban, then installed Ubuntu because his Windows XP disk didn't recognize his hard drive. A couple of us are assuming that the computer has a SATA hard drive and needs extra drives for Windows XP to go back on. 

So lets start from the Top Solais, What is the Make and Model of your computer so we can find out if it is a SATA drive.

---

### Post by mike1234 on 2008-09-16
> **Solais said:**
> OK so I insert the cd and boot it, how can i run to recovery o.O, and how do i rebuild the mbr:confused:, what ever mbr is lol :KS

MBR=master boot record. Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password. Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer. I had to use this on a PC that I had corrupted the MBR with by using a boot manager. The only good way to do what I believe it is you are asking is to install XP first, ubuntu second and then you'll have grub as a boot manager. SATA drives on my system have never been a problem during install. (and I have an original XP disk without any service packs on it). Heres more about Vista related problems because you now want to go back to XP.  [http://support.microsoft.com/kb/931760](http://support.microsoft.com/kb/931760)



M.

---

### Post by Dougie187 on 2008-09-16
Well, i don't remember how to boot into recovery, but if you boot using the windows cd then on the screen that is blue or grey there is an option that says Recovery Console or something like that.
You can view the screen on this page, it is number 4
[http://articles.techrepublic.com.com/5100-10878_11-6031733.html](http://articles.techrepublic.com.com/5100-10878_11-6031733.html)

after you get to that, its going to be a command prompt, and you can type help to get a list of commands.
Also, you can look through this thread for the options.
[http://ubuntuforums.org/showthread.php?t=134785](http://ubuntuforums.org/showthread.php?t=134785)

---

### Post by sudo_chop on 2008-09-16
> **Solais said:**
> Well I was trying to install xp and it said it couldn't detect any hardware (hard drive) drivers. i checked everything and it detected the hard drive but when i was going to install xp it just wouldn't work so i installed linux first and i went to hard drive and deleted everything that was in there and installed linux, i want to install xp again and dual bot them or however you call it but when i put the xp home cd it wont detect the hard drive :( how can i "install my hard drive as a driver" lol:confused:
 
Usually that message isnt for the HDD's (hard drive) driver not being present, but for the HDC's (hard drive controller) driver. If you are using a pre-SP2 XP disk then chances are they just aren't there. At any rate, I would suggest using nLite to integrate SP3 into your XP disk, and even better would be to find out what hardware you have and integrate those drivers specifically. Sometimes this can be a pain, I have done XP installs where I integrated an HDC driver and it still didn't detect the HDD during install. Sometimes, you just have to make a floppy :(
 
I think nLite has tutorials to show you how to integrate a service pack, but if you need help of course, just ask here.
 
> **Solais said:**
> How can I save a folder from Linux? cause i guess when i install xp ima replace linux for a while, but i have like 20gb of music and others and i want to make a folder so when i install xp just drag it to desktop :confused:
 
I'm not really sure the best way to do this besides moving the files to an external hard drive (maybe you know somebody who has one) or even an ipod (as an external hard drive)
 
You could partition the space for your windows install beforehand with gparted I suppose, and then assuming your dual boot works (idk much about it, i've only ever done linux with windows already installed) just copy the files over after.
 
Hope that helps!
 
Keep us updated!
 
-sudo chop

---

### Post by sudo_chop on 2008-09-16
> **Solais said:**
> OK so I insert the cd and boot it, how can i run to recovery o.O, and how do i rebuild the mbr:confused:, what ever mbr is lol :KS
 
 
I'd say first order of business would be moving those files somewhere safe, before we go messing up (potentially) your MBR! :)
As I doubt you have burnt 4 DVDs in half an hour

---

### Post by Solais on 2008-09-16
Oh wow :confused:, ummm, english plz ^^;;;?:confused:, ok ima take pics of me pc lol one sec and the hd

---

### Post by Solais on 2008-09-16
Hmm, um whats the program for burning data dvd disk on linux btw? (let's start with that hahaha xD)

---

### Post by Dougie187 on 2008-09-16
Brasero

---

### Post by mike1234 on 2008-09-16
> **Solais said:**
> Hmm, um whats the program for burning data dvd disk on linux btw? (let's start with that hahaha xD)

places -> CD/DVD creator

M.

---

### Post by Solais on 2008-09-16
Oh my god, oh my god..... my stuff ended up being a 98.gb file :shock::shock::shock:

---

### Post by Solais on 2008-09-16
Ok guys, thanks for all the help, I made all this into a document for future use. But, you know what, I think ill just stay with Ubuntu lol, my major concern was my gaming, since I play alot of pc games, but i got to work Ragnarok WoW and Warcraft 3, and I entertain myself figuring out this Linux programs. Just started Linux like a week ago, sorry for so many newbie questions and stuff, but thanks again guys, I'm gonna go to sleep, very tired, night guys, take care all :)

---

### Post by cobra741 on 2008-09-16
you'll more than likely be able to fix this problem by going into your BIOS (usually by pressing F2, ESC or DEL as soon as the machine comes up after restart/power up) 
then go into your SATA settings and set the SATA drive mode to Compatability Mode/Legacy Mode. 
your SATA hard drive will then be detected as a standard IDE drive which the Windows XP cd will detect. 

in Windows setup you'll be able to delete the existing partitions on the hard drive and make a new one, just make sure you leave at least 8gb free for your linux partition (i'd actually try to leave about 20GB so you've got plenty of room to play with). 

setup windows as normal then whack in your ubuntu live disk and get linux cranking making sure you only install linux in it's own partition. 

after that you should be sweet :)

---

### Post by mike1234 on 2008-09-16
> **Solais said:**
> Oh my god, oh my god..... my stuff ended up being a 98.gb file :shock::shock::shock:

21 blank DVD discs. Wow that's too much "stuff".

M.

---

### Post by Solais on 2008-09-16
By the way my Hard Drive has the red cable connection, so that is Sata yes?

---

### Post by Solais on 2008-09-16
> **mike1234 said:**
> 21 blank DVD discs. Wow that's too much "stuff".

M.

Lol

- Over 3k on pictures
- 16.8gb of music plus friends music 4-8 gb
- world of warcraft file 10-13 gb
- heroes season 1-2
- dexter series completely
- scrubs v7
- many windows programs setup i kept for future use

I want a 1 TB Hard drive :popcorn:

---

### Post by karlr42 on 2008-09-16
I believe you can play WOW in Ubuntu: [HOWTO](http://ubuntuforums.org/showthread.php?t=579378)

---

### Post by Solais on 2008-09-16
> **karlr42 said:**
> I believe you can play WOW in Ubuntu: [HOWTO](http://ubuntuforums.org/showthread.php?t=579378)

Yeah thats what I said:), happy I can play wow ro and wc3, suprisingly way better than when i had xp, more fps:), but most new games need direct x which pisses me off :(, Devil May Cry 4, Halo 3, But I guess ill keep this pc as linux, is it true that there is no virus for linux what so ever? Ill just put xp on a laptop i wanna buy? Btw guys? what do you think of Toshiba laptops?

---

### Post by mike1234 on 2008-09-16
> **Solais said:**
> Lol

- Over 3k on pictures
- 16.8gb of music plus friends music 4-8 gb
- world of warcraft file 10-13 gb
- heroes season 1-2
- dexter series completely
- scrubs v7
- many windows programs setup i kept for future use

I want a 1 TB Hard drive :popcorn:
  I buy external USB hard drives to store "stuff" so as to not muck up my bootable hard drive.  

M.

---

### Post by Solais on 2008-09-16
> **mike1234 said:**
> I buy external USB hard drives to store "stuff" so as to not muck up my bootable hard drive.  

M.

Yeah that a Portable Hard Drive I mean lol, saw one with 1tb i was like omfg :shock:

---

### Post by Solais on 2008-09-16
Ok now I am off, night :)

---

