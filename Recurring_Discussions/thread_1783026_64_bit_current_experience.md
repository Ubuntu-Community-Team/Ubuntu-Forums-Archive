---
title: "64 bit: current experience"
date: 2011-06-15
forum: Recurring Discussions
---

### Post by Nonno Bassotto on 2011-06-15
When I bought my laptop with 4GB of RAM a couple years ago, the common wisdom was that support for 64 bit in Linux was still poor, hence it was a better choice to stick with 32 bit, even if that means losing 1GB  of RAM because you cannot address it.

What is your experience with 64 bit today? Are there still problems with Flash, Skype and so on? Or is everything working smoothly? Apart from being able to address more than 3GB of RAM, are there actual improvements? Can one find all the major packages? And if not, will the 32 bit packages work the same?

Please, advice me, as I am considering whether the time has come to switch to 64 bit.

---

### Post by Bandit on 2011-06-15
You know me. I havent used 32bit on my system since 5.04.

But now things are so much easier, I dont have to compile everything from scratch to get my multimedia working.

---

### Post by Nonno Bassotto on 2011-06-15
Can you describe in a little more detail? What did you have to compile manually? Do you have to compile anything today?

What with notoriously problematic (and proprietary) software like Flash or Skype?

---

### Post by Bandit on 2011-06-15
> **Nonno Bassotto said:**
> Can you describe in a little more detail? What did you have to compile manually? Do you have to compile anything today?

What with notoriously problematic (and proprietary) software like Flash or Skype?

Dont use Skype..

Flash issue was resolved when all systems became hybrid systems containing both 32bit and 64bit libs, thus allowing 32bit firefox to run on a 64bit kernel. But with all the 64bit support we have now, this is becoming less of an issue. Today other then hardware requirements there is no real noticeable difference from 32bit Linux to 64bit at least for the end user.

What did I have to compile back then, well I am not listing everything but I will say everything from every audio and video lib, to all gstreamer, xmms, mplayer, totem.. etc.. etc..  You get the idea..

---

### Post by mips on 2011-06-15
been using 64-bit for years. Currently everything works fine for me in 64-bit without any tweaks etc.

---

### Post by handy on 2011-06-15
I've been using 64bit since Breezy Badger - 5.10.

Next to no problems, the last of them has been Flash which is really no problem these days.

Using:

 [https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/#install-beta](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/#install-beta)

Has certainly smoothed the flash problems out completely for me (though it works for both 32 & 64 bit hardware/systems). :)

---

### Post by BrokenKingpin on 2011-06-15
I have been using 64-bit for years with no issues as well. If you have a 64-bit machine you should be using a 64-bit OS.

---

### Post by 3Miro on 2011-06-15
I have been using exclusive 64-bit Linux since 8.10. Flash issues used to be resolvable, not they are almost non-existent. Skype work just fine.

There are still some printer issues.

BTW you can use all 4GB of RAM on a 32-bit machine if you install the PAE kernel.

---

### Post by DZ* on 2011-06-15
> **3Miro said:**
> BTW you can use all 4GB of RAM on a 32-bit machine if you install the PAE kernel.

Probably not an issue for a regular desktop usage, but if a single process can grow that big they'd have to go 64.

---

### Post by Paqman on 2011-06-15
> **mips said:**
> been using 64-bit for years. Currently everything works fine for me in 64-bit without any tweaks etc.

Same here.

Back when I first switched (about 6.06 or so) there were issues with Flash which meant you had to run a 32-bit browser. Since that was sorted i've had no issues at all, except for very occasionally running into a 3rd party app that doesn't have a native 64-bit version (Amazon MP3 downloader is the main one that springs to mind).

Skype works fine for me (when their network is up, that is).

There's no reason at all to throttle a 64-bit chip down to 32-bit speeds IMO.

---

### Post by Gregorybekkers on 2011-06-15
I'm using 64bit versions for more then a year now and it works fine.

Flash and stuff is much better now. 
no problem with skype aswell. 

works fine forme.

---

### Post by oldos2er on 2011-06-15
I've been using 64-bit for years too, without issues. Use FlashAid to install flash, since 64-bit flash is not in the repos.

---

### Post by Ace..... on 2011-06-15
So why is the 32bit ubuntu download recomended?

see:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

my thread is
[http://ubuntuforums.org/showthread.php?t=1782145](http://ubuntuforums.org/showthread.php?t=1782145)

Im at disk partitioning stage, and need to choose an os.

---

### Post by handy on 2011-06-15
The reason that 32bit is recommended is that new Linux users will usually have fewer problem if they make that choice.

---

### Post by Nonno Bassotto on 2011-06-15
Thank you all for the replies. It seems that 64 bit is the way to go.

Now, do I have to reinstall everything from scratch, or can I just download the 64 bit kernel from synaptic and start using that one?

---

### Post by Jesus_Valdez on 2011-06-15
Use Adobe Air used to be a problem for 64bit, don't know the current status.

---

### Post by Maheriano on 2011-06-15
64 bit isn't a problem at all anymore. Loading the native Flash 10 used to be a pain in the *** a few releases ago but it's fine now.

---

### Post by Ace..... on 2011-06-15
ok....... so what are the upgrade issues?
ie. do i install 32 bit on my 64 bit pc, and then, in say 6/12 months time, upgrade to 64bit.

or is the recommendation running a bit out of date now (lol)?

---

### Post by tgm4883 on 2011-06-15
> **Ace..... said:**
> ok....... so what are the upgrade issues?
ie. do i install 32 bit on my 64 bit pc, and then, in say 6/12 months time, upgrade to 64bit.

or is the recommendation running a bit out of date now (lol)?

Install 64-bit now. To go from 32-bit to 64-bit requires reinstalling the OS.

---

### Post by 3Miro on 2011-06-15
You cannot "upgrade" from 32-bit to 64-bit. You can only make a complete new install.

---

### Post by Maheriano on 2011-06-15
> **3Miro said:**
> You cannot "upgrade" from 32-bit to 64-bit. You can only make a complete new install.

This. There is no upgrade.

---

### Post by TBABill on 2011-06-15
I use 64 bit on machines from as far back as 2002 or 2003 and as new as 2010. Works great on all of them and I never use 32 bit distros. Flash is easy with either Ubuntu Tweak or with Flash Aid, either of which can keep you with a 64 bit "latest" version of Flash from Adobe. As stated above a couple times, reinstall to get to 64 bit from 32 bit.

---

### Post by mips on 2011-06-15
> **Ace..... said:**
> So why is the 32bit ubuntu download recomended?


Because the majority of people in the world still have older 32-bit computers. The 32-bit version will work on 32-bit & 64-bit hardware but if a person downloads the 64-bit version (s)he won't be able to run it on 32-bit hardware. It's the safe recommendation.

---

### Post by mips on 2011-06-15
> **Nonno Bassotto said:**
> 
**Now, do I have to reinstall everything from scratch**, or can I just download the 64 bit kernel from synaptic and start using that one?

**From scratch**, there is no upgrade.

---

### Post by Donalt2010 on 2011-06-15
I'm running 32 bit on a 64 bit machine, so buying an external hard drive this weekend and doing some backing up then doing a clean install of 64 bit 10.04.

---

### Post by giddyup306 on 2011-06-15
I'm far from a Linux guru, and I don't have any more problems with 64-bit.  Flash works fine (there was a new version for 64-bit that came out a few months ago).  Mint 11 has flash pre-installed. 

They say that you only get about 7% more performance from a 64-bit OS.  I paid for a 64-bit processor, I want to utilize it.  What I noticed is that USB 2.0 is MUCH faster with 64-bit.  When I was using 32, I would rarely see high 20's.  I snapped this screenshot yesterday.

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/woah.png[/IMG]

I've seen it as high as 45/sec before, but this is by far the highest.  I encrypted this drive with Truecrypt.  I read in the documentation that it might increase speed due to pipelining, so that might be where the extra 5mb/sec came from...  And yes, this is 2.0.  I don't have a usb 3.0 card, or any usb 3.0 devices.  What's funny is that this is mypassport, and it seems to drag compared to mybook.

BTW the 64-bit Ubuntu uses the POE (think that's what it's called) Kernel if you have over 4 GB of ram.  The 32-bit Ubuntu uses all 6 gigs of RAM on my laptop.

---

### Post by tgm4883 on 2011-06-15
> **giddyup306 said:**
> 
BTW the 64-bit Ubuntu uses the POE (think that's what it's called) Kernel if you have over 4 GB of ram.  The 32-bit Ubuntu uses all 6 gigs of RAM on my laptop.

I think you mean the 32-bit version of Ubuntu uses the PAE kernel. There is no reason for a 64-bit machine to use PAE.

---

### Post by mips on 2011-06-15
> **giddyup306 said:**
> 
They say that you only get about 7% more performance from a 64-bit OS.  I paid for a 64-bit processor, I want to utilize it.  What I noticed is that USB 2.0 is MUCH faster with 64-bit.  When I was using 32, I would rarely see high 20's.  I snapped this screenshot yesterday.

Depends very much on the application. When you do stuff like encoding of audio/video, compression, encryption etc it makes a big difference I would say.

---

### Post by maestrobwh1 on 2011-06-15
The only issue I ever had with 64 bit was when I wanted to install the AmazonMP3 Downloader.  I have been using 64 bit on my Asus 1201T sub notebook with 64 bit NEO processor.

I had to use --force architecture on the package and I could not use gdebi to make it download the dependencies and it was kind of a pain.  I did that with Lucid.  Okay so with Natty I decided this was no big deal, so I just have 32 bit on my home machine for that.  The Amazon Cloud player kind of came out around the same time so I don't need to "have" all my music on all of my machines.

In other words, there is NO observed issue running 64 bit from my experience since I started using a 64 bit processor.

I ordered a 4 GB chip on Amazon already because I like Natty so much and want to see what the extra 32 bits can do with the extra 2 GB.  I have been using the 'buntu's since Dapper (6.06) but always found myself using things like Puppy Linux because of the raw speed I would get out of their "light" nature.  Kubuntu Natty is very quick on its feet and I still have a non stripped down OS.

---

### Post by giddyup306 on 2011-06-15
> **tgm4883 said:**
> I think you mean the 32-bit version of Ubuntu uses the PAE kernel. 


That's what I meant to say.

---

### Post by oldos2er on 2011-06-15
> **maestrobwh1 said:**
> The only issue I ever had with 64 bit was when I wanted to install the AmazonMP3 Downloader. 

There are a couple solutions to having a 64-bit Amazon mp3 downloader, if you're interested: 

[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

[http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/)

---

### Post by handy on 2011-06-15
> **mips said:**
> Depends very much on the application. When you do stuff like encoding of audio/video, compression, encryption etc it makes a big difference I would say.

You are right on it there mips. 

In the days that I have briefly used 32bit Linux, I wasn't using anything other than DVDShrink for ripping backups of my DVD collection.

Since then I've been using HandBrakeCLI, which most definitely makes good use of both 64bit & all of the cores that your machine has available (in the most intelligent & considerate way).

---

### Post by wolfen69 on 2011-06-15
I have been using 64bit for a couple years now, and would never go back to 32bit. Works great for me.

---

### Post by FuturePilot on 2011-06-15
inb4 "use PAE"

PAE is a hack.

Been using 64bit since 8.04. It's been a great experience so far and it will probably continue to get better as 32bit gets phased out.

---

### Post by BrokenKingpin on 2011-06-15
> **Ace..... said:**
> So why is the 32bit ubuntu download recomended?

Because some users don't know if they have a 32-bit or 64-bit CPU, so installing the 32-bit will work regardless.

I personally do not think they should be recommending the 32-bit over the 64-bit, as the 64-bit is just as usable and stable.

---

### Post by lulled on 2011-06-15
Just a question: PAE sounds like "the perfect plan" for those whose sole purpose for using 64 bits is to use all the RAM they have. Is there a "but" about using that PAE solution?
"PAE allows you to use all of your RAM **BUT** ..." ?

I'm asking this because although I haven't had any problems (at least none I have linked to the fact I'm using 64 bits), and Flash wasn't a pain to install, I feel that some Flash apps just don't go that smoothly (being a Web Dev myself, that can be a problem). YouTube, weirdly, works 100% fine, but some other Flash apps don't. It's like when I place my mouse cursor over some spot of the Flash app, that spot will disappear. Has anyone faced that? Is this a 64 bits related flaw?

Since YouTube works just perfect, I sense it's something about HOW the Flash presentation was exported, but I don't know anything about Flash development.

Thank you very much, guys.

---

### Post by ratcheer on 2011-06-15
I recently got a new PC and started using 64-bit. I have had no problems at all thet I relate to it being 64-bit.

Tim

---

### Post by 8_Bit on 2011-06-15
I use 64 bit Ubuntu and have never had any problems.

Well, I did have graphical glitches with Flash, but it was because it was using the 32 bit version. The 32bit->64bit compatibility layer was making it glitch.
Since I removed the 32 bit Flash and installed the alpha 64 bit version Adobe Labs put out, I've had zero problems. Smooth sailing! :popcorn:

---

### Post by lulled on 2011-06-15
Is this topic the one I ask you how to remove Flash 32 bits? :oops:

---

### Post by 8_Bit on 2011-06-15
You have to find the libflashplayer.so (something like that)

It should be in the following directory
/usr/lib/mozilla/plugins/

Then, download the 64 bit Flash alpha from Adobe Labs. Extract the libflashplayer.so file.
Place this file in the following directory

~/.mozilla/plugins

(This is a hidden folder inside your Home folder. Enable hidden files to see it.)

Then just restart Firefox and you're done! ;)

---

### Post by Khakilang on 2011-06-15
I don't have 4GB RAM (only 2GB) but I use 64bit anyway just to see how it perform. No problem or any issue so far on my 11.04. Give it a go and see for yourself.

---

### Post by 3rdalbum on 2011-06-15
> **Nonno Bassotto said:**
> When I bought my laptop with 4GB of RAM a couple years ago, the common wisdom was that support for 64 bit in Linux was still poor, hence it was a better choice to stick with 32 bit, even if that means losing 1GB  of RAM because you cannot address it.

If you bought your laptop with 4 GiB of RAM, then you were misadvised at the time. 64-bit support in Linux has been excellent for a very long time. 

64-bit support in Windows is meant to be very poor.

---

### Post by tgalati4 on 2011-06-16
The only 64-bit problem I encountered is floola  ([http://www.floola.com/home/](http://www.floola.com/home/)) would only work in 32-bt.  It's a java application and it's stored on your iPod then you can run it on Windows, Mac or Linux, but you either have to have 3 versions on your iPod or pick one version and stick with it.  Regardless, there is no 64-bit linux build that I know of.

---

### Post by wolfen69 on 2011-06-16
> **tgalati4 said:**
> The only 64-bit problem I encountered is floola  ([http://www.floola.com/home/](http://www.floola.com/home/)) would only work in 32-bt.  It's a java application and it's stored on your iPod then you can run it on Windows, Mac or Linux, but you either have to have 3 versions on your iPod or pick one version and stick with it.  Regardless, there is no 64-bit linux build that I know of.

It can be done with:
```
sudo dpkg -i --force-all [package.deb]
```
;)

---

### Post by Dustin2128 on 2011-06-16
Just joined the 64-bit club with my latest arch install. It's pretty nice, honestly- no rough edges or anything (well, none exclusive to 64 bit anyway ;)). Even though I also only have 2GB RAM, I'll probably still be using this computer when 2038 rolls around, so...

---

### Post by mips on 2011-06-16
> **Dustin2128 said:**
> Just joined the 64-bit club with my latest arch install. It's pretty nice, honestly- no rough edges or anything (well, none exclusive to 64 bit anyway ;)). Even though I also only have 2GB RAM, I'll probably still be using this computer when 2038 rolls around, so...

RAM is cheap so dropping in another 2GB would be nice. You might even get the ram for free as lots of people have old ram lying around.

---

### Post by el_koraco on 2011-06-16
> **3rdalbum said:**
> 
64-bit support in Windows is meant to be very poor.

I think that's a leftover impression from the early XP days, when people installed XP and couldn't get their games to work. Sure, recompiling open source programs to 64 bit is easier, but I don't think Windows has too many problems with it, except for maybe some legacy apps. 

On topic, I've been using 32 bit for some unknown reason. Might go 64 bit on the next install.

---

### Post by FuturePilot on 2011-06-16
> **el_koraco said:**
> I think that's a leftover impression from the early XP days, when people installed XP and couldn't get their games to work. Sure, recompiling open source programs to 64 bit is easier, but I don't think Windows has too many problems with it, except for maybe some legacy apps.

Except for the fact that a large majority of the applications you use are still 32bit. So what's the point of having a 64bit OS when you run mostly 32bit programs.

---

### Post by lulled on 2011-06-16
Thanks :D

---

### Post by Dustin2128 on 2011-06-16
> **mips said:**
> RAM is cheap so dropping in another 2GB would be nice. You might even get the ram for free as lots of people have old ram lying around.
Yeah, but I'm saving money for a new build that would use DDR3- old computer uses DDR2, lowish clock too.

---

### Post by manzdagratiano on 2011-06-16
I had 7 OSes - 2 on the Sony VAIO and 5 on the Dell Vostro V13 - all 32-bit.
I learned that the advantages of 64-bit were not merely for > 4GB RAM, for instance, video transcoding etc were much faster on 64-bit, which utilized the full instruction set.
Over the course of a week, I nuked all of the 7 one by one and installed their 64-bit counterparts.

And it is awesome!!!

I use not a single 32-bit app at the moment.

---

### Post by giddyup306 on 2011-06-16
> **mips said:**
> RAM is cheap so dropping in another 2GB would be nice. You might even get the ram for free as lots of people have old ram lying around.


This is so true!  I need to send in my laptop to be "repasted" (I can't do it because I don't want to break something, and I have 2 1/2 years left on the warranty).  I was thinking about having them upgrade the RAM at the same time (one bank is inaccessible unless you take the laptop apart).  The RAM companies say that you need to have all of the RAMS of the same type, so I priced 16 GB of RAM.  It was less than $200.  I couldn't believe that.  I have no idea what I'd do with that much ram...

Or eBay might be an option if you're brave...

---

### Post by PhillyPhil on 2011-06-16
> **FuturePilot said:**
> Except for the fact that a large majority of the applications you use are still 32bit. So what's the point of having a 64bit OS when you run mostly 32bit programs.

Maybe you mean the large majority of applications in existence, not necessarily ones we use.  That's pretty much a given when the community is growing into a new architecture anyway: of course the old one still has more apps.

Anyway, I have a 64 bit browser, 64 bit media player, skype packaged for 64 bit, 64 bit Google Earth, 64 bit VM software, 64 bit flash, 64 bit bt client. 
Those programs cover 90% of my time spent on my computer at the moment.

@OP: 64 bit works great.  Skype is fine. Flash is fine (get the 64 bit version).

---

### Post by Sef on 2011-06-17
More 32-bit or 64-bit, so moved.

---

