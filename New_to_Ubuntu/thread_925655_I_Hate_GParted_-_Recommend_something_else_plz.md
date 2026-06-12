---
title: "I Hate GParted - Recommend something else plz"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-20
K i officially hate gparted now. it screwed up my HDD.

remember this post : [http://ubuntuforums.org/showthread.php?t=921700](http://ubuntuforums.org/showthread.php?t=921700)

i partitioned that HDD with GParted and got the error "disc error"

and after that windows could not detect my HDD.

I thought that my HDD died but today i partioned my desktop with the same disc of GParted and got the same error.

I HATE GParted.


Is there any better partitioner than GParted?

better to be freeware or opensource

---

### Post by Dr Small on 2008-09-20
I have never had problems out of gparted.

---

### Post by Sef on 2008-09-20
1) Have you tried downloading GParted from its site?   

2) They all work about the same.  Check the repos for qtparted.  

3) Could be a problem with your hard drive, the CD, the burn, etc.  Don't just assume it is GParted.

---

### Post by infinitejones on 2008-09-20
It might not necessarily by gparted's fault, but if you do want to try something else, I discovered [PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php") a few weeks ago and it's brilliant. It's a small Linux distribution on a LiveCD image - with a bit of googling I put it onto a bootable 1GB USB disk and it works like a dream!

---

### Post by Pascal11110 on 2008-09-20
I have never had any problems with gparted either, all there is a risk of that happening with any partitioner. If that happened using the same disk on both hard drives, it could be something wrong with the disk. I work at a computer store and use gparted 20+ times a day and have never had any problems. If this has happened to you twice using different disks then either you are doing something wrong (which I don't think would happen because it is pretty straightforward) or you are the unluckiest person in the world and got two bad disks (maybe a bad burner) or you suffer from getting two bad hard drives (at the store once we ordered 50 used 40 gig hard drives and 38 had bad sectors) I know none of this will probably help, but I thought you should hear my two cents.

********************************************************
Remember to thank good posts!

---

### Post by kansasnoob on 2008-09-20
I use Gparted a lot, now I seldom use Gparted to resize a Vista partition because Vista has it's own tools, but I have no problems unless I goof!

Be really specific about what you're doing. What partitioning process failed?

---

### Post by starcannon on 2008-09-20
I use gparted regularly, never had any problems. Perhaps time to do a little troubleshooting?

---

### Post by mc4100 on 2008-09-20
The only other program I know is good is PartionMagic, but you might not want that for obvious reasons.

---

### Post by rzrgenesys187 on 2008-09-20
I have never had a problem with gParted.  Nowadays I usually do hard drive partitioning using fdisk and mkfs since it's faster to load a livecd without a graphical environment.

---

### Post by Harisz750 on 2008-09-21
download hiren's boot cd 9.4 and boot from this. it has many grafical partition programs and not only!

---

### Post by MasterNetra on 2008-09-21
Could always use the Gnome Partition Editor! :p

---

### Post by phidia on 2008-09-21
To oppose the majority opinion, gparted can be slow and somewhat unresponsive. That probably depends on your cpu clock speed and amount or ram though.

I always use cfdisk it's fast and works well. You can open cfdisk from the terminal and access the man page there as well > sudo cfdisk /dev/hdx x=the actual drive letter and depending on the drive type you may want to use sdx.

---

### Post by twitch2197 on 2008-09-21
like others have said... it's not necessarily gparted. i've screwed up hard drives with the windows vista partitioning utility, gparted, and partitionmagic.
guess it all boils down to "can you use it safely?"
apparently i can't... 
no more dual booting for me

---

### Post by Gordy on 2008-09-21
try gparted using the command line "sudo gparted" enter you password and you will find it works better...

---

### Post by Dr Small on 2008-09-21
> **phidia said:**
> To oppose the majority opinion, gparted can be slow and somewhat unresponsive. That probably depends on your cpu clock speed and amount or ram though.

I always use cfdisk it's fast and works well. You can open cfdisk from the terminal and access the man page there as well  x=the actual drive letter and depending on the drive type you may want to use sdx.
Thanks, I may end up using cfdisk from now on. :)

---

### Post by yragrelluf on 2008-09-21
A really good partition manager is Acronis Disc Director Suite. It is not open source, and I dont know how much it costed (gift from friend), but it works great. You can use it if it is installed in windows, but then you cant edit mounted partitions, but it comes with a step by step gui to guide you through the easy process of making a bootable Acronis that runs from itself and is a very powerful tool. Go online and try the trial version, see if you like it!

---

