---
title: "64 bit Processor Distributions"
date: 2007-10-06
forum: Other OS Talk
---

### Post by Last.Karrde on 2007-10-06
Im about to purchase a new AMD X-2 64 bit chip and im wondering what distros have really good 64 bit support. Ive googled and read here that there are some problems with flash and a few other things but i think ill be right.

So yeah.. What distros have good 64bit support?

Thanks!

---

### Post by fumduck on 2007-10-06
ubuntu 64 worked easy with me..

---

### Post by Pancetilla on 2007-10-06
Hi, AMD X2 3800 here

Flash can be fixed with two or three different workarounds in most 64 bits distros, but Sabayon 64 bits has it working from the start.

Debian/ubuntu would be my choice, I've got flash working with nspluginwrapper, but if you don't want to mess with it, try Sabayon (gentoo based)

---

### Post by Last.Karrde on 2007-10-06
Thanks for the quick reply, is Sabayon like Linux Mint, except a gentoo/64 bit version?

---

### Post by Pancetilla on 2007-10-06
> **Last.Karrde said:**
> Thanks for the quick reply, is Sabayon like Linux Mint, except a gentoo/64 bit version?

Sorry, I'm not familiar with Linux Mint. But I heard that Mint is Ubuntu with some adittional software+plugins+goodies in it, so in that sense the answer might be yes.

---

### Post by mips on 2007-10-06
> **Last.Karrde said:**
> Thanks for the quick reply, is Sabayon like Linux Mint, except a gentoo/64 bit version?

Sabayon x86-64 has everything installed by default, codecs, flash, java, dvd, ati, nvidia etc so it could be compared to mint if you want to put it that way. You don't have to worry about installing extra stuff in order to get things working like in ubuntu  for example.

Yes, it's based on gentoo.

---

### Post by fistfullofroses on 2007-10-06
In all honesty, besides Gentoo, I think that Slamd64 and Ubuntu are the only good 64bit distributions around.

I could be wrong, but I have tried quite a few distributions and those three are the only ones that worked well out-of-box. I personally gave up on finding a good 64bit system, and I am using 32bit. Slackware.

:::EDIT:::
Mostly it is just a lack of 64bit software. Slamd64 and Ubuntu had the largest amount of 64bit software, and as such were favored by me.

---

### Post by rsambuca on 2007-10-06
Basically all of the main distros nowadays have pretty decent 64bit support.  If you are looking for 64bit specific distros, you might try [bluewhite64linux]("http://www.bluewhite64.com/news.php"), or [64Studio]("http://64studio.com/"), in addition to the ones already mentioned.

---

### Post by D-EJ915 on 2007-10-06
If you *only* want to use 64 bit software you could give Arch a whack as theirs doesn't include 32 bit compatability.

---

### Post by rsambuca on 2007-10-06
> **D-EJ915 said:**
> If you *only* want to use 64 bit software you could give Arch a whack as theirs doesn't include 32 bit compatability.

I could be mistaken, but doesn't arch have i686 as well?

---

### Post by fwojciec on 2007-10-06
Arch64 is pure 64bit by default, though multi-lib can be installed either as lib32 packages or in the form of a 32bit chroot (both methods are unsupported though).  There is also a separate 32 bit (i686) version or Arch available, of course.  

If the OP wants a 64bit distro that supports things such as Flash/Skype out of the box then Arch is definitely *not* a good choice - most other distros will be better suited since they will have some multi-lib support installed by default.  It can be kind of fun, however, to run a pure 64bit system... it does require some flexibility in terms of software choices, but it is actually possible to have a full featured desktop environment in pure 64bit these days.

By the way - there are actually very few tangible benefits of running a 64bit system at the moment, it's mostly art for the sake of art at this stage, IMO.

---

### Post by rsambuca on 2007-10-06
> **fwojciec said:**
> By the way - there are actually very few tangible benefits of running a 64bit system at the moment, it's mostly art for the sake of art at this stage, IMO.

Why don't you back-up your entire DVD collection and then try to convince me there isn't a difference.  It can be quite substantial, in fact.

---

### Post by fwojciec on 2007-10-06
> **rsambuca said:**
> Why don't you back-up your entire DVD collection and then try to convince me there isn't a difference.  It can be quite substantial, in fact.

I'm not saying that there isn't difference, I'm saying there are very few tangible benefits - and encoding video might be one of them - I wouldn't go as far as saying that the difference is substantial though.  I'm actually running a 64bit system at the moment, so it's not like I'm trying to justify something here, btw...  And I certainly don't want to start a flame war over this, it's just my opinion :)

---

### Post by the.dark.lord on 2007-10-07
> **Pancetilla said:**
> Hi, AMD X2 3800 here

Flash can be fixed with two or three different workarounds in most 64 bits distros, but Sabayon 64 bits has it working from the start.

Debian/ubuntu would be my choice, I've got flash working with nspluginwrapper, but if you don't want to mess with it, try Sabayon (gentoo based)

Option for flash support will be included by default in Ubuntu 64 bit from Gutsy.

---

### Post by rsambuca on 2007-10-07
> **fwojciec said:**
> I'm not saying that there isn't difference, I'm saying there are very few tangible benefits - and encoding video [COLOR="Red"]might[/COLOR] be one of themYou obviously don't believe me.  Please test it yourself before saying there are no benefits.

> **fwojciec said:**
> I wouldn't go as far as saying that the difference is substantial though.  Is a 35% increase in performance not substantial to you?  In order to gain that much performance through hardware purchases, you would have to spend approx 50% more in cpu, etc.  Why not save that cost and use the 64bit encoded programs?

---

### Post by fwojciec on 2007-10-07
I have no reason not to believe you, and I think you do bring up a valid point - I was, perhaps somewhat carelessly, using "substantial" more generally, and not specifically in reference to video encoding - something I don't have much experience with.  Let's agree then that encoding video is one of the "few tangible benefits" that do exist.

---

### Post by rsambuca on 2007-10-07
I am afraid I don't agree with your use of the word "few" for the amount of tangible benefits.  There are many different areas where the use of 64bit encoded programs will bring performance increases.  Just because you only use a "few" of them doesn't mean that is all that exists.

---

### Post by fwojciec on 2007-10-07
Man... nothing satisfies you, and here I was trying to appease for the sake on not making this thread go off topic...  

I actually run a 32bit system and a 64bit system in parallel, on the same hardware, using exactly the same software and configurations, so I have some actual basis for what I had said was the case "in my opinion."  

It is true that I don't encode video, but otherwise my desktop is full featured and I use it for a range of things which, I believe, are fairly typical (text editing, internet, music playback and management, watching movies, compiling stuff, etc.)  I see no substantial differences between the 32bit version and the 64bit version in regular everyday use: there are differences, of course, for example the 64bit version, on average, uses more memory for the same apps, and requires slightly more maintenance and care, but that's about it as far as I can tell - I wouldn't call these differences substantial in either case, the systems are strikingly similar.

I think it's a valid point to make and something for the OP to consider, that's all.  What are some other areas where there are tangible benefits to using 64bit systems?  I am willing to learn, as you have seen, I am capable of revising my opinion when evidence is presented to me.  I think it would be useful to be as specific as possible about the benefits of 64bit systems, that way the OP would be able to make a more informed decision about whether 64bit system is something that might have some benefits for him specifically.

---

### Post by rsambuca on 2007-10-07
I think for the most part we agree on the basics - that there is little difference in the setup and maintenance between the two.  I guess where we disagree is that you seem to think "why bother?", whereas I think, "why not?".  

At least if you do install the 64bit system, the ***potential ***is there in certain applications for  performance gains, whether the operator uses them or not.  If you install the 32bit system, then in these cases you are hampering your system.

---

### Post by fwojciec on 2007-10-07
Well, except we can tell in what areas those benefit can be actually expected, since they only appear when programs are specifically coded to take advantage of 64bit architecture.  This is why I thought it would be useful to be as specific as possible about where those benefits can be expected, since the vast majority of programs are not specifically coded to take advantage of 64bits.

---

### Post by dptxp on 2007-10-08
This is a switchover time from 32 bit to 64 bit, within next one year there will be hardly anything that does not run well with 64 bit and in next 2 years all software shall be developed in 64 bit. 32 bit OS has limited lifetime, say 3 to 5 years.

In most of the programs you will just not see any difference, take a text editor for instance. It was as fast in 16 bit. But take a very large file, matters become different.

Audio/Video editing, photo editing, long mathematical algorithms etc all will surely show a significant increase in speed.

I use both, 64 bit on laptop - have found all my programs I needed in 64 bit. What is it that you can not run in 64 bit.

I use 32 bit on desktop though it has a 32 bit CPU just because it has low RAM (256 MB), and 64 bit needs a bit of more RAM.

If anyone wants to stick to 32 bit, it is a personal choice. It is true that not all 64 bit programs are optimized for 64 bit.

---

### Post by Last.Karrde on 2007-10-08
> I use both, 64 bit on laptop - have found all my programs I needed in 64 bit. What is it that you can not run in 64 bit.


What distros do you run?

---

### Post by misfitpierce on 2007-10-08
Ubuntu 64 is fast and does me wonders... :)

---

### Post by darksong on 2007-10-08
Ubuntu x64 worked well for me after the install (ordinary disk did not work for me) same as x32 but a bit quicker.

Opensuse works well out of the box

Sabayon work well out the box.

---

### Post by Last.Karrde on 2007-10-08
Yeah, im juggled up between Sabayon and Ubuntu 64. Mayby Gutsy will provide better 64 bit support?

---

### Post by dptxp on 2007-10-09
> **Last.Karrde said:**
> What distros do you run?

ubuntu.

i want to stick to a main-stream distro.
a distro that i expect to see after 10 years.

---

### Post by Anubis on 2007-11-21
I've been 64bit Ubuntu from the start.

---

### Post by wolfen69 on 2007-11-21
my vote goes to ubuntu 64.

---

### Post by SunnyRabbiera on 2007-11-21
well some people have been able to use the x86 versions on their 64 computers and say they work better for certain things...
64 bit specific stuff I heard is a pretty hard buy from what I have learned

---

