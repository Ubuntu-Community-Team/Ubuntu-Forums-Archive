---
title: "Linux distro recommendation for Windows users on old laptop"
date: 2007-12-31
forum: Other OS Talk
---

### Post by VCSkier on 2007-12-31
I have some friends that have an old laptop (purchased in 2000 or 2001) who have become very frustrated with Windows' performance on it.  I'd like to offer to install a Linux operating system on it for them, but I'm not sure what distribution would be intuitive and/or lightweight enough for them to use and be completely satisfied.

They aren't particularly computer savy, and have a young child, so don't have alot of time to learn the intricacies of a complicated operating system.

Here are the options and concerns that come to my mind:
Xubuntu (is it light enough)
Fluxbuntu (is it easy and stable enough)
Gebuntu (is it stable and light enough)
gOS (will it run on a laptop and is it stable enough)
MEPIS antiX (is it easy enough)

I have no personal experience with any of the distributions on this list with the exception of Xubuntu, and that brief experience was when the project was first officially adopted.  So any advice is greatly appreciated.

What on, or off, this list would you recommend?  Keep in mind, the laptop is 7 years old, and ease of usability for a Windows user is the first priority.  I will be able to install and setup the operating system for them but will not be there to administer or maintain it, they must be able to handle it on their own.  Thanks!

---

### Post by Herman on 2007-12-31
What are the machine's specs? Some older machines are still pretty good if they have enough RAM. It depends on what they're likely to want to use it for too.

I think Gnome (Ubuntu) is the simplest to use, but maybe that's only because I'm so used to it. 
There are some really great video tutorials you can download for them and give them to watch here,  [screencasts.ubuntu.com]("http://screencasts.ubuntu.com/").
If they watch some of those that should help them a lot. They're good for anybody, I learned a lot from them myself.

Often it's better when people don't have a lot of computer knowledge get the chance to learn Ubuntu first, because that way they don't learn a lot of wrong ways to do things that they need to 'unlearn' again. Some new users just take to Ubuntu like a duck to water. Actually, it's a lot easier. All they have to do is use it. There's not much to go wrong really.

Regards, Herman :)

---

### Post by Rumor on 2007-12-31
I've an older laptop as well. i don't know how old it is in terms of years, but it is a P2 / 233 with 64 megabytes of ram. It has no on-board LAN capability and I have not as yet bought a PC card for it to tie it into my home network. 

It is currently running Antix on it. Antix runs quite well. It was the only distro I tried that installed without any issues and gave me a very nice looking screen with crisp font rendering. It uses fluxbox and the menu is already set up. I am very happy with it, so I recommend you give it is a look.

[http://antix.mepis.com/index.php/Main_Page](http://antix.mepis.com/index.php/Main_Page)

---

### Post by Deach on 2007-12-31
I have a Dell inspiron 4000 with 600 mhz and 256 of ram.  I'm curious too.  I Installed kubuntu but that lagged some (ok pretty much) and got the xcfe desktop which would make it xubuntu basically.  It runs way better with that on it.  I was reading at another forum though that there's ways to trim the fat off the KDE desktop and make it pretty usable too.  

I guess I'll try some of the others mentioned too.  I've checked the live cd running on a couple of builds but obviously that was sloooooow.  I'll keep an eye out  here and see what others are using.

---

### Post by elithrar on 2008-01-01
> **Deach said:**
> I have a Dell inspiron 4000 with 600 mhz and 256 of ram.  I'm curious too.

[Fluxbuntu](http://fluxbuntu.com/js.html) would be ideal for a system like that, IMO. You get all the basics - word processing/spreadsheets/email/web-browsing - and you can easily add on a basic music app if wanted.

---

### Post by exploder on 2008-01-01
I think Antix or Fluxbuntu but if the machine is really old then Vector might be another distribution to consider. I have got Vector Linux running on some old machines where nothing else would work. Vector optimizes itself the first time you boot up and the end result is a very fast system.

Just my two cents!

---

### Post by tdrusk on 2008-01-01
puppy linux

amazing

---

### Post by K.Mandla on 2008-01-01
> **VCSkier said:**
> What on, or off, this list would you recommend?  Keep in mind, the laptop is 7 years old, and ease of usability for a Windows user is the first priority.  I will be able to install and setup the operating system for them but will not be there to administer or maintain it, they must be able to handle it on their own.  Thanks!
Can you be specific about the laptop's guts? Knowing more technical points might help suggest a proper distro. (I have two 7-year-old laptops, but one is a 1Ghz machine and the other is 550Mhz, just as an example.)

Off the bat, I'd say if you weren't going to be around to help them with it, you're going to want something simple to maintain and more or less self-sufficient. Go with one you think is intuitive for adding and removing software, and more or less sets itself up. 

I'd experiment with Fluxbuntu (with Synaptic) and Mepis AntiX, and with Wolvix, or maybe Ubuntulite, although it's still not quite finished. All of those performed great for me on an old (sub-500Mhz) laptop. Try them all out briefly and see which one does the best job setting itself up and seems easiest to manage.

---

### Post by tdrusk on 2008-01-01
If you're not going to be around to help him with it put vlc on both of your computers.That way you can be there without being there.

---

### Post by Deach on 2008-01-01
OK...I'll try fluxbuntu and look at antix.  Thanks I've just got a couple of these around and thought I'd try to get them going again.

---

### Post by Rutabega on 2008-01-01
> **Deach said:**
> OK...I'll try fluxbuntu and look at antix.  Thanks I've just got a couple of these around and thought I'd try to get them going again.

Definitely check out antiX. I've currently got antiX installed on my laptop, probably the most complete fluxbox configuration that I have come across. I find Fluxbuntu's fluxbox configuration lacking, unless you're a veteran or willing to spend the time setting the menus and configurations in fluxbuntu I'd suggest antiX.

---

### Post by RedSquirrel on 2008-01-01
I've always liked the idea of starting from a minimal system and adding the stuff you want. You can do this with Ubuntu using either the alternate install CD or the net installer:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

If you're setting up a system for someone else, you would just have to add the software that will make it fairly straightforward for them to use and maintain the system, for example, synaptic, update-notifier, etc.

Xfce is not hard to use (there is a metapackage for that in the repositories  -- xfce4).

You can go lighter and install a window manager instead of a full desktop environment. IceWM might be a good choice. I use mainly Fluxbox or Openbox but it takes a little time and practice to get used to them.

---

### Post by mmb1 on 2008-01-01
Depending on the age of the hardware, you could run anything between xubuntu and damn small linux.

---

### Post by (((X))) on 2008-01-01
of course MEPIS!

---

### Post by VCSkier on 2008-01-01
Thank you everyone for your responses so far.  I'll get some more details on the hardware specs next time I talk to them, but I think most laptops made in 2000 and 2001 were between 500 and 1000 mhz.  Therefore, I would think that an XFCE-centric operating system would be sufficiently light.  A system with IceWM or fluxbox might run alittle faster, but I think XFCE would give them a better experience all around, considering they've never experienced anything but Windows before.  Would you agree?

If so, what XFCE based operating system do you think would be the best for these kind of people?  Would Xubuntu be the easiest to maintain, or would SAM or some other be better.

---

### Post by elithrar on 2008-01-01
Personally, I'd say Xubuntu - you've got the Ubuntu repo's to rely on if they want any additional software, it has a great GUI and there's a lot of docs/support (wiki & forums) available for yourself to help them fix any issues they might come across.

---

### Post by angry_johnnie on 2008-01-02
you could try puppy.  it's small enough, fast enough, and functional enough.  it's really amazing to see all the things that just work out of the box, and the best thing is that it's so lightweight, it'll run on a matchbox if it must!  there's a puppy called wNOP that comes with compiz fusion already.  it really is worth a try.

---

### Post by ceciliaFX on 2008-01-02
wouldn't the smart thing to do be boot the system up with a live CD and see how it responds?

my 2002 Dell Latitude (with nVidia and half gig of memory) seems very happy with Ubuntu 7.10

it is automatically online - mostly because I have FIOS

I made my system multi boot as soon as i got it and am only in the process of getting enough courage to replace the orginal Red Hat with Ubuntu (and not touch the Windows that's there now)

---

### Post by RedSquirrel on 2008-01-02
> **VCSkier said:**
> Thank you everyone for your responses so far.  I'll get some more details on the hardware specs next time I talk to them, but I think most laptops made in 2000 and 2001 were between 500 and 1000 mhz.  Therefore, I would think that an XFCE-centric operating system would be sufficiently light.  A system with IceWM or fluxbox might run alittle faster, but I think XFCE would give them a better experience all around, considering they've never experienced anything but Windows before.  Would you agree?

I agree. IceWM isn't too hard in terms of just using it, but Xfce is probably easier to customize and maintain, especially for someone who is used to Windows.

I haven't tried out Xubuntu since edgy, but it was pretty nice. I think it's gotten a little more bloated lately, but it may still be OK (depending of course on the specs of the target machine). As mentioned above, the Ubuntu forums are great for getting help, and that may be something to consider should they have questions or get stuck.

You can also setup your own custom Xfce system as I mentioned, but that obviously takes longer and requires more knowledge than simply inserting an installation CD. 

I think if the machine(s) can handle it, Xubuntu would be a good choice.

---

### Post by sujoy on 2008-01-03
didn't try out Xubuntu but I think Zenwalk is a very good light weight distro that has XFCE and being based on Slackware, its solid and stable.

---

### Post by dizee on 2008-01-04
Puppy is very fast and designed to be easy to use for Windows converts. Should run great on a laptop from 2000.

---

### Post by liquidfunk on 2008-01-05
Try LinuxMint Fluxbox. Pretty nippy.

---

### Post by Presto123 on 2008-01-06
I just got Puppy today. Quite good. :) Good enough, in fact, that I have added it to my distro list and am running it right now.

Not as pretty as other distros like Ubuntu, but perfect for USB booting. I haven't tried the compiz enabled one, but I wonder if I can get it onto this USB in reasonable space.

---

### Post by LinuxGuy1234 on 2008-01-06
> **VCSkier said:**
> I have some friends that have an old laptop (purchased in 2000 or 2001) who have become very frustrated with Windows' performance on it.  I'd like to offer to install a Linux operating system on it for them, but I'm not sure what distribution would be intuitive and/or lightweight enough for them to use and be completely satisfied.

They aren't particularly computer savy, and have a young child, so don't have alot of time to learn the intricacies of a complicated operating system.

Here are the options and concerns that come to my mind:
Xubuntu (is it light enough)
Fluxbuntu (is it easy and stable enough)
Gebuntu (is it stable and light enough)
gOS (will it run on a laptop and is it stable enough)
MEPIS antiX (is it easy enough)

I have no personal experience with any of the distributions on this list with the exception of Xubuntu, and that brief experience was when the project was first officially adopted.  So any advice is greatly appreciated.

What on, or off, this list would you recommend?  Keep in mind, the laptop is 7 years old, and ease of usability for a Windows user is the first priority.  I will be able to install and setup the operating system for them but will not be there to administer or maintain it, they must be able to handle it on their own.  Thanks!

Slackware, Debian or a base system install of Ubuntu (well you get the base packages to get to a "user@computer~$" prompt).

---

