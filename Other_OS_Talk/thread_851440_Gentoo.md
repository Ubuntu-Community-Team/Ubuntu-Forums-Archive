---
title: "Gentoo"
date: 2008-07-06
forum: Other OS Talk
---

### Post by Naiki Muliaina on 2008-07-06
Untill recently ive had 2 hard drives in my PC (120 gig and 320 gig) one with windows and one with Ubuntu. Over the last 2-3 years ive moved more and more onto Ubuntu and linux in general. Ive now acquired a naffy 40 gig hard drive that im going to plonk windows XP on. I only use it for Guildwars and Open University stuff.

Ive been having a nosey around forums wondering what to put on my 120 gig hard drive and ive read a few times Gentoo is realy good, realy different, and is great for gaming. Infact i havent seen anyone say anything bad about Gentoo on the Ubuntu forum. The thing is, i also havent read why Gentoo is so good, so different, and good for gaming. 

I had a nosey on the Gentoo website and it looks, well, not os 'proffesional' as Ubuntu (does that makes sense? cant think of the right word :-( ). So im curious to know what specificaly makes Gentoo so good everybody likes it? :-)

---

### Post by wolfen69 on 2008-07-06
if your video card/driver works well with ubuntu and gentoo, there probably wont be much difference, as the same games are available. if you are going to use gentoo, i hope you have ALOT of patience. i know it's not for me. i like to use my computer instead of waiting hours for stuff to compile.

---

### Post by tamoneya on 2008-07-06
I definately agree with the patience recommendation and would like to add that currently is a fairly nice time to switch they just(today) came out with a new release 2008.0.  Also what you can do if you are still doubting it is that you could run it inside virtualbox or vmware just to give it a test spin.

---

### Post by Naiki Muliaina on 2008-07-07
Thanks for the replys :-) I have one more question, hope you folks can awnser it :-)

Like i say my switch to linux has been up to 3 years in the making. Ive tried Ubuntu and Mandriva in the past which, although not always stable, have been pretty straight forward dummy proof distros.

I want to stick with Ubuntu which will stay on my main drive. This secound hard drive is going to be mainly used for playing with other distros, and maybe beta'ing Ubuntu. So, my next question is, is Gentoo for more advanced linux users? Will i learn a bit more about how linux works Gentoo? Ive heard it takes a lot of setting up which got me curious. Is there any other distros around that are good at teaching more advanced stuff? 

On this spare hard drive im quite happy to unplug the other hard drives and crash test stuff as it were. So if an advanced distro means crashing about in terminal a bit messing stuff up thats perfectly fine :-)

---

### Post by tamoneya on 2008-07-07
in my opinion with the exception of linux from scratch ( exactly what it sounds like) gentoo is for the most advanced users.  You compile almost all of your programs from source and you will definitely get a more indepth knowledge of the OS.

---

### Post by Naiki Muliaina on 2008-07-07
Fantastic :-) Thankyou very much for the replys!

---

### Post by mips on 2008-07-07
Have a look at Arch. Yes, I have tried Gentoo before.

---

### Post by Antman on 2008-07-07
Also try Slackware

---

### Post by atomkarinca on 2008-07-07
> **Naiki Muliaina said:**
> ...Is there any other distros around that are good at teaching more advanced stuff?...

You should try Arch. You learn a lot and installation is not as hard as it seem.

---

### Post by MisfitI38 on 2008-07-07
> **tamoneya said:**
> in my opinion with the exception of linux from scratch ( exactly what it sounds like) gentoo is for the most advanced users.  You compile almost all of your programs from source and you will definitely get a more indepth knowledge of the OS.

I respectfully, yet strongly, disagree. 
Using Gentoo will teach one about the 'Gentoo Way' of doing things, with its own brand of idiosyncratic abstraction. 
Portage is merely an automated, (hence abstracted), method of source package management. It really has nothing unique nor in-depth to teach anyone that can be transferred to any other distro. Installing Gentoo involves untarring a stage tarball, followed by compiling and installing the base system and kernel. After that, you configure your USE flags.
This sort of thing really does not offer a laterally useful skill set for any other system, because it is a unique methodology. 
LFS or Arch would offer a more comprehensive system setup, wherein during the installation, you are exposed to the components more intimately. Slackware's installation is highly automated, but is very manual to use, and therefore forces one to rely on and embrace the shell.
LFS, Arch or Slackware would be my suggestions. If you go for LFS, I would also recommend trying the BSD style init in place of sysV. (Instructions available under Hints section)

---

### Post by azza85 on 2008-07-07
I had to use Gentoo in a working environment. It was the first time I had ever used Linux, and was extremely hard to get the hang of. I got by with it, but tried out Kubuntu on a personal laptop. The ease of use, and how everything "just worked" amazed me.  Gentoo may help you learn more about the nitty gritty of using linux, but my personal opinion is it's a pain in the ****! Nothing ever seemed to run smoothly, and once I got one thing working, something else would break.

If you want to do lots of learning, go for it.  Just be prepared to lose a lot of hours on it.  But hey, you may learn something new.

Otherwise, stick to Ubuntu :)

---

### Post by Naiki Muliaina on 2008-07-07
Ahh now this is intresting :) So anything i learn from Gentoo isnt realy applicable elsewhere?

Well, like i said my main hard drive (and main OS) will remain Ubuntu. But now i have a few things to try on the 120 gig one. Well, ill give Gentoo a try to see what its like, then give Arch and Slackware a go. If i can have a little bit of usefull experience from each, im happy :-)

---

### Post by MisfitI38 on 2008-07-07
> **Naiki Muliaina said:**
> Ahh now this is intresting :) So anything i learn from Gentoo isnt realy applicable elsewhere?


Well, you can't quite say that, either. There's plenty of things you can learn, while using Gentoo. 
My perspective is that GNU is GNU and Linux is Linux, so what separates one distro from another is largely the methodology of package management, system configuration, init style, and the presence of a ports system, (or not). 
Gentoo centers largely on the ability to globally define compiling options for your software, and upon the portage system. This is much of 'what makes it Gentoo.'
Neither of these unique methods or procedures thereof are really available outside of Gentoo, which is why I say that learning Gentoo prepares you for, well, Gentoo.
Again, you can learn many things while using Gentoo, (as you can on any distro for that matter) but Gentoo is very unique.
On the other hand, learning something lean, like Slackware, exposes you to a very pure system that you will invariably come to rely upon and become comfortable with, due to the complete lack of abstraction.
Learning apt and Debian will prepare you for any Debian derivative, and there are dozens of those.
(LFS is quite simply the purest of the pure, obviously.)

---

### Post by RedSquirrel on 2008-07-07
> **Naiki Muliaina said:**
> So im curious to know what specificaly makes Gentoo so good everybody likes it? :-)

Well, not everyone likes it, as you have seen. :)

With Gentoo, when you install packages, you build them from source. This allows you to have packages on your system that only support the options you want. This can help make your system faster. You can also build your packages with special compiler options (these may or may not help that much). The Gentoo docs cover this in detail.

When you use binaries that someone else made (e.g., from the Ubuntu repositories), you are stuck with the compiling options they chose. 

Also, I think most Gentoo users build a custom kernel which is suited to their hardware and their needs. That improves system performance.

Gentoo is popular with developers because all of the development packages are installed by default. With Debian-based systems, for example, you have to install these yourself which can be a bit of a nuisance.


> **Naiki Muliaina said:**
> I want to stick with Ubuntu which will stay on my main drive. This secound hard drive is going to be mainly used for playing with other distros, and maybe beta'ing Ubuntu. So, my next question is, is Gentoo for more advanced linux users? Will i learn a bit more about how linux works Gentoo? Ive heard it takes a lot of setting up which got me curious.

Gentoo takes longer to setup than Ubuntu, that's for sure. I suppose a lot of "advanced" users like it because it gives you lots of control over everything. If you like to tinker with your system, Gentoo is great for that. I don't think you have to be an advanced user to use Gentoo (although it doesn't hurt!). You really just have to **read the documentation **and ask questions if you get stuck. [http://forums.gentoo.org](http://forums.gentoo.org)

Be sure to use the manual installation method outlined in the Gentoo Handbook.


> **Naiki Muliaina said:**
> On this spare hard drive im quite happy to unplug the other hard drives and crash test stuff as it were. So if an advanced distro means crashing about in terminal a bit messing stuff up thats perfectly fine :-)

You'll definitely be spending a lot of time on the command line, so it's good that it's perfectly fine with you.


> **Naiki Muliaina said:**
> Ahh now this is intresting :) So anything i learn from Gentoo isnt realy applicable elsewhere?

I don't think that's the case. You will very likely pick up quite a bit from playing with Gentoo. 


> **Naiki Muliaina said:**
> Well, like i said my main hard drive (and main OS) will remain Ubuntu. But now i have a few things to try on the 120 gig one. Well, ill give Gentoo a try to see what its like, then give Arch and Slackware a go. If i can have a little bit of usefull experience from each, im happy :-)

That's a great way to look at it. I'm sure you'll learn quite a bit from trying all those.

---

### Post by cardinals_fan on 2008-07-07
Slackware is awesome and is a great learning experience.  IMHO, Arch won't teach you anything.  I've used (and enjoyed) Arch, but Pacman automates package management so thoroughly that you won't do much exploring with Arch.  NetBSD is educational and fun.

---

### Post by rsambuca on 2008-07-07
I went through a period where I turned into a complete distro whore.  Ubuntu, Debian, Gentoo...  I currently have 7 OS's installed, but now that the novelty has worn off, I am gravitating back to Ubuntu more and more.  I actually like Gentoo quite a bit, and would recommend it highly to you as it sounds like you will pick up a few things.  In the end, just pick one or two or three or four and install them.  Just pre-partition the extra drive so you can install them without getting rid of another one.  You don't have to bother disconnecting any drives as they don't affect each other.

One note for installing Gentoo, if you choose to go that route - [install it from your existing Ubuntu]("http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5") (onto another partition or hard drive, of course).  There is a huge benefit for installing with this method - no computer down time.  You have full use of your computer as normal during the initial compilations, which can take a few hours.  Also, this lets you access the net and the gentoo handbook during the installation so you don't have to print everything out.

Once Gentoo is installed, there really isn't that much difference between it and any other distro. Installing software takes a bit longer, but is only really a factor for huge things like Desktop Environments, or beasts like OpenOffice.  Other than that, most installations take a minute or less.

---

### Post by RedSquirrel on 2008-07-08
I would just like to add that Gentoo provides official binaries for some applications (for example, mozilla-firefox-bin, mozilla-thunderbird-bin, and openoffice-bin).

---

### Post by skintythe1andonly on 2008-07-08
I tried Sabayon for a while, which is a variant of Gentoo and is a good place to start.It is quite easy to install, although it has a lot of proprietary software pre-installed, which may or may not suit you. It does however use portage and in the Gentoo mentality compiles all new packages from source.

---

### Post by Naiki Muliaina on 2008-07-16
1 week later, thought id say an extra thanks after a week of Gentoo. Took me a whole night to install, but i greatly enjoyed using it for a week. It is however not a distro for me to stick with. As far as learning about linux is concerned, like MisfitI38 said, it taught me the Gentoo way of doing things. Playing with terminal is fun and i learnt quite a bit in a week, but i dought ill be taking much with me back to ubuntu :-) 

All the same, nothing ventured, nothing gained :-) Ill be on to Slackware next week :-)

Thanks again everyone!

---

### Post by Cap'n Skyler on 2008-07-16
> **Naiki Muliaina said:**
> Ahh now this is intresting :) So anything i learn from Gentoo isnt realy applicable elsewhere?

Well, like i said my main hard drive (and main OS) will remain Ubuntu. But now i have a few things to try on the 120 gig one. Well, ill give Gentoo a try to see what its like, then give Arch and Slackware a go. If i can have a little bit of usefull experience from each, im happy :-)
sabayon is based on gentoo and it will work right off the dvd :)
their forums are very active and have some brill people on there,but for me and my junk it is just too much to cope with.
now if you like what comes on the live cd or dvd and that suits your uses well,then by all means give it a whirl!
it works awesome,with nvidia and ati drivers included and all the same sort of gnome/kde pidgin etc etc included.
i have NEVER been able to get gentoo to install on anything.
i go thru all the motions and then get a failed to install or some non sense from it,then back to square one and live cd.ugh.
sabayon however did what a live ubuntu cd would do--WORK!!LOL

:popcorn:

---

