---
title: "FAQ: Does Ubuntu support ReiserFS?"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
Yes, you can select this when you first setup Ubuntu. You will need to manually edit the paritions to select this mode.

---

### Post by HungSquirrel on 2004-10-16
Does it/will it support Reiser4?  Just curious.

---

### Post by mindwarp on 2004-10-18
[quote=ubuntu-geek]Yes, you can select this when you first setup Ubuntu. You will need to manually edit the paritions to select this mode.[/quote]

What do we need to add to fstab etc?

---

### Post by atom on 2004-10-21
fstab is generated for you even if you choose reiser. :)

---

### Post by FLeiXiuS on 2004-10-22
ReiserFS is lightening fast!!

---

### Post by ohman on 2004-10-22
[quote=FLeiXiuS]ReiserFS is lightening fast!![/quote]
But not good for laptops due to constant disk spin.

---

### Post by jdong on 2004-10-24
Just in case some people didn't know, you can enhance performance of a reiserfs volume with options noatime and notail.


noatime prevents the fs from updating access times, and notail (err, not a rocket scientist) just makes the reiser volume faster!

As far as reiser4, I hope to see it worked on in hoary. In its current state (I use 2.6.9-cko and reiser4progs 1.0.2), I've still ran into a few random issues -- including corruption (fsck-fixable though), disappearing files (just a file, couldn't reproduce).


The repacker is seriously messed too, in direction=1, it's oops'ed on me multiple times.

---

### Post by neerolyte on 2007-03-22
> Yes, you can select this when you first setup Ubuntu. You will need to manually edit the paritions to select this mode.
Are the Kubuntu and Ubuntu installs really that different? I can't select reiserfs on my "kubuntu 6.10 desktop i386" CD. I even already had a reiserfs partition that was empty that I simply wanted to label without formatting, nup wouldn't let me.
> What do we need to add to fstab etc?
> fstab is generated for you even if you choose reiser. 
Sometimes you need the console way of doing things even if the GUI is awesome. E.g. I needed the fstab line because:
a) Kubuntu install **DOES NOT** support reiserfs by any method I can find.
b) I have been setting up a software raid array, post install. As far as I can find there is no decent GUI support for this either.

So maybe it would be a better idea to not just tell them why they don't need it but also tell them where they might look (just in case for some reason you can't see, they do need it).

Anyway rant over, here is the fstab line I used to mount a device /dev/md0 at mount point /media/ra using reiserfs:
```
/dev/md0        /media/ra       reiserfs        defaults,notail,noatime 0       0
```

---

### Post by sugarland2k on 2007-07-09
Yes, on install with manual disk partitioning as noted.  I use ReiserFS with my Kubuntu 7.04 system (160 GB HD) and it works great.  

Friends do not let friends run Vista !
Billy in Sugar Land :)

---

### Post by JMO707 on 2007-07-30
Got a problem. I recently reinstalled Feisty, and... well, I wanted to test ReiserFS with / partition.
The problem I find is that things doesnt update. You know, Nautilus need F5, and in Firefox the bookmarks need to be "tab-re-opened".

What can it be? =S

---

### Post by diskotek on 2007-09-26
i'm cuirous about reiserfs... 
in fact i first met with this file system when i'm trying to install "elive - gem"... but i2ll install it on my laptop and as mentioned here it's so great for laptops.. so... i'll try it little bit later :D

---

### Post by jonny_noog on 2007-10-03
Hello,

I'm trying to gather a bit of information on reiserfs and I have a couple of questions:

1. I note that user ohman in this thread states that reiserfs is not good for laptops due to constant disk spin. Why is this an issue and apparently a particular issue for laptops? Will the constant spin shorten the life of the hard drive or something?

2. If one has a reiserfs partition on a disk but it does not have either the notail or noatime options set in fstab, can one just edit fstab and add these options or do you have to reformat the partition to use these options?

Thanks for your time.

---

### Post by glaze on 2007-10-03
> **jonny_noog said:**
> Hello,

2. If one has a reiserfs partition on a disk but it does not have either the notail or noatime options set in fstab, can one just edit fstab and add these options or do you have to reformat the partition to use these options?


Yes, You can simply edit fstab.

---

### Post by Steveway on 2007-10-03
> 
1. I note that user ohman in this thread states that reiserfs is not good for laptops due to constant disk spin. Why is this an issue and apparently a particular issue for laptops? Will the constant spin shorten the life of the hard drive or something?
It will shorten your battery-life. So it's not good for Laptops.
And as another addition:
[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)

---

### Post by jonny_noog on 2007-10-03
Ah, OK thanks for the answers.

---

### Post by jeremy=awesome on 2008-12-05
could someone post a quick howto set up a ReiserFS HD(not as primary) through the bash?

---

### Post by FlemmingJ on 2010-01-06
> **jdong said:**
> Just in case some people didn't know, you can enhance performance of a reiserfs volume with options noatime and notail.


noatime prevents the fs from updating access times, and notail (err, not a rocket scientist) just makes the reiser volume faster!

As far as reiser4, I hope to see it worked on in hoary. In its current state (I use 2.6.9-cko and reiser4progs 1.0.2), I've still ran into a few random issues -- including corruption (fsck-fixable though), disappearing files (just a file, couldn't reproduce).


The repacker is seriously messed too, in direction=1, it's oops'ed on me multiple times.

Talking about ReiserFS:

Yesterdau I lost a reiser formatted 350G disk completely. It's neiter visible with df nor fdisk or blkid.
It has then spunned like a charme for nearly 2 years.
Any good guesses why, most welcome

regards Flemming

---

### Post by feistybill on 2010-02-04
> **jonny_noog said:**
> 1. I note that user ohman in this thread states that reiserfs is not good for laptops due to constant disk spin.

I was wondering about the same thing. I have used and benchmarked each and every linux filesystem and ReiserFS (not v4) with "noatime,nodiratime" has always been the fastest hands down. I must admit I have never noticed this "constant disk spin" issue, perhaps because of the noatime options.
So I was wondering if anyone else has experienced the problem jonny_noog was talking about?

---

