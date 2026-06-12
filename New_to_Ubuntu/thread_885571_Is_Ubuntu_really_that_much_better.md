---
title: "Is Ubuntu really that much better?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by superduke on 2008-08-10
Well, frankly, like everyone else here I am in complete hatred of windows! I installed ubunto hardy, ubunto studio, kbunto and played with them all. It's really hard to get anything to work like wireless networking and games. I hate dual booting because I have large files that I like to keep on hand and more OS's eat up too much room... I bought a book to help me learn how to make better use of linux but haven't read that much of it yet.

What stopped me from continuing on and figuring the whole thing out was when I tried to copy all of my photos to my new OS. It freezes!!1 Not once, not twice.... everytime! Whenever I try to copy large files it freezes hard! Is this anything like what u guys/gals experience with ubuntu or is it just my Toshiba Satellite A215? I wish I would have known of a laptop that didn't come with vista before I bought this one, or even laptops that come with linux...


I really have a steap learning curve if I want to use this OS I know, but this file copying forced me to leave it for XP black... but now that just bsod'd on me after a fresh install, what the crap!??

---

### Post by hyper_ch on 2008-08-10
is there actually any question for support in that text?

---

### Post by superduke on 2008-08-10
Yeah, it's in there... my apologies for the ramblings...

"Whenever I try to copy large files it freezes hard! Is this anything like what u guys/gals experience with ubuntu or is it just my Toshiba Satellite A215? "

---

### Post by hyper_ch on 2008-08-10
does it freeze immediately or after a while?

---

### Post by superduke on 2008-08-10
It would go for something close to 2-3 munites and then just stop... no matter what the file size(10gig - 100gig) I thought ext2 and ext3 were good stable file systems too, am I wrong? It probably has nothing to do with the file system though, huh?

---

### Post by apdc on 2008-08-10
Hey Superduke!  I feel your frustration.  I am not a computer person and thought that I would try linux as a learning experience and to support this voluntary initiative.  But, I can't seem to do the basic things as i did on windows.  Maybe this sysytem is for an elite type??

---

### Post by hyper_ch on 2008-08-10
(1) install htop
(2) open a terminal an run htop
(3) start copying and what how the processes develop in htop

---

### Post by superduke on 2008-08-10
Yeah, I hate that microsoft has me on this tight leash even though they blow so much... it's just that everything just works on windows...   !!!  I tried to get Gentoo working on a laptop 2 years ago building the kernal from scratch... can u guess how many months I wasted on that and nothing to show for it?? I though something like Ubuntu would be more my skill level, lol!!

---

### Post by superduke on 2008-08-10
htop huh? what exactly does that tool do? Also I still havent fould out how to install anything yet. I don't know the commands well. DOS is no problem for me though, lol... great. I even tried to install unreal tournament and UT2003 and couldn't get them working(games that have native unix support). I must be just horrible with this stuff.

I don't have ubuntu installed right now but I will try it again very soon because I really want to make it work. BTW, would I ever be able to get my fingerprint reader working? I thought it was so badass that my camera worked right after the install!!

---

### Post by spiderbatdad on 2008-08-10
Toshiba hardware doesn't have a reputation as linux friendly. There are workarounds and many people eventually have success running Ubuntu on this model. Random freezes have been reported to be resolved using the kernel boot options: noapic nolapic. Always delete quiet splash.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

To make your boot options permanent you need to edit the file /boot/grub/menu.lst after the installation.

---

### Post by hyper_ch on 2008-08-10
> **superduke said:**
> htop huh? what exactly does that tool do?
Hmmm, you could try to find that out yourself.

> **superduke said:**
> Also I still havent fould out how to install anything yet.
A great resource on installation is the page you find when googling for "monkeyblog install anything ubuntu"

> **superduke said:**
> BTW, would I ever be able to get my fingerprint reader working?
What do you want fingerprint reader for?

---

### Post by superduke on 2008-08-10
Thanks for the advice, I really appreciate any I receive :). Also I just glanced over another thread that says the 64bit ver is known to be jerkey and freezy... Should I try out the i386 32bit versions and would I be losing that much?? I didn't know it would matter.

---

### Post by superduke on 2008-08-10
> **hyper_ch said:**
> What do you want fingerprint reader for?

Convenience... I have a lot of passwords to remember, the less I have the better :)

---

### Post by Horomancer on 2008-08-10
Ubuntu is easy to install new programs on.
The two main ways are through Applications> Add/remove programs (which REALLY works unlike in M$)
and also System> Administration> Synaptic Package Manager which is a little more advanced but has more control than the simpler Add/remove interface.

Go into Add/Remove and do a serach for 'htop'. Make sure that the dropdown window is on 'all available programs'
Then click on the checkbox next to Htop and then click the apply changes button.

To get more things working in Ubuntu i highly recommend you do a search both in the forums and in the ubuntu help files on adding 'repositories' These give you more options on pre compiled programs, codecs, and tools to make linux work better for you.
Hope you figure out what up with your file transfer. I haven't had that problem, but then again i can't get the networking between Ubuntu and Vista to work 100% either.

---

### Post by spiderbatdad on 2008-08-10
> **superduke said:**
> Thanks for the advice, I really appreciate any I receive :). Also I just glanced over another thread that says the 64bit ver is known to be jerkey and freezy... Should I try out the i386 32bit versions and would I be losing that much?? I didn't know it would matter.

My understanding is the 64 bit support has come a long way and is worth installing, but the 32 bit runs fine. I really don't know. Googling that question with the Ubuntu tag should produce a lot of info. I know there are threads here making comparisons...but the forum search tool doesn't work that well for me, so I search google: ubuntu 64bit 32bit...or something like that.

---

### Post by hyper_ch on 2008-08-10
> **superduke said:**
> Convenience... I have a lot of passwords to remember, the less I have the better :)

A fingerprint reader does not really provide any security.

---

### Post by superduke on 2008-08-10
[QUOTE=Horomancer;5559898]Ubuntu is easy to install new programs on.
The two main ways are through Applications> Add/remove programs (which REALLY works unlike in M$)
and also System> Administration> Synaptic Package Manager which is a little more advanced but has more control than the simpler Add/remove interface.

Go into Add/Remove and do a serach for 'htop'. Make sure that the dropdown window is on 'all available programs'
Then click on the checkbox next to Htop and then click the apply changes button.

To get more things working in Ubuntu i highly recommend you do a search both in the forums and in the ubuntu help files on adding 'repositories' These give you more options on pre compiled programs, codecs, and tools to make linux work better for you.[QUOTE]


I did stumble upon the add/remove programs and that was super easy, awsome even. But did little for things that weren't in the list like games I own or wireless drivers so I still have to eventualy learn how to do it myself. I will definatly look into the repositories stuff, sounds like good stuff to know.

---

### Post by superduke on 2008-08-10
> **hyper_ch said:**
> A fingerprint reader does not really provide any security.


Huh, I was unaware of that...




The thing that kills me is that I have to stop and go to bed now, early day tomorrow... I always leave wanting to learn more because i don't get enough time to research everything I want to, argh! Later, thanks for the right directions.

superduke

---

### Post by Elfy on 2008-08-10
This might be of use
[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by bobbob1016 on 2008-08-10
> **hyper_ch said:**
> A fingerprint reader does not really provide any security.

I don't think he wants security, just ease of use.  My guess is most fingerprint programs store your passwords, like roboform, and enter them automatically when you scan your finger.

I think you should look into roboform or something instead of a fingerprint scanner.  It will do the same thing, but you have to enter a password instead of scanning your finger.

---

### Post by Linux&amp;Gsus on 2008-08-10
> **superduke said:**
> Well, frankly, like everyone else here I am in complete hatred of windows!
Well, in a sense I actually love Windows. As long as Windows and OSX together have at least 80%+ market share on the desktop all the malware hackers don't really care too much about Linux. Therefore less to worry about. :biggrin:

> **superduke said:**
> I really have a steap learning curve if I want to use this OS I know...
Linux is a different OS. As with everything new it takes time to learn it. As most people here you probably used Windows for quite some years. Over this period of time you learned a lot and you're now pretty familiar with it. Now you have something different, still a computer, but it works a bit different.
Just hang in there, don't give up. It's doable. I'm the best example, if I can learn it, you can. By no means am I a genius. Patience is probably your best friend, and this forum of course. I consider a forum like this better than any book.
E.g. the copying problem. I sort of doubt that you'll find a solution to that in a book. But someone here will most likely be able to help you.

> **superduke said:**
> htop huh? what exactly does that tool do?
It's something like the Taskmanager in Windows, a System Monitor to see all the running applications, how much RAM they need, CPU usage, etc. This is a tool for the terminal but there is also one with a graphical interface.

> **superduke said:**
> Also I still havent fould out how to install anything yet. DOS is no problem for me though, lol... great.

If you are familiar with DOS then you're not afraid of the command line, I guess. ;)
So, in a Terminal you install apps as follows:
sudo apt-get install <package_name> <package_name> <package_name> ...
"sudo" gives you super user privileges (as in "Administrator" in Windows). You'll be asked for your password but you wont see it as you type, hit <enter> and the app will be downloaded and installed. So, for htop it looks like this:
> sudo apt-get install htop
When it's installed type in the following command and hit <enter>:
> htop
htop is running now, you can stop it when you hit <crtl> + c
Have a look at the following page to see how it looks like:
[http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/](http://www.howtogeek.com/howto/ubuntu/using-htop-to-monitor-system-processes-on-linux/)

---

### Post by hyper_ch on 2008-08-10
htop doesn't need to be run as root. Normally you should not run anything as root.

---

### Post by Linux&amp;Gsus on 2008-08-10
> **hyper_ch said:**
> htop doesn't need to be run as root. Normally you should not run anything as root.

oooooooops :oops:
My bad, changed it...

Cheers.

---

### Post by tjwoosta on 2008-08-10
i just cant resist

i must add my two cents

ubuntu in my opinion is definatly worth the effort

and no it is definatly not only for the elite type
(in my experience ubuntu is actually one of, if not, the single easiest linux distro availible)

if you have used windows your entire life then there is of course going to be a general learning curve before you would feel comfortable with using it as an everyday OS 
(i suggest a dual boot with windows untill you feel comfortable with linux)

i do have to admit that there will be quite a bit of effort required to get everything up and running (drivers etc.)

with windows you pop in the disk and click a few buttons and bam youve got everything all set up

with ubuntu you will probably need to search around for the correct drivers and possibly even need to learn how to compile them before everything is running flawlessly


but in the end, when you have everything all setup, ubuntu will run much smoother and with 1/2 as much bloat and about 1/4 the maintenance as windows 

ubutnu has no need for virus scanning at all and you dont have 14 different programs constantly searching for updates, bogging down your system while your just trying to read the news
(in ubuntu all the programs update all at once, it usually takes about 15 seconds from start to finish compared to vista wich will take about 5 to 10 minutes)

---

### Post by mikewhatever on 2008-08-10
This was a funny post, let the reply be a welcome to the comunuty.


> **superduke said:**
> Is Ubuntu really that much better?

Better then what? Windows, MACOSX, Fedora, Suse, Debian, BSD .............?

> Well, frankly, like everyone else here I am in complete hatred of windows!

I don't hate Windows. This isn't Windows haters forum. Do speak for your self.

> I installed ubunto hardy, ubunto studio, kbunto and played with them all. It's really hard to get anything to work like wireless networking and games. I hate dual booting because I have large files that I like to keep on hand and more OS's eat up too much room... I bought a book to help me learn how to make better use of linux but haven't read that much of it yet.

Ubuntu usually works on supported hardware. It's unfortunate, some vendors don't care to provide support.

> What stopped me from continuing on and figuring the whole thing out was when I tried to copy all of my photos to my new OS. It freezes!!1 Not once, not twice.... everytime! Whenever I try to copy large files it freezes hard! Is this anything like what u guys/gals experience with ubuntu or is it just my Toshiba Satellite A215? I wish I would have known of a laptop that didn't come with vista before I bought this one, or even laptops that come with linux...

I've never experienced the freezes you describe, as for a laptop with Ubuntu, check the link below.
[http://www.dell.com/ubuntu](http://www.dell.com/ubuntu)

---

### Post by Sava8420 on 2008-08-24
> **hyper_ch said:**
> Hmmm, you could try to find that out yourself.


A great resource on installation is the page you find when googling for "monkeyblog install anything ubuntu"


What do you want fingerprint reader for?

Hey man thanks for the link for the "monkeyblog install anything ubuntu"  I've been trying to find a good resource and you have provided it.  Once again Thank You.

---

### Post by RequinB4 on 2008-08-24
I think someone already posted this, but check "how to install anything in ubuntu" in my signature.

Also, if you're having some problems experiencing the difference between windows and ubuntu, remember a few things:

1) "Easy" for most people is not what makes the most logical sense - it is what they are used to - but if an OS isn't different how can it be better?

2) If you click on "Linux is not windows" in my signature, it's a good read on some common issues people may have.

3) Ubuntu may require a little more work to set up, but it is a ONE time thing and very worth it. It's actually much easier to install than Windows, you just don't notice because windows comes pre-installed...

On the OP support question, can you go to system - applications - terminal and try to copy the files manually:

```

cp /home/$USER/path/to/file/file1.txt /home/$USER/

```

This will attempt to copy file1.txt to your home directory.

---

### Post by danny_galaga on 2008-08-24
> **superduke said:**
> Convenience... I have a lot of passwords to remember, the less I have the better :)

boo to fingerprint readers! the less 'the man' knows about me, the better. i remember years ago when they tried to introduce the 'australia card' here, there was an uproar about privacy issues. nowadays, no one thinks twice about having something as private as your fingerprint in some database somewhere for convenience sake...

now about the topic of this thread! im a non-tech type too. but so far i have found ubuntu to be pretty good. it may have helped that my pc is a basic 4 year old HP with onboard everything so i had no issues at all with drivers etc. i must admit the problems i have had dont seem to have any answers, but in time theyll either be resolved or i learn to live without them. i boot into XP maybe once or twice a fortnight now at most. which isnt a bad thing, because it now tries my patience waiting for XP to load up, making me more and more enthusiastic about linux (",)

---

### Post by Perkins on 2008-09-11
You probably don't really need to copy everything onto every OS.  Install the ntfs configuration tool and turn on read-write support for your windows partition.  Then you can just use it where it is.  There are drivers for windows too to let you go the other way, but I haven't used them myself.  Just hit up google for windows ext3 drivers.

As for the fingerprint scanner, the big thing to remember is that, unless you wipe it off after you use it, it's quite likely to have, oh, say, a fingerprint on it...

I've seen instructions for setting them up on previous versions floating around the forums, but the packages they mention have been removed from the repositories.  So since not all types of scanner are supported yet, and since I don't really need mine to work, I'm not spending a lot of effort on figuring it out.

---

### Post by Ntweat on 2008-09-11
well... as some1 said... its community... wel.. 1stly at the question.... i have copied over 20 GB with ubuntu... and over 5GB with live cd boot i never faced any problem the main problem u must facing which i think is that ur ntfs partition must be fragmented ... with ext3 no problem....

secondly... well... i turned over to ubuntu fully cause i wanted to get away from vista....  and its much fater.... now m helping ppl of my college to adopt the same with a localised repo, a newly opened LUG and everything so hoping someday there will be more linux user on my campus than windows... cheers

---

