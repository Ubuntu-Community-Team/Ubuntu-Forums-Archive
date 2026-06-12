---
title: "HOWTO:Faster network file transfers"
date: 2006-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ashrack on 2006-02-12
I was really pissed at UBUNTU since my network throughput was at max 3MB/s with a 100Mb FULL DUPLEX NIC when copying a file from a Win2k3 SERVER computer.
So I mounted my network shares using CIFS and not SMBFS and my speed has doubled!!!

First install the CIFS support:
```
sudo apt-get install smbfs
```
Then mount it:
```
mount -t cifs //network/share /media/networkshare
```
If U want the share to be mounted at every reboot than write the following into /etc/fstab:
```
//server/d	/media/d		cifs		username=username,passwords=password,user					0	0
```
Note that this will only give U read support.

But if U want full read/write access for all users on your CIFS share as well as it to be case insensitive so U wont have problems with Windows using Upper or Lower case replace the above line with the following line in /etc/fstab. :
```
//192.168.0.1/d /media/d	cifs credentials=/root/.smbserver,noperm,nocase,file_mode=0777,dir_mode=0777	0	 0
```

For those wanting to contact their computers by their names instead of IPs check out this great guide:
[http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios](http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios)

---

### Post by Ahriman on 2006-02-13
Works like a charm. Cheers man.

One question: what should the fstab entry look like if I were to stick this into it? I'm just not 100% sure where the cifs parts goes, etc. And while I could write a file that would run the command every boot, it would be a little tidier if it were in the /etc/fstab

---

### Post by ashrack on 2006-02-13
[QUOTE=Ahriman]Works like a charm. Cheers man.

One question: what should the fstab entry look like if I were to stick this into it? I'm just not 100% sure where the cifs parts goes, etc. And while I could write a file that would run the command every boot, it would be a little tidier if it were in the /etc/fstab[/QUOTE]
I have updated the first post so it now reflects the FSTAB.
I knew I forgot to add something when I was writting this howto:rolleyes:
btw. I fail to see the reason for the guides still suggesting the use of SMBFS which is clearly slower than CIFS

---

### Post by voger on 2006-02-13
Hi i have a problem when i try to mount it with fstab

mount error: could not find target server. TCP name blackbox/shared not found  rc = -1074562682
No ip address specified and hostname not found

my fstab line is
//blackbox/shared  /mnt/blackbox_share     cifs    rw,user,auto,iocharset=utf8,username=xxxx,password=xxxxx 0 0

When i give an actual IP adress then it works ok. How can i fix that?

---

### Post by george_apan on 2006-02-14
Are there any side-effects to using CIFS instead of SMBFS?

---

### Post by jstueve on 2006-02-14
> When i give an actual IP adress then it works ok. How can i fix that?put the actual ip for blackbox in your /etc/hosts file.

---

### Post by ashrack on 2006-02-15
[QUOTE=george_apan]Are there any side-effects to using CIFS instead of SMBFS?[/QUOTE]
as far as I know none. Have set it up on 2my computers thus far and have seen no side-effects yet. But on the other hand I've only been using it for a week or so.

---

### Post by ashrack on 2006-02-15
[QUOTE=voger]Hi i have a problem when i try to mount it with fstab

mount error: could not find target server. TCP name blackbox/shared not found  rc = -1074562682
No ip address specified and hostname not found

my fstab line is
//blackbox/shared  /mnt/blackbox_share     cifs    rw,user,auto,iocharset=utf8,username=xxxx,password=xxxxx 0 0

When i give an actual IP adress then it works ok. How can i fix that?[/QUOTE]
This should fix your problems:
[http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios](http://ubuntuforums.org/showthread.php?t=88206&highlight=netbios)

also added it to the guide

---

### Post by goombah88 on 2006-02-15
i followed this guide but sadly i still only get at max 1.2 MB/s when xfer'ing files from my win xp "server" acting as my fileserver and my kubuntu laptop (wireless).  it's the same as when i was using samba.  any suggestions would be greatly appreciated.

---

### Post by voger on 2006-02-15
Thanks that worked. 

I only had a speed increase by 0.5M but i guess that is probably because my other machine is an old PII at 350MHz running WINXP. 

Thanks again :D

---

### Post by ashrack on 2006-02-15
[QUOTE=goombah88]i followed this guide but sadly i still only get at max 1.2 MB/s when xfer'ing files from my win xp "server" acting as my fileserver and my kubuntu laptop (wireless).  it's the same as when i was using samba.  any suggestions would be greatly appreciated.[/QUOTE]
On you laptop do U have Windows installed, if U do try it with them to see if its not a problem of wireless or anything similar.And report back then

---

### Post by ashrack on 2006-07-09
This will give U full write access for all users on your CIFS share as well as it will be case insensitive. So U wont have problems with Windows using Upper or Lower case:
```
//192.168.0.1/d /media/d	cifs credentials=/root/.smbserver,noperm,nocase,file_mode=0777,dir_mode=0777	0	 0
```

---

### Post by RawMustard on 2006-07-09
It's a bit quicker, but not double for me :(  I guess the communication between linux and windows is still not there,(Note I know this is not linux's fault) transfers between windows and windows is much much faster for me :(  Transfers between linux and linux is just as fast.

---

### Post by ashrack on 2006-07-09
4M using cifs transfers between LINUX-WINDOWS or LINUX-LINUX is about the same speed. 
But when I used SMBFS it was terrible.

---

### Post by MetalMusicAddict on 2006-07-10
For some reason, for me, this hasnt helped my LINUX-LINUX transfers at all. In fact its made 'em worse.

Heres what happening for me.

I have a server. nForce2 chipset with gigabit NIC onboard. I have a desktop. From windows I can move a 1.5 gig file in 2 mins. Maybe less. In Ubuntu from the same drive to the same server over the same hardware its about 6 mins. I have no clue as to test the connection/transfer speed. I actually have 2 gigabit NICs. 1 a SMC and the other a Linksys.

](*,)

---

### Post by Jason_25 on 2006-07-10
> **MetalMusicAddict said:**
> For some reason, for me, this hasnt helped my LINUX-LINUX transfers at all. In fact its made 'em worse.

Try using NFS instead.

---

### Post by MetalMusicAddict on 2006-07-10
Will using NFS mess with CUPS? I believe CUPS and SAMBA work together somehow. I guess as long as the configs are there and SAMBA and CUPS still run in the background it will work.

---

### Post by fragos on 2006-07-10
> **goombah88 said:**
> i followed this guide but sadly i still only get at max 1.2 MB/s when xfer'ing files from my win xp "server" acting as my fileserver and my kubuntu laptop (wireless).  it's the same as when i was using samba.  any suggestions would be greatly appreciated.

Given there is no diffference spead that others have reported, perhaps the WinXP is slower than what you'd tried on the Linux side.

---

### Post by deadfolk on 2006-07-16
Hi all,

I'm a total Linux noob, and could really use some further explanation on this, if anyone could spare the time.

There are two fstab entries mentioned in the original post.  Do I need both?

And what do the entries mean?  For example, 
> //192.168.0.1/d /media/d	cifs credentials=/root/.smbserver,noperm,nocase,file_mode=0777,dir_mode=0777	0	 0

What do //192.168.0.1/d and /media/d refer to?  Why the ip address - isn't the share on the local machine?  Have I missed the point entirely?:-k 

In my case, I have a Samba share called 'music' which sits at /media/sdc1/music.  How would I apply this?  btw, I am accessing all my share from a WinXP Laptop.

Thanks for any info,

DF

---

### Post by ashrack on 2006-07-28
> **deadfolk said:**
> 
What do //192.168.0.1/d and /media/d refer to?  Why the ip address - isn't the share on the local machine?  Have I missed the point entirely?:-k 

In my case, I have a Samba share called 'music' which sits at /media/sdc1/music.  How would I apply this?  btw, I am accessing all my share from a WinXP Laptop.

Was on vacation. Please recheck the OP since I have edited it.
And for the IP address it depends whether the other machine is broadcasting its DNS name or not!

---

### Post by whoscheesemine on 2008-03-15
When I entered command:

```
mount -t cifs //network/share /media/networkshare
```

I got this:

```

mount error: could not find target server. TCP name network/share not found
No ip address specified and hostname not found

```

---

### Post by ashrack on 2008-03-15
if you don't have Winbind installed then you have to connect through IP address and not DNS address

---

### Post by whoscheesemine on 2008-03-15
I hate to be a stooge.... but wha? could someone explain that to me a lil dummer?

---

### Post by ashrack on 2008-03-16
sorry for not replying sonner had been busy.
Anyway here's some WIKI info about IP address:
[http://en.wikipedia.org/wiki/IP_address](http://en.wikipedia.org/wiki/IP_address)
Every computer has a unique IP address. But since IP address are harder to remember then DNS names we use names.
You can try it by doing this in a terminal:
```
ping www.google.com
```
and you will see that the address 'www.google.com' translates into its IP number.

So try to ping the other computer by its IP number

---

### Post by Xyphoid on 2009-05-14
Hya,

How do I get my folder to automount on boot?
I tried the option auto and _netdev, but it still won't automount on boot.
If I mount manually with mount -a, then fstab works fine.

Never mind.
All my problems (including webcam that wasn't working) were because I burned an Ubuntu CD with a faulty DVD burner. Which caused Ubuntu to not install correctly. It took me three days (and two nights. I'm soooooo tired, but so happy everything is working now :P) to figure that out.

---

