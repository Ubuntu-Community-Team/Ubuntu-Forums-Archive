---
title: "burning DVDs (data only)"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by poldie on 2008-11-09
I want to write some digital photos and other data to disk. I've tried Brasero, but it doesn't verify - I get an error.  I've reported this, but not received a response yet (I've reported another error which has been acknowledged and will presumably be fixed at some point, but sadly that's an unimportant error).

I searched this forum and someone suggested K3B.  I'm trying that now but unless the verify stage takes 30 mins it too doesn't work properly.

Can someone suggest a DVD writing app which actually works?

---

### Post by bttb on 2008-11-09
Hi,

I had issues with the default Hardy brasero as well, but as far as I'm concerned the updated version in the Hardy backports repo works far.

---

### Post by dracayr on 2008-11-09
ubuntu has one installed by default: Places&#8594;CD/DVD creator

dracayr

---

### Post by poldie on 2008-11-09
> **dracayr said:**
> ubuntu has one installed by default: Places&#8594;CD/DVD creator

dracayr

I don't really see an app there at all - how do I choose for the session to be closed, to enable verify, change burn speed etc? 

I've filed a bug report on k3b.  Seems there has been problems with verify in the past.  I had no problems burning disks using 8.4.1 so I'm not convinced I have a hardware problem.

Are there any other apps which are recommended?  Is there something to do to check that any Ubuntu components related to optical writing are installed correctly and up to date?

---

### Post by dark_harmonics on 2008-11-09
I loved Nero so much that i actually purchased the Linux version. Maybe it has what you want? Brassero or K3B really should have what you need though. I just really liked Nero's design from when i was a winblows user.

---

### Post by poldie on 2008-11-11
> **dark_harmonics said:**
> I loved Nero so much that i actually purchased the Linux version. Maybe it has what you want? Brassero or K3B really should have what you need though. I just really liked Nero's design from when i was a winblows user.

I despise Nero - I had nothing but problems with it, and I'm not going to pay for non-free software to simply write data to a dvd.  Nero under Windows always struck me as one of the buggier, popular Windows apps.

Is there a small tool which compares binary files under Ubuntu? I had a quick google but they all seem to be geared for comparing text files. I don't want to know what the differences are - just that there are differences.  Would just calculating an md5 hash for the two files and comparing them be good enough?

---

### Post by SamNSane on 2008-11-11
You're going to think I'm crazy, but I'm going to say this anyway:

The best burning application I've found for Linux is a Windows application. I have absolutely had it with brasero and k3b.

I sat here yesterday trying to use both of them to burn data to DVD. Brasero would kind of cooperate and then fail during verification. I was able to prove that the burn was successful and verify the files written by an alternate method, but why should I have to go through that? Brasero's error messages were about as unhelpful as they could be.

And then there's k3b, which spins up the DVD writers (tried with three different drives) and shows me the specs on the media in the right-hand pane while showing me "no media" in the the upper left-hand pane! Yeah, it was proving that it could read the media, and claiming that no media was inserted. You just have to love that.

What a pain, these panes.

So, I installed wine from the repository (I'm running 8.04 with backports enabled.), and then installed ImgBurn. ImgBurn was far and away my favorite burning app of all time on the Windows side. Guess what. It works under wine. Perfectly. And it burned my data DVDs faster than brasero. And the faster burn time included verification.

If you're not turned off by using wine and some Windows freeware, give ImgBurn a shot. ImgBurn has a somewhat unusual user interface, but it's the most highly configurable burner I've seen. It's also head and shoulders above anything else I've ever used for reliability. You'll have to deal with its Windows-centric idea of where the files are. (You'll see what I mean.) But it works.

The guy who writes it also has a pretty decent support forum, too.

---

### Post by dark_harmonics on 2008-11-11
> **poldie said:**
> I despise Nero - I had nothing but problems with it, and I'm not going to pay for non-free software to simply write data to a dvd.  Nero under Windows always struck me as one of the buggier, popular Windows apps.

Is there a small tool which compares binary files under Ubuntu? I had a quick google but they all seem to be geared for comparing text files. I don't want to know what the differences are - just that there are differences.  Would just calculating an md5 hash for the two files and comparing them be good enough?

Wow i have to say i've burned 3 times as many bad dvds with k3b and brassero than i ever did with nero. I dont like the newest versions for windows (too much fluff) but i love the cut-down interface. It just has everything i needed in one place. 

I've used brassero since it became an ubuntu standard, but i've had some trouble with it. 

For complicated burns i use nero linux (i like to support companies that provide linux solutions closed or open source) and for regular everyday type burning i use brassero. I no longer use k3b but it is a pretty nice app as well.

BTW i use imgburn as well because it allows you to define the separation point in the layers of a dual-layer disc.

---

### Post by SamNSane on 2008-11-12
I've used Roxio (and its blighted predecessors) and Nero on many systems over the years. I finally got so that they were the first thing I removed from anything that crossed my path. The bells and whistles versions are just downright awful, while the OEM versions are a bit less complex but just as likely to screw something up horribly. If you pay for Nero and download the simplest modules that you need, it can work pretty well.

But I've never seen any other burning software that topped ImgBurn for control and reliability. I can't remember any failures with it at all, and it simply doesn't affect the rest of a system that it's installed upon.

I'm just delighted to be able to use it under Linux.

Don't get me wrong. I'll continue to watch brasero to see if it will stop being cantankerous, and I'll be glad to use it when it becomes useful to me. I'd rather be using Open Source software, on a philosophical plane. But, on a practical plane, burning software really needs to just work and not give the user a bunch of lip.

---

