---
title: "Switching OS. Advice?"
date: 2008-02-05
forum: Other OS Talk
---

### Post by Lung on 2008-02-05
I have decided to switch to a linux based OS from Windows. I have never used unix/linux before and need some advice.

1)
I am an beginning level programmer, and would like to know what kind of software/IDE's/environments are available for programing (C/C++, OOD, SQL, JScript etc.) i will mainly be working on simple mathamatical based code for sound editing/production/sequencing. 

2)
I would like to exlore the linux kernel, just to start familiarizing my self with how an OS runs and start reasearching it for a future class in linux/unix, and would like to know if Ubuntu is a good candidate for this. 

3)
I will also be using it for sound design and music production. I have looked into Ubuntu Studio, but have trouble seeing why i should choose Ubuntu, Ubuntu Studio, or any other Linux based OS.

thank you!

---

### Post by justin whitaker on 2008-02-05
> **Lung said:**
> I have decided to switch to a linux based OS from Windows. I have never used unix/linux before and need some advice.

Welcome to the dark side! :)

> 1)
I am an beginning level programmer, and would like to know what kind of software/IDE's/environments are available for programing (C/C++, OOD, SQL, JScript etc.) i will mainly be working on simple mathamatical based code for sound editing/production/sequencing. 

I am not a programmer, but it seems like there are alot of tools available to programmers on Linux. You have tons of multi-language IDEs, from Eclipse to Ajunta, with many language specific IDEs as well. 

For sound production, C sound, Pure Data, and a bunch of other programmatic music representation languages are available natively.

> 2)
I would like to exlore the linux kernel, just to start familiarizing my self with how an OS runs and start reasearching it for a future class in linux/unix, and would like to know if Ubuntu is a good candidate for this. 

The source is available, and you can explore it all you like. So yes, it is a good candidate.

> 3)
I will also be using it for sound design and music production. I have looked into Ubuntu Studio, but have trouble seeing why i should choose Ubuntu, Ubuntu Studio, or any other Linux based OS.

Ah, this is the rub. Really, it comes down to flexibility. With Linux, all the code is available for you to see and manipulate. You can do what you like with  it. 

The sacrifice you make is that many music production tools that are standard operating procedure on Windows or OSX will not run, at least, not natively. 

That said, many of the audio production tools are quite good, such as Ardour, and keep getting better. 

The core difference, then, is do you want free and open, or closed and....well, you can't say that Windows isn't capable. 

As for your last question, the difference between Linux distributions are minimal really. You get down to what package management system the distribution uses before you really start to see any tangible difference. 

The difference between something like Ubuntu and Ubuntu Studio is that all of the production tools you are likely to need are included by default. It saves you a bit of time. They use the same code base though, so that is the only difference.

---

### Post by VCSkier on 2008-02-06
Ubuntu is an excellent distribution for several reasons.
[LIST]
[*]It is a great balance (for most people) of stability and cutting edge software
[*]It has a huge selection of available packages that are all high quality, accessible, and ready to go with just a couple clicks
[*]It is well supported, allowing for smooth upgrades between releases, switching entire DE's relatively easily, and other niceties
[*]It's well tested because so many people use it
[*]It's got a great (huge) community and documentation
[*]It's pretty well polished and nice looking as well
[/LIST]
So you'll certainly have access to whatever you need for developting.

Another distribution that may be of interest to you would be Arch Linux.  It takes a bit more work to get it set up and running, because you basically build it from the ground up, by installing most of the system piece by piece.  It teaches you alot, and it's not too hard because there's excellent documentation.

---

### Post by mivo on 2008-02-06
> **Lung said:**
> I would like to exlore the linux kernel, just to start familiarizing my self with how an OS runs and start reasearching it for a future class in linux/unix, and would like to know if Ubuntu is a good candidate for this. 

Ubuntu is as good as any distro for this, though it is not the best "tinker" distro. I'd definitely go with Arch for the tinkering. :)  For kernel stuff, the best starting point is this site: [http://kernelnewbies.org/](http://kernelnewbies.org/)

---

### Post by lespaul_rentals on 2008-02-06
> **Lung said:**
> 1)
I am an beginning level programmer, and would like to know what kind of software/IDE's/environments are available for programing (C/C++, OOD, SQL, JScript etc.) i will mainly be working on simple mathamatical based code for sound editing/production/sequencing. 


Linux is a programmer's dream.  Python, Perl, Ruby, C, C++...so many programming languages are supported.  It was a fair PITA for me to try to run C++ scripts in Windows (I'm not a serious programmer but I run scripts) but with Linux, just run it through **gcc**.

> **Lung said:**
> 2)
I would like to exlore the linux kernel, just to start familiarizing my self with how an OS runs and start reasearching it for a future class in linux/unix, and would like to know if Ubuntu is a good candidate for this. 

Yes.  Slackware or Arch are my recommendations if you want a deep immersion into the waters of Linux.  You might want to start with Ubuntu, though, to get started gradually.  Then, try either Slackware or Arch.

> **Lung said:**
> 
3)
I will also be using it for sound design and music production. I have looked into Ubuntu Studio, but have trouble seeing why i should choose Ubuntu, Ubuntu Studio, or any other Linux based OS.

thank you!

I'm not going to sugarcoat it...I have bad luck with Linux and music.  There are very few applications out there that work as well as their Windows counterparts.

I like your willingness to learn and your desire for knowlege!  Keep it up, mate!  :)  Welcome to the forums.

---

### Post by pieisgood4589 on 2008-02-06
I believe Fedora will be the perfect distro for you, if not Debian.

---

### Post by DUDE_2000 on 2008-02-07
For learning about the linux kernel: [Linux From Scratch]("http://www.linuxfromscratch.org/")

---

### Post by sujoy on 2008-02-07
i think for programming, fedora is more suitable or you may as well try out openSuse

---

### Post by Bungo Pony on 2008-02-07
> I'm not going to sugarcoat it...I have bad luck with Linux and music. There are very few applications out there that work as well as their Windows counterparts.

It has it's positives and negatives from what I've experienced. Jack Audio Control is great (if you have a sound card that will agree with it). It's like using audio software as stereo components - you can hook them together any way you like. Audacity isn't a bad piece of software for recording and editing, but it's also available for Windows. Hydrogen is by far the best free drum simulator I've used.

The downsides are the "audio components", as there isn't much choice for alternatives. You're basically stuck with what you get, and you have to attach all these programs together to perform simple tasks that could easily be performed in one piece of Windows software.

On the plus side, I've been able to get some Windows audio softare to work with Wine. CDex and EAC are great audio extractors and MP3 converters that work well in Wine (if you have a CD or DVD drive that agrees with them). I've also been able to get Creative Wave Studio and Multitrack Studio to both run in Wine. Another bonus is you can attach Windows software running in Wine to the Jack audio control, so they can be integrated with Linux audio software.

On the downside of Wine, it can take a bit of tinkering to get a piece of Windows software to work in it, and that's if it will even work at all.

I'm also afraid that CD and DVD burning is a bit of a chore in Linux as well. Most people will suggest using K3B, but I can't get that damned thing to work without crashing in UbuntuStudio, thus I'm stuck with the burner integrated into Nautilus. I have yet to try other burning software (possibly Windows software such as CDRWin in Wine.)

---

### Post by Midwest-Linux on 2008-02-07
I would go with Linux Mint 4.0 , its based from Ubuntu 7.10 but has the capability to do audio and video streaming out of the box and the driver support is very good. IMO its the best Linux distro out there.

---

