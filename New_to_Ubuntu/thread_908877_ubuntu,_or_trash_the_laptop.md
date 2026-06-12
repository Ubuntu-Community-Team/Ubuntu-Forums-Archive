---
title: "ubuntu, or trash the laptop?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by cnymike on 2008-09-02
I've got an old HP Pavilion XH136 laptop with 600MHz Celeron and just 256MB RAM. I'm currently running Windows XP Professional sp2 but it's slow and I hate windows.

I thought maybe I'd try installing ubuntu and see if it would inject a bit of life in this old laptop. But then I noticed that the minimum system requirement is 384MB. Bummer.

Am I dead in the water or do I have some other options? I'd really love to try ubuntu on this dog of a machine that is in beautiful condition but apparently grossly underpowered.

What do you suggest?

Michael

---

### Post by Whiffle on 2008-09-02
Give it a shot, or try something lighter like Xubuntu.  Can't hurt.  With the right setup and tweaks, Linux flies.

---

### Post by iaculallad on 2008-09-02
With that specification, try Zenwalk (v5.2 Final is already out).

---

### Post by linuxlizard on 2008-09-03
Try one of the pclinuxos lightweight spinoffs and it should work just fine.

pcfluxboxos, tinyme, or sam should all put new life into your machine. zenwalk is ok too (I used it for a year on my old laptop before finding pcfluxboxos), but these are all a little more fast and and have much, much more software available via synaptic.

I'd be really surprised if you could get any ubuntu spinoff to work at a decent speed on your laptop...

---

### Post by rossjman1 on 2008-09-03
Xubuntu should work, and Fluxbuntu will definatly work. Years ago I was running plain Ubuntu (one of the first versions) on a 500MH Celeron and 128MB of ram. XFCE flew, and Gnome was still useable. System requirements have gone up a little bit, but either way it should be faster than Windows XP.

---

### Post by Oldsoldier2003 on 2008-09-03
I would try xubuntu, fluxbuntu or even damn small linux. Puppy linux is also an option. 

Basically there are a lot of good choices out there- that laptop has plenty of life left :)

---

### Post by shae on 2008-09-03
I would like to chime in you could try Ubuntulite (see link in my signature).

---

### Post by cnymike on 2008-09-03
While waiting for replies, I went ahead and installed the full desktop version and although the installation took a while, it completed without any problems and I'm now booted into ubuntu on my old laptop. I'm thrilled. Of course, I'm not sure it's performing as "fast" as it could be, but so far I've not run into any glitches.

Should I want or need to speed things up a bit, how easy is it to revert to xubuntu or some other flavor? I'm pretty much a total noob.

---

### Post by wolfen69 on 2008-09-03
on a machine with specs like that, xubuntu 7.04 will run *OK*, but you should really think about distros like puppy or go with fluxbox as a desktop environment.

---

### Post by HittingSmoke on 2008-09-03
I have an old P3 500 mhz desktop with 256 MB of RAM running Kubuntu just fine. Its not lightning fast but its a hell of a lot better than running Windows on it. I'ts completely usable for web browsing and the like.

---

### Post by Oldsoldier2003 on 2008-09-03
> **cnymike said:**
> 
Should I want or need to speed things up a bit, how easy is it to revert to xubuntu or some other flavor? I'm pretty much a total noob.

Xubuntu is easy. just install the xubuntu-desktop package. Then if you want to clean it up and get rid of the excess gnome stuff follow this [tutorial]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by linuxlizard on 2008-09-03
Do yourself a favor and try the ones I suggested (sam, tinyme, or pcfluxboxos).

I just finished comparing this morning on an old computer slightly less powerful than yours- there is no comparison in speed between one of those and fluxbuntu. They run much, much faster and you still have all the bells and whistles, and thousands of apps in synaptic just like ubuntu- but unlike dsl or puppy which have about the same system requirements as these I am suggesting.

Unless you are just going for brand name loyalty, ubuntu just isn't worth it on a low end machine like yours (and some of mine).

Don't get me wrong- Ubuntu is great for machines with better specs- the best IMO.

---

### Post by cnymike on 2008-09-03
Oldsoldier- Is installing xubuntu as intuitive as ubuntu was? After installation, it basically found my network, adding my printer was a snap...I was amazed that I didn't really have to configure anything at all. I'm such a dunce with all this that I don't want to get into a position where I've got to start digging in to it to make it work. ubuntu is running just fine right now for me on my archaic laptop. I even added Java already. So I'm totally willing to try xubuntu, but don't want to have to worry about configuring it. What do you think?

linuxlizard- Many of my concerns about xubuntu apply to your suggestions too. I looked at the sites you mentioned and SAM seems really vague as far as what info is on the website. pcfluxboxos was perhpas the most compelling but my concerns about ease of installation and setup remain.

And finally, when installing ubuntu, I was not sure about how to set up partitions and I think I just went with the default. As far as I recall, I've now got 3 partitions of about equal size...maybe 25MB each? Is that reasonable or should I manually create partitions. There are lots of opinions on partition schemes but I'm just going to be using this for surfing, music and some web development. Nothing too fancy for me.

This forum has been really helpful. Thanks.

Michael

---

### Post by CJ56 on 2008-09-03
Can I just second the Zenwalk suggestion before you commit for good..?

I have a wheezy old Dell with a Celeron processor & 256 Mb RAM and have run Zenwalk on it very happily for the last year. I've just put on Zenwalk 5.2, dedicating the whole hard drive (all 40 Gb of it) to Zenwalk, done a few updates, and left it more or less at that.

All the software Zenwalk put on the distro works well, I can watch DVDs, write documents with AbiWord, listen to music and surf the net. The only thing you might have to do is install a driver for your wireless card with Ndiswrapper - not a problem if you have the original driver disc.

Hope this helps... ;)

---

### Post by snowpine on 2008-09-03
> **cnymike said:**
> Oldsoldier- Is installing xubuntu as intuitive as ubuntu was? After installation, it basically found my network, adding my printer was a snap...I was amazed that I didn't really have to configure anything at all. I'm such a dunce with all this that I don't want to get into a position where I've got to start digging in to it to make it work. ubuntu is running just fine right now for me on my archaic laptop. I even added Java already. So I'm totally willing to try xubuntu, but don't want to have to worry about configuring it. What do you think?



Hi Michael, you can 'sudo apt-get install xubuntu-desktop' from within your existing Ubuntu installation. There is no need to reinstall if you do this method; basically all you're doing is putting a new windows manager or "shell" over your existing Ubuntu "core". It will keep all of your documents and settings intact (except for settings specific to Xubuntu, of course). Then, when you bootup, you'll see a "Sessions" option on the login screen. You can choose between Gnome (Ubuntu) and Xfce (Xubuntu) each time you log in.

Adding xubuntu-desktop to Ubuntu is a low stress, low risk, easy way to speed things up. If you are happy with the outcome, great! You can stop there.

If you aren't happy with Xubuntu, there are many other options to try. They will all require a fresh install, though, so my advice is start with Xubuntu for now.

---

### Post by silverglade00 on 2008-09-03
Another alternative for you...

I have a laptop that runs perfectly well except it has a huge crack through the screen. I ended up installing Ubuntu Server on it and remote into it. I use it to learn remote server administration, apache, mysql, and all kinds of other goodies. As long as you can ssh in, you can do pretty much everything. Ubuntu Server should run perfectly well on that computer since there is no GUI (though you can install a small one for learning). Just set the power setting to do nothing when you close the lid.

---

### Post by cnymike on 2008-09-03
Well, I'm installing xubuntu using the terminal. That is so cool to be able to do that. Like I said, I'm newbie and have a lot to learn about the command line. Anyway, ubuntu was running OK and I'm not even sure how I'd know if it was running slow or not. Is it boot time that is the issue? Or just sluggish application launching? How would I be able to run some benchmarks to compare the performance of ubuntu vs some of the other suggestions like xubuntu?

Sorry for asking so many questions.

snowpine, your idea of installing server had crossed my mind. But for now I think the non-server is the way for me to go. I plan to use this laptop frequently now that I've got rid of Winblows XP...the speed difference in booting into ubuntu compared to XP is astounding.

---

### Post by snowpine on 2008-09-03
> **cnymike said:**
> Well, I'm installing xubuntu using the terminal. That is so cool to be able to do that. Like I said, I'm newbie and have a lot to learn about the command line. Anyway, ubuntu was running OK and I'm not even sure how I'd know if it was running slow or not. Is it boot time that is the issue? Or just sluggish application launching? How would I be able to run some benchmarks to compare the performance of ubuntu vs some of the other suggestions like xubuntu?


Yes, it is very cool. :) I don't think you'll see a difference in boot time. What you will (hopefully) notice is that simple everyday tasks like scrolling through menus, resizing windows, switching between applications, etc. are all a bit "snappier."

---

### Post by egalvan on 2008-09-03
> **cnymike said:**
> Well, I'm installing xubuntu using the terminal. That is so cool to be able to do that. Like I said, I'm newbie and have a lot to learn about the command line. Anyway, ubuntu was running OK and I'm not even sure how I'd know if it was running slow or not. Is it boot time that is the issue? Or just sluggish application launching? How would I be able to run some benchmarks to compare the performance of ubuntu vs some of the other suggestions like xubuntu?

Sorry for asking so many questions.

snowpine, your idea of installing server had crossed my mind. But for now I think the non-server is the way for me to go. I plan to use this laptop frequently now that I've got rid of Winblows XP...the speed difference in booting into ubuntu compared to XP is astounding.

Well, 'running fast or slow' is relative, at least to me, because it depends on what machine I'm using.

My slow machine:
 HP E-PC, 933mHz, 256M RAM, 1meg on-board video, no expansion options
runs Xubuntu well, Firefox is a little slow loading and rendering.
I need a little patience with this one.

My fast machine:
 HP M7690n, 2.13 Core 2 Duo, 2G RAM, 256 nVidia 7600GT, lots of expansion, SATA-II drives...
runs Ubunut/Kubuntu/ FAST!, loads FAST!, renders FAST!.. did I mention it was FAST!

I don't expect that little old E-PC to run as fast as that big, new, MediaCenter

Look at it like different ages in people. Young kids run fast, older folks walk slow.

Adjust your speed to the machine.

And if I really want to see FAST!, I boot a Puppy v4 LiveCD on that new computer.

It sounds as if you are having fun with your machines and Linux.

Never be afraid of asking questions;
when you stop asking, you stop learning.

---

### Post by ugm6hr on 2008-09-03
> **cnymike said:**
> Anyway, ubuntu was running OK and I'm not even sure how I'd know if it was running slow or not. Is it boot time that is the issue? Or just sluggish application launching? How would I be able to run some benchmarks to compare the performance of ubuntu vs some of the other suggestions like xubuntu?

Ubuntu is only slow if you think it is too slow for the use you intend it for.

If you are happy with it - just carry on.  And most people refer to application launch times, speed of applications once open; boot time does come into the equation too, but given you probably only rebbot 1-2x per day, an extra 30secs of boot time is probably irrelevant in the long term.

But no harm will come from install xubuntu-desktop on top (except for a bit of HD space).  Just select XFCE from the sessions menu when you next log in.

There are plenty of even faster options that can be added on top of Ubuntu if XFCE (Xubuntu) is not your cup of tea.  In fact, Xubuntu tends to use a lot of "Gnome" (i.e. Ubuntu) applications in the background, so the speed difference is not that noticeable unless you tweak a few things.

Ubuntulite - as mentioned by shae - can also (I believe) be added on top of Ubuntu; it's marginally more effort than Xubuntu, but uses LXDE so should be significantly faster.

---

### Post by cnymike on 2008-09-03
I think my only other two "issues" are...

1. Partitions. I guess I have two partitions...Home and File System and both are the same size (about 30GB). Is this reasonable and fine as it is for my general daily use of the computer?

2. It doesn't seem quite right the way my hibernate or snooze button works anymore. It feels like I'm always turning off the computer via the on/off button and that hibernate or sleep doesn't work any more. And if I close my lid, the display stays on I think. Is this something that I can fix somewhere?

Michael

---

### Post by Dreamerman on 2008-09-03
> **rossjman1 said:**
> Xubuntu should work, and Fluxbuntu will definatly work. Years ago I was running plain Ubuntu (one of the first versions) on a 500MH Celeron and 128MB of ram. XFCE flew, and Gnome was still useable. System requirements have gone up a little bit, but either way it should be faster than Windows XP.

Hmmmm.... I installed Xubuntu in my very old P3 HP Vectra MMX 550MHz 512MB RAM & discovered that it is as slow/fast as WinXP. Configuring it to work takes more time than XP & at the end I reinstalled XP which I can do with my eyes closed. There are tweaks one can do in XP to speed up any machine. I am not advocating XP but just to share my personal experience. I have Ubuntu on my main machine (which is also old) & after a few weeks of fresh install, it is showing signs of slowing down. Don't quite understand it.

Cheers

---

### Post by cnymike on 2008-09-03
Dreamerman, one thing I can say with certainty is that on my old laptop, XP took forever to boot and launching apps was slow beyond belief. I may be splitting hairs between ubuntu, xubuntu and all the other variations, but even ubuntu is noticeably faster for me by a large margin. NOt sure why you seem to have the opposite experience... it just doesn't make sense actually since XP is such a resource hog.

---

### Post by Dreamerman on 2008-09-03
> **cnymike said:**
> Dreamerman, one thing I can say with certainty is that on my old laptop....

Don't make sense to me either but I report what I see. I won't crack my brains over my old P3 as all it does is sit under my desk running 24/7 torrenting. Does not run other apps or even has a monitor/kb/mouse.

My real concern is my old main machine (specs below). It ran well on the 1st week after fresh Hardy install but is reduced to a crawl now (3rd week). Struggling to run 2 apps simultaneously (say unrar & browse internet). It has all the latest updates & I don't play games (hence never upgraded my old pc). At least previous XP don't seems to crawl running simple apps.

---

### Post by mikjp on 2008-09-04
> **cnymike said:**
> What do you suggest?

Any of the ten distros I mention in my blog posting about [lightweight distros](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html).

mikko

---

### Post by linuxlizard on 2008-09-04
> linuxlizard- Many of my concerns about xubuntu apply to your suggestions too. I looked at the sites you mentioned and SAM seems really vague as far as what info is on the website. pcfluxboxos was perhpas the most compelling but my concerns about ease of installation and setup remain.


Well, to tell you the honest to goodness truth- you aren't going to find one that is as easy as ubuntu to setup on a computer that old- at least if you intend to use software other than what comes with it. And when I say that I mean ubuntu spinoffs like xubuntu and fluxbuntu aren't going to be easy as ubuntu either. At least sort of- they don't have the friendly forums and stuff. But none of these pclinux spinoffs are hard either- most stuff like codecs and flash come pre-installed, and they have an excellent and easy to use control panel for the system settings. You can also ask questions on each one's forums as well as pclinuxos forums.

That said, all linux is pretty similar, and if you can set any one of these up, you can set another up. If you are really determined to get your machine into a useful state, now might be a good time to get into the mindset that you may need to spend a little time tinkering with it first.

All of these set up pretty nicely though- I think you would be surprised if you actually tried one instead of just peeking at the home page- and all are live cd's- you can try before you commit to one on your hard drive. For that matter you can actually install each and play around with it for a day or two and then try another- the cost is only the cost of a cd- what's that like 10cents to try each? I believe all of these come with multimedia codecs and flash and stuff already built in- you just will want to enable your video card (for nvidia, you just go into synaptic, search for nvidia, and select the latest driver that has your card listed in the description, then click apply and it does the rest of the magic of setting things up for you.

Honestly- if you want your machine to be useful, you are going to find these much better- ubuntu variants are going to be much, much slower and a headache to use.

PS- if you end up going with fluxbox even in ubuntu or elsewhere- you may want to look into grabbing fbpanel from synaptic. It gives fluxbox a nice lightweight panel and start menu. It can be configured to look like gnome panels in ubuntu as well...

---

### Post by cnymike on 2008-09-04
linuxlizard, thanks for that info.

I've settled on xubuntu for the time being. It is definitely faster on my laptop than ubuntu and I've been easily able to add a few packages already so I'm relatively comfortable right now. Since I'll mostly be using the machine as a browser, my demands aren't great. And as long as I can see flash, quicktime and run java applets, I'm good to go. And so far I can do all of that. So I'll run with xubuntu for now. Maybe I'll install the LiveCD versions of a couple others and get a fell for them, but I've got to say that xubuntu is OK for now.

---

### Post by quanumphaze on 2008-09-04
> **Dreamerman said:**
> My real concern is my old main machine (specs below). It ran well on the 1st week after fresh Hardy install but is reduced to a crawl now (3rd week). Struggling to run 2 apps simultaneously (say unrar & browse internet). It has all the latest updates & I don't play games (hence never upgraded my old pc). At least previous XP don't seems to crawl running simple apps.

That's very odd. I'm running it on a Celeron @ 1.6GHz laptop with 1 GB RAM and the only slowing down Ubuntu did was bootup time and Gnome's login time. Apps are still snappy and running fast. And it's pretty much the same speed as XP when that was on it.

For your problem it's best to make a new thread so you get more attention without stealing it from cnymike.

---

### Post by Dreamerman on 2008-09-05
quanumphaze, ok.

---

### Post by cnymike on 2008-09-05
CJ56, I gave Zenwalk a look today and was impressed and am now installing it. It was faster than xubuntu and auto configuered by network card which pcfluxboxos did not do. I'll give Zenwalk a whirl and see if it stays. So far I like it a lot.

---

