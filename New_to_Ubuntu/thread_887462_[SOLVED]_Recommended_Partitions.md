---
title: "[SOLVED] Recommended Partitions?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Captain_Carisma on 2008-08-12
Hi All,

First post, so go easy (and apologies if this is a bit of a no-brainer)!

I've been playing with Ubuntu on & off for a little while now, & have gone through a few test installs, both stand alone & dual-boot with XP, so I'm fairly confident on how to install.

I've just purchased a 250GB HDD for my PC, and I'd like some ideas on a partition scheme to use.

I've already created a (approx) 40GB partition for Windoze (Hitachi Deskstar, so reads at about 238GB availiable space), leaving approx 200GB free for Ubuntu/anything else that needs to go on.

I was planning on creating the following:

20GB /
20GB /Home
2 GB Swap
Whatever's left /Usr

Would you say that this should be OK, or could you recommend an alternative? I've had a look through other posts regarding partitions, but I just thought I'd ask for a second opinion

PC Specs as follows:
Intel P4 1.8 GHz, 1GB SDRAM, NVIDIA FX5200.

Thanks in advance.

Martin

---

### Post by billgoldberg on 2008-08-12
> **Captain_Carisma said:**
> Hi All,

First post, so go easy (and apologies if this is a bit of a no-brainer)!

I've been playing with Ubuntu on & off for a little while now, & have gone through a few test installs, both stand alone & dual-boot with XP, so I'm fairly confident on how to install.

I've just purchased a 250GB HDD for my PC, and I'd like some ideas on a partition scheme to use.

I've already created a (approx) 40GB partition for Windoze (Hitachi Deskstar, so reads at about 238GB availiable space), leaving approx 200GB free for Ubuntu/anything else that needs to go on.

I was planning on creating the following:

20GB /
20GB /Home
2 GB Swap
Whatever's left /Usr

Would you say that this should be OK, or could you recommend an alternative? I've had a look through other posts regarding partitions, but I just thought I'd ask for a second opinion

PC Specs as follows:
Intel P4 1.8 GHz, 1GB SDRAM, NVIDIA FX5200.

Thanks in advance.

Martin

/ 10gb or 20gb.
/swap 2gb
/home the rest 

All your documents, videos, music should go in /home, not in /usr.

Also note that /usr isn't the same as /Usr and /home isn't the same as /Home. Meaning everything is case sensitive.

There is no /Usr or /Home directory by default.

---

### Post by Captain_Carisma on 2008-08-12
Whoops, my apologies!

Got /usr & /home mixed up. Also didn't realise that they were case sensitive!

Should've read:

20GB /
20GB /usr
2GB Swap
Whatevers Left /Home

I've deliberately added the /usr partition as from reading through several other posts I've seen this configuration recommended, as (and correct me if I'm wrong) this is where all your settings ect are stored, so in the event of something going disasterously wrong, you can do a re-install & keep your settings?

---

### Post by Riffer on 2008-08-12
I would have another partition (maybe as a fat32) for storing things that you "really" want to save.  Its a bit old fashioned but a tried a true method for preserving data.

---

### Post by Captain_Carisma on 2008-08-13
Thanks for the suggestions.

I'll have another look later on, but I'll probably go with an extra FAT32 partition as a data store.

---

### Post by starcannon on 2008-08-13
most user settings like what wallpaper you have, how your panels look, playlists, last document opened, last command used in terminal, etc.. etc.. are stored in /home. I've been using linux exclusively for the last 5+ years, I always create a /home partition, but never created a /usr partion. I did try a seperate /opt partition, but found I never really needed it, so I gparted it and reabsorbed it into /.

Anyway
10~20 gb for /
>=installed RAM for swap
rest to /home

That is a very good, simple, and friendly scheme. In the end its all about choice though, so use what works best for you.

P.S. yeah a fat32 partition isn't a bad idea for passing files back and forth, though with stable NTFS support now in linux, its not a big deal anymore.

---

### Post by HotShotDJ on 2008-08-13
> **Captain_Carisma said:**
> I've deliberately added the /usr partition as from reading through several other posts I've seen this configuration recommended, as (and correct me if I'm wrong) this is where all your settings ect are stored, so in the event of something going disasterously wrong, you can do a re-install & keep your settings?No.[QUOTE="Linux Filesystem Hierarchy"]/usr is the second major section of the filesystem. /usr is shareable, read-only data. That means that /usr should be shareable between various FHS-compliant hosts and must not be written to. Any information that is host-specific or varies with time is stored elsewhere.[/QUOTE]SOURCE: [Filesystem Hierarchy Standard Group]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

Settings are stored in either /etc (system wide) or in /home/username. A separate /etc partition is NOT recommended.  Having a separate /home partition should be sufficient to keep your customized settings safe in most cases.

For the typical home system, you only need three partitions.... / (15 to 20 gig), SWAP (RAM X 2 for 1 gig or less system RAM; RAM X 1.5 for > 1 gig system RAM), /home (all remaining space).

Servers may have specialized needs and will need other partitioning schemes.

---

