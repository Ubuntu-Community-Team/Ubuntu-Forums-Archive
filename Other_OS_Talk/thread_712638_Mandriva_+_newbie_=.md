---
title: "Mandriva + newbie = ?"
date: 2008-03-01
forum: Other OS Talk
---

### Post by datenshi on 2008-03-01
Well, although after trying out Ubuntu on a friend's computer I really love it and wish I could get it to work for me, I think as a total newbie I have to conclude it's not going to work for me with my current computer.  (I have one of the dreaded HP Pavilion dv6000 series laptops with Windows Vista, which seem to have so many problems with Ubuntu that it's just too intimidating for me as a newb.  And yes, I have tried the Live CD and sadly it didn't work out).  However, when I put in a Mandriva live CD everything seems to be working peachy -- it runs great, my wireless and my screen resolution were detected automatically and so on.  I'd like to try installing Mandriva to an external USB hard drive so I can have Mandriva there and keep Windows on my internal drive, but I don't know the first thing about how to partition or about using the Live Install utility on Mandriva One and I can't find any help files or anything explaining how to use it -- not in the OS itself, not on the Mandriva wiki, not in the official forums, not via Google.  Does anyone have any advice/could direct me to help docs on installing to an external USB HD or on using Mandriva's Live Install partitioning software?

I've also asked this question on the Mandriva forum, of course (still waiting for replies), but people in the Ubuntu forum have always been so kind and helpful I thought it might not hurt to check here too.  Thanks very much.

---

### Post by AdamWill on 2008-03-02
When you run the live installer, early on in the process it'll give you a choice of whether to let it do the partitioning automatically, or use 'custom partitioning'. This is the option you want to choose. You can then set the partitions up any way you choose - so in your case, you'd create whatever partitions you like on the external drive, and not mount any of the partitions on the internal drive. That should work. I haven't ever installed to an external drive myself, but I know some of our users have, and it works okay.

---

### Post by r76 on 2008-03-02
The Mandriva forums are not as active as these ones, but it is a great noob-friendly distro.

Personally I'm always a bit wary when trying any distro that the installer might mess up my existing partitioning so I rely on[ system rescue cd]("http://www.sysresccd.org/Main_Page") or the [gparted live cd]("http://gparted-livecd.tuxfamily.org/") to do my partitioning first, then the install of any distro afterwards has been very smooth, i.e. just tell it which partition to use!

These are great tools to have around, and at least be aware of  - for system backups, later changes to partitions, data recovery etc.

---

### Post by SunnyRabbiera on 2008-03-02
Mandriva is a great way to begin, though yes its forums are dry and are nowhere near as good as here

---

### Post by BigSilly on 2008-03-02
I think anyone who uses a PC for any purpose, beginner or not, will find a lot to like about Mandriva. I picked up this month's Linux Magazine which came with a free copy of Mandriva 2008 Powerpack, and so far I am really enjoying using it. Everything works without any fuss. Add in some extra repositories and you're laughing. I'll be sticking with it till the next one for sure.

I wouldn't use it to replace my Ubuntu install, since I do find it easier to get around Ubuntu as my experience with Linux deepens. But I would certainly consider buying Mandriva 2009 Powerpack from them next year. 

I'm surprised it's not more popular to be honest.

---

### Post by Nikolaiownz on 2008-03-02
> **datenshi said:**
> Well, although after trying out Ubuntu on a friend's computer I really love it and wish I could get it to work for me, I think as a total newbie I have to conclude it's not going to work for me with my current computer.  (I have one of the dreaded HP Pavilion dv6000 series laptops with Windows Vista, which seem to have so many problems with Ubuntu that it's just too intimidating for me as a newb.  And yes, I have tried the Live CD and sadly it didn't work out).  However, when I put in a Mandriva live CD everything seems to be working peachy -- it runs great, my wireless and my screen resolution were detected automatically and so on.  I'd like to try installing Mandriva to an external USB hard drive so I can have Mandriva there and keep Windows on my internal drive, but I don't know the first thing about how to partition or about using the Live Install utility on Mandriva One and I can't find any help files or anything explaining how to use it -- not in the OS itself, not on the Mandriva wiki, not in the official forums, not via Google.  Does anyone have any advice/could direct me to help docs on installing to an external USB HD or on using Mandriva's Live Install partitioning software?

I've also asked this question on the Mandriva forum, of course (still waiting for replies), but people in the Ubuntu forum have always been so kind and helpful I thought it might not hurt to check here too.  Thanks very much.

I got DV6000, and i installed ubuntu and it works like a charm and ive had it for over a week. I removed the "splash" from the boot menu when it dident bootup, and there are good guides to the wireless network.

---

### Post by tbroderick on 2008-03-02
> **datenshi said:**
> 
I've also asked this question on the Mandriva forum, of course (still waiting for replies), but people in the Ubuntu forum have always been so kind and helpful I thought it might not hurt to check here too.  Thanks very much.

Don't forget the mailing lists, if the forums are unhelpful.

---

### Post by AdamWill on 2008-03-03
"The Mandriva forums are not as active as these ones"

Well, I have to read every post to the Mandriva forums and they sure feel active enough to me. =) Not *as* many people as here, it's true, but it's certainly a lively place and there's people who are willing to help with just about any problems.

(17,000+ posts to said forums in three years, and counting...)

---

### Post by AdamWill on 2008-03-03
"I've also asked this question on the Mandriva forum, of course (still waiting for replies)"

By the way, I went through the forums today and don't recall seeing your post. Are you sure you were using the official forums, at [http://forum.mandriva.com/](http://forum.mandriva.com/) ? If so, could you send me the link to the post so I can figure out why I missed it? Thanks.

---

### Post by Hallvor on 2008-03-03
Too much activity in the forums might not always be a good thing. It may indicate that a lot of people are experiencing problems.  :)

I installed Mandriva spring 2007 on a laptop last year, and it was so easy I didn`t need a forum for anything. The Control Center was also brilliant.

---

### Post by djbsteart1 on 2008-03-03
I have had a great experience with mandriva. bar my printer, otherwise it is perfect. 
The forums being dry is about right, although when you do get a response, it is always helpful. I'm sure the wiki and docs are good, I have just never needed them.

Installing on an external drive will be ok. However, before you proceed with anything, check that your bios supports booting from usb as I guess that that is how the drive will connect. 
If your bios does, then it should be ok to go ahead and install on a partition of the drive. I would advise as well using gparted or system rescue cd, both can be found on distrowatch.com, which is a good site for anything to do with various distro's.

---

### Post by mick222 on 2008-03-03
Mandriva grub didn't detect my ubuntu install you will need to configure grub after install , also just read a post about installation on an External drive apparently the windows mbr can be overwritten so check posts [http://ubuntuforums.org/showthread.php?t=713757](http://ubuntuforums.org/showthread.php?t=713757) look at Julian67 's post. Apart from that i liked mandriva  the mcc is a great idea . Only problem was my computer hung on shutdown .

---

### Post by r76 on 2008-03-03
> **AdamWill said:**
> "The Mandriva forums are not as active as these ones"

Well, I have to read every post to the Mandriva forums and they sure feel active enough to me. =) Not *as* many people as here, it's true, but it's certainly a lively place and there's people who are willing to help with just about any problems.


Sorry Adam :)  What I should have said was "The Mandriva forums are not as active as these ones so don't worry if you don't get an immediate reply - but the quality of replies is very high and you are pretty much guaranteed that Adam will post something really sensible and useful in any given thread".

> **Hallvor said:**
> Too much activity in the forums might not always be a good thing. It may indicate that a lot of people are experiencing problems.  :)

I installed Mandriva spring 2007 on a laptop last year, and it was so easy I didn`t need a forum for anything. The Control Center was also brilliant.

That's my experience of recent Mandriva releases too.  I registered some time ago on the Mandriva forums but never posted anything yet. Perhaps I should - just to say it works and is really good.

It's funny, in the last issue of Microsoft's TechNet magazine there was an article on the last page which said that Microsoft assessed the number of users of various obscure Windows functions by the number of support calls they received i.e. if they got no support calls, they consider the feature is no longer used :roll:

---

### Post by BigSilly on 2008-03-03
I registered on the Mandriva forums just to say thank you to some one who had solved a slight problem with the sound on the ZSNES emulator, but other than that and a slight problem trying to run pSX that's it really. It updated to a newer kernel the other day, and though I was a mite worried because that can cause problems for people, it all went perfectly. 

I can't recommend it enough. It's thoroughly polished, easy to use and nice to look at too. Can anyone tell me why it's not more popular? I just don't get it.  :confused:

---

### Post by djbsteart1 on 2008-03-03
> **BigSilly said:**
> I registered on the Mandriva forums just to say thank you to some one who had solved a slight problem with the sound on the ZSNES emulator, but other than that and a slight problem trying to run pSX that's it really. It updated to a newer kernel the other day, and though I was a mite worried because that can cause problems for people, it all went perfectly. 

I can't recommend it enough. It's thoroughly polished, easy to use and nice to look at too. Can anyone tell me why it's not more popular? I just don't get it.  :confused:

I think it has to something to do with distrowatch saying it costs 49 bucks, and people go why pay for something when there is a free one next to it. It stopped me using it for ages, then I came across one and I really have very few complaints.

---

### Post by Extreme Coder on 2008-03-03
Mandriva is a very no-frills distro ;P

---

### Post by BigSilly on 2008-03-03
As I say, I'm using the 2008 Powerpack version, but it's not really doing anything that Mandriva One 2008 can't do already for free. But I would buy it in future though, no question, to help Mandriva continue. People donate to Ubuntu don't they, and at least if you pay for the Mandriva Powerpack you get some extras. I'll go for a boxed version next time I think, rather than the download.

I do think that it's potentially damaging and often confusing for users when there are multiple versions of a distro around. Look at the confusion around Ubuntu, Kubuntu, and Xubuntu for example. People are going to see the paid for Mandriva and presume it's way better than the free one, which will just put them off altogether as you say, djbsteart1. Really you are paying to support the community, rather than paying for anything "better". 

I'm more than happy to do that personally though. :)

---

### Post by djbsteart1 on 2008-03-03
The only thing in power pack that I can see that is worth have that cannot be got easily is cageda, but then wine is just around the corner so its nothing large. But you do quite rightly say, you are supporting the community. 

Would you care to explain why Mandriva is a no frills distro, it is more frilly than any of the ubuntu varieties on first boot on the live cd or install.

---

### Post by AdamWill on 2008-03-03
mick222: you'll be glad to hear that we added detection of other distributions as a new feature in the upcoming release, 2008 Spring (due in April). :)

---

### Post by AdamWill on 2008-03-03
I tend to assume people know this, but these days I guess it shouldn't be taken for granted, heh. Mandriva actually used to be the most popular distribution - certainly the most popular desktop distribution - up until around 2004-2005 (it was still called Mandrake, at that time). Then two major things happened...

Ubuntu came along, and Novell bought SUSE and made it free. Those two were then giving away stuff that we were still, at the time, charging for (we didn't provide any proprietary stuff for free until Mandriva 2007 came out, while it's always been easy to get stuff like NVIDIA drivers, wireless firmware and Flash for Ubuntu). Ubuntu also did a really good live CD - we actually had a live CD before Ubuntu (Mepis had it first, though), but our first cuts weren't as polished as early Ubuntu releases. And Ubuntu did (and still does) a great job on publicity (of course, having lots of funding for it helps). OpenSUSE had much the same impact at a rather lower level.

Second, we did some releases that had significant problems; 2005 and 2006 both came out with some rather major bugs that never should have been in a release. That didn't help a lot either.

Since 2006 or so we've been focussing on providing everything that people have come to expect to be available for free, improving our publicity, removing all the things that made people get the perception that Mandriva was a 'commercial distribution' (like opening up the Mandriva Club, the forums, the Knowledge Base and so on), and quality control - 2007, 2007 Spring and 2008 all incrementally improved on release quality, they had far fewer and less obvious bugs at release than 2005/2006. Everything takes a long time, but interest in MDV is actually rising steadily again these days.

---

### Post by djbsteart1 on 2008-03-04
> **AdamWill said:**
> I tend to assume people know this, but these days I guess it shouldn't be taken for granted, heh. Mandriva actually used to be the most popular distribution - certainly the most popular desktop distribution - up until around 2004-2005 (it was still called Mandrake, at that time). Then two major things happened...

Ubuntu came along, and Novell bought SUSE and made it free. Those two were then giving away stuff that we were still, at the time, charging for (we didn't provide any proprietary stuff for free until Mandriva 2007 came out, while it's always been easy to get stuff like NVIDIA drivers, wireless firmware and Flash for Ubuntu). Ubuntu also did a really good live CD - we actually had a live CD before Ubuntu (Mepis had it first, though), but our first cuts weren't as polished as early Ubuntu releases. And Ubuntu did (and still does) a great job on publicity (of course, having lots of funding for it helps). OpenSUSE had much the same impact at a rather lower level.

Second, we did some releases that had significant problems; 2005 and 2006 both came out with some rather major bugs that never should have been in a release. That didn't help a lot either.

Since 2006 or so we've been focussing on providing everything that people have come to expect to be available for free, improving our publicity, removing all the things that made people get the perception that Mandriva was a 'commercial distribution' (like opening up the Mandriva Club, the forums, the Knowledge Base and so on), and quality control - 2007, 2007 Spring and 2008 all incrementally improved on release quality, they had far fewer and less obvious bugs at release than 2005/2006. Everything takes a long time, but interest in MDV is actually rising steadily again these days.

Very interesting post, I'm glad to here that interest is increasing  again, you have my support, and I await 2008.1 eagerly. The bug fixes that have been done were very good as I havnt come across one yet.

---

### Post by trmiv on 2008-03-04
I tried Mandriva last night and really liked it.  Very polished and everything works pretty well.  The one thing I couldn't get working in the hour or so I messed with it was the extra buttons on my Logitech MX620 wireless mouse.  Sure the mouse worked, but the foward/back didn't work, and I couldn't get the zoom to do anything.  In Ubuntu I'm using btnx to configure the mouse how I want it.  If I could get my MX620 working the way I want it I'd seriously considering switching to Mandriva as my main distro.

---

### Post by djbsteart1 on 2008-03-04
> **trmiv said:**
> I tried Mandriva last night and really liked it.  Very polished and everything works pretty well.  The one thing I couldn't get working in the hour or so I messed with it was the extra buttons on my Logitech MX620 wireless mouse.  Sure the mouse worked, but the foward/back didn't work, and I couldn't get the zoom to do anything.  In Ubuntu I'm using btnx to configure the mouse how I want it.  If I could get my MX620 working the way I want it I'd seriously considering switching to Mandriva as my main distro.

Try the mandriva forums, I am sure that there will be something there.

---

### Post by AdamWill on 2008-03-04
trmiv: try this. Edit /etc/X11/imwheel/startup.conf and change the second line - where it says imwheel.generic (probably), change it to imwheelrc.MX500. Then restart X. Does that help? If not, you can try imwheelrc.MX700 or imwheelrc.MX1000. If any of them work, let me know, and also give the output of:

lsusb

and I can file a bug and hopefully get it autodetected in future.

---

