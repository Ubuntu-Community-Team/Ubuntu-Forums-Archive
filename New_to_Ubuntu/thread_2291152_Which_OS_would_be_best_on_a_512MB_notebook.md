---
title: "Which OS would be best on a 512MB notebook?"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by TrustTheGeneGenie on 2015-08-18
Hi there,
I've never used Linux before (although I did use Unix a little at uni), and I'd like to start by installing a version of Ubuntu on my Samsung N220 Notebook.

1.66GHz single-core processor, 512mb RAM.

ATM it is running Windows 7 Starter.

I never really used it is with the Windows 7 starter it came with, and it is gathering dust.  What I would like to do with it now is use it for word processing, some web browsing, checking emails etc, and to get to know my way about a Linux operating system a bit before I take the plunge on anything more valuable! It does not have a CD drive, so I'll have to install from USB, I think. (USB 2.0 port) There is nothing on the device that I need to keep, and I don't need to do a dual install.  

What OS do you recommend? 

Many thanks!

---

### Post by flaymond on 2015-08-18
Lubuntu - [http://lubuntu.net/](http://lubuntu.net/) from the Ubuntu family might be your choice, or smaller one like ToriOS - [http://torios.net/more-about/](http://torios.net/more-about/),  TinyCore - [http://tinycorelinux.net/](http://tinycorelinux.net/), or Puppy Linux - [http://www.puppylinux.com](http://www.puppylinux.com) .

---

### Post by howefield on 2015-08-18
Lubuntu would certainly be the lightest of the Ubuntu set of flavours. 

Easy enough to download a few different distros and test them out from a USB stick to give you an idea of how it will work out.

---

### Post by ajgreeny on 2015-08-18
I would start with the mini.iso from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and install a command-line system and then add the **lubuntu-core** package to get a minimal lubuntu system. Then you can add whatever application packages you want and need, and it should run very well for such a limited machine.

Trying to install lubuntu graphically with only 512MB ram (I assume you did mean MB not KB?) may be a very slow and halting procedure but using the mini-iso will be fast and flexible.

---

### Post by TrustTheGeneGenie on 2015-08-18
Lol, yes, I did mean MB.  I've been missing my Amigas lately, and my teenage years!

---

### Post by TrustTheGeneGenie on 2015-08-18
Should I use a 32-bit mini.iso?

---

### Post by howefield on 2015-08-18
> **TrustTheGeneGenie said:**
> Should I use a 32-bit mini.iso?

Unsure if your notebook would even run a 64 bit system, but even if it does you would probably be best with the 32 bit given it will use less of your all to tight memory.

---

### Post by TrustTheGeneGenie on 2015-08-18
Ok, I downloaded 32 bit vivid vervet from [here]("https://help.ubuntu.com/community/Installation/MinimalCD"): 
and also unetbootin to put it on a USB drive. 
I found a list of Lubuntu Core packages for Vivid Vervet [here]("http://packages.ubuntu.com/vivid/i386/lubuntu-core/download") but how do I know which one to use? I'm in the UK.

---

### Post by verymadpip on 2015-08-18
Hi there.
This is old, but still quite helpful I think:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
Be sure to read it through, as your install will differ slightly from this example.
You'll install your lubuntu-core packages after the base command line install is done.

I recently did a 14.04 mini.iso install plus LXQt desktop & I had to do mine with a wired connection.  Wireless worked fine during the base install, but the connection was down when I rebooted & I made a mess of getting it working.  I started from scratch & once I had my desktop up & running with a network manager wireless wasn't a problem.  With any luck you may not have that issue, but using a wired connection might be wise.
 
Good luck

---

### Post by TrustTheGeneGenie on 2015-08-18
Thank you, that link is very helpful.  I know there is an ethernet cable here somewhere, haven't seen it for a couple of years though! :-)

---

### Post by verymadpip on 2015-08-18
Haha.
They're handy things to have around.
I prefer a wired connection, but wireless is spectacularly convenient.
Do keep us up to date on how you get on.

---

### Post by oldos2er on 2015-08-18
Changed thread title.

---

### Post by oldrocker99 on 2015-08-18
> **TrustTheGeneGenie said:**
> Lol, yes, I did mean MB.  I've been missing my Amigas lately, and my teenage years!

Ah, the Amiga. Maximum PC, in their first issue back in 2000 or so, said "Everyone who is cool either programmed or owned an Amiga."

I started using an Amiga in 1986, and stopped using one in 1996. I wandered in the world of Windows viruses:oops: until 2008, when I finally got smart and installed 8.04, Hardy Heron\\:D/. I was reminded of the Amiga OS immediately and pleasurably. When Amiga OS was hammered together in '84-'85, there weren't a lot of other OSes to emulate. They created an OS which had similarities to a cut-down UNIX. And UNIX is, via the superior GNU, run by the Linux kernel, **is** UNIX. Only better.

These days, everyone who is cool either programs or uses Linux;).

I will add that, among the lightweight versions of Ubuntu, Ubuntu MATE is just about as lightweight, and is fast and configurable. It's my desktop of choice, and it's worth it to check out.

---

### Post by Mike_Walsh on 2015-08-19
I would concur with InterProg on this one; Puppy Linux, without a shadow of doubt. The entire .iso for the current 'flagship', Tahrpup 6.03 (which is based on 'Trusty' anyway.....hence the name) is about 200 MB, total. I've been using it for about nine months, since its release in November last year. 

If you're dead set on using one of the 'buntus, I would recommend what AJ does; the mini .iso. That way, you can add what you need, up to the point where you've got the setup you want.

Tahrpup can be run entirely from a flashdrive; this has always been one of 'Puppy's' strengths, in that you can have one OS installed on your hard drive/SSD/whatever, and run another OS which will not interfere with the 'main' one. If you're interested, you can get it from here:-

[http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/)

As your N450 Atom **does** support Physical Address Extensions (PAE: the ability to address more than 4 GB of RAM.....though a moot point with your Samsung!), you'll want the 4th entry from the bottom; tahr-6.02_PAE.iso. The 6.03 'upgrade' comes in the form of a 'service pack', offered the first time you open the package manager. Burn to disk, and boot from the resulting 'LiveCD' in the usual way.

Hope that gives you an alternative; you can always run both the Ubuntu mini.iso version **and** Puppy (from a USB), alongside each other. Lots of options, and **plenty** to 'play with'!


Regards,

Mike. ;)

---

### Post by night_sky2 on 2015-08-19
I would add a chip of RAM in that machine and make it to at least 1GB if you can. That would give you a decent computing experience with Lubuntu.

Ebay is a great place to get all sorts of RAM chips at reasonable prices. And the computer is not that old if it came with W7 Starter so I think you would benefit from that.

---

### Post by brian-mccumber on 2015-08-19
Zorin Lite is another good alternative for older hardware and it's made  to resemble Windows. I had it installed on this computer but it was  Zorin 4, so I upgraded to Ubuntu Trusty Tahr. But the link goes to the newest  version of Zorin Lite.

[http://zorin-os.com/download9.html](http://zorin-os.com/download9.html)

---

### Post by ajgreeny on 2015-08-20
Hi brian-mccumber.

Don't worry about all those duplicates; the forum sometimes takes on a mind of its own and if it delays when you click the reply button, a second click will make duplicates, just the way it did for you.

I have removed all the unnecessary duplicates and left the information you added in just one post.

---

### Post by NM5TF on 2015-08-21
I put Ubuntu 14.04.2 LTS MATE on my Wife's Dell laptop with similar spec's as yours....

runs OK with only 512MB, but 1 Gb would be better....

YMMV of course....

tommy

---

### Post by Bucky Ball on 2015-08-21
When you have the ethernet cable plugged in, start the mini.iso install. You will reach a 'tasksel' screen eventually which allows you to select a profile for the machine. Choose the Lubuntu-core profile and it will download and install the correct one, you don't need to 'know' which one to download or download it prior to the install. :)

Here's a couple more links that might help you along:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Apologies if either of these is a duplicate of the one given previously. Good luck.

---

### Post by crashnburn_in on 2015-08-24
> **Bucky Ball said:**
> When you have the ethernet cable plugged in, start the mini.iso install. You will reach a 'tasksel' screen eventually which allows you to select a profile for the machine. Choose the Lubuntu-core profile and it will download and install the correct one, you don't need to 'know' which one to download or download it prior to the install. :)

Here's a couple more links that might help you along:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Apologies if either of these is a duplicate of the one given previously. Good luck.

Interesting. I might want to try this out as well. Thanks.

---

### Post by brad-bogar on 2015-08-25
As another option, I really like the LXLE (another version of Lubuntu) it is just as usable on a low end system and its GUI design is just beautiful. Check it out! [http://lxle.net/](http://lxle.net/)

---

