---
title: "Have these projects already been undertaken?"
date: 2006-08-07
forum: Programming Talk
---

### Post by H.E. Pennypacker on 2006-08-07
Before I do anything "major" (I should laugh at myself for saying something like that being a Python newbie), I wanted to know if someone already had done something like the following programs I wanted to create in Python.  It would be a waste of time to duplicate someoneelse's work if that work has already been done under GNU GPL.

1.  I was thinking of something that would automate the following commonly used commands for compiling source pacakges.  A. ./configure. B. Make. C. checkinstall.  Instead of asking a Linux beginner to open up the terminal every time, what if a beginner simply right-clicked on an executable and selected "Compile."  This program would then just do then automate these commands (./configure, make, checkinstall).  There would be a GUI with step-by-step instructions so that a beginner would never know what was going on (not willing to compromise on this - the beginner should not know what's happening).  

2.  I want something similar to Windows' "Desktop Properties."  It would bring together just about everything related to the desktop in one place.  Check out this picture for an example:

[http://www.optimizingpc.com/i/i/bb2.gif](http://www.optimizingpc.com/i/i/bb2.gif)

Please let me know if these two have already been done.

---

### Post by simonn on 2006-08-07
> **H.E. Pennypacker said:**
> 
1.  I was thinking of something that would automate the following commonly used commands for compiling source pacakges. ...


This is why god invented packages. 

If a newbie **NEEDS** to compile from source (extraordinarily unlikely in Ubuntu*) then she/he (oh how PC of me!) should know or be prepared to learn what they are doing. 

Once you start compiling from source you are stepping away from the distribution so should be able to support yourself to a certain extent.

Half the messes I see on this board were created because people do not use the repositories correctly.

Also, not every software package uses autotools.

*What are people compiling from source (genuine question)? The only things I have needed to compile from source are plptools, rdiff-backup and denyhosts. A quick search has revealed that plptools and rdiff-backup are now in the repositories though. Yes, I can play pretty much any media format in MPlayer, Totem, Xine, VLC and XMMS.

---

### Post by 23meg on 2006-08-07
1. AFAIK not undertaken, and there's perhaps good reason: if a compilation process is indeed as easy as ./configure, make, checkinstall, that is, if autotools are used, the build environment is OK and all build dependencies are satisfied (unlikely if the user is compiling from source just to get a newer version of a program), does it really need to be simplified any further? If yes, it can be done very easily, even with a bash script and Zenity. If the process isn't that easy, and it usually isn't, then the software would also have to satisfy build dependencies (how? from which trusted repository?) and things get more complicated.

2. Your screenshot is of "Display Properties" rather than "Desktop Properties"; it brings together more or less everything related to *display *rather than the desktop. I'm not sure where you draw the lines that define "the desktop" so I can't be of much help there, but both GNOME and XFCE already have quite sensible GUIs for this kind of task.

---

### Post by x64Jimbo on 2006-08-07
I have to agree. Compiling from source is often not advisable for a newbie. I like the idea, and I think this theoretical program you're proposing (ironically) should only be able to be compiled from source so that from that point on, experts could skip the compiling hassle. Sort of like the special pair of scissors that are designed to open really tough plastic packages, but that actually come in a really tough plastic package. "The last program you'll ever have to compile from source" if you will. :)

---

### Post by Note360 on 2006-08-07
The Idea is good for some one like me. I am forced to compile every waking hour of my life and I would love it if all I had to do was hit a button and everything would compile (instead of waiting). 

Just to note I am a PPC user so compiling is a daily task even on Ubuntu especially since I love bleeding edge software on Dapper.

Oh and I would love to help with the compiling thing that wouldnt be to hard would it?


EDIT:

Noice Seinfeld related name H.E. Pennypacker

---

### Post by toojays on 2006-08-08
Some of the automatic compiling thing has been done in this project: [http://kconfigure.sourceforge.net/](http://kconfigure.sourceforge.net/)

---

### Post by rupert on 2006-08-08
well there is sourceinstall [http://www.gnu.org/software/sourceinstall/](http://www.gnu.org/software/sourceinstall/) it doesnt create a .deb package, but it great for managing self compiled software, i similiar tool is on gnomefile.org, but i cant remember the right name.

---

### Post by x64Jimbo on 2006-08-08
Oh now that is sweet, toojays! If I ever get to the point where I have to compile from source, you can bet I'll be looking at this. Thanks for the link. rupert, your link is interesting as well. I'll have to keep these in mind. I (heart) these forums. :)

---

### Post by ember on 2006-08-08
Point 2 has been solved on SLED 10 (which I tried yesterday). You can adjust your desktop properties as you do on Windows.

---

### Post by H.E. Pennypacker on 2006-08-09
> This is why god invented packages. 

If only we could find distro-specific packages everywhere.  This proposition is for when you can't find packages.

> 
If a newbie NEEDS to compile from source (extraordinarily unlikely in Ubuntu*) then she/he (oh how PC of me!) should know or be prepared to learn what they are doing.


If life required learning everything, we'd all be wasting a lot of time.  We need most stuff done for us so we don't have to do it ourselves.   A newbie should not have to know what compiling software is.

> Once you start compiling from source you are stepping away from the distribution so should be able to support yourself to a certain extent.

If someone has a busy life, why add more to that life?  It should make sense that everything should be easy.

> *What are people compiling from source (genuine question)? 

I am a regularl average Ubuntu user, and I seem to need to compile software almost on a daily basis.  For example, I wanted to switch to GBrowser (the file manager), but there is no .DEB; just the source.  This happens a lot to me...not being able to find a package.

> does it really need to be simplified any further?

Most definitely.  It is very difficult as it is.

> then the software would also have to satisfy build dependencies (how? from which trusted repository?)

This obsession with trusted repositories is weird, at least in my opinion.  Linux users have this need to trust just about every source they download software from.  Coming from a Windows background, none of this makes sense that much, and it was never that important.  With Windows, I'd search any website, and download packages without necessarily confirming whether the website was safe to use or not.

I wish to bring some of this "I don't care about safety" mentality to Linux.  I know this upsets a lot of people, but safety is not all that important.  

> both GNOME and XFCE already have quite sensible GUIs for this kind of task.

There are different tools but there is no single tool bringing everything together.

> Noice Seinfeld related name H.E. Pennypacker

Yeah, it is from Seinfeld. :)

toojays and rupert, thanks.

> Point 2 has been solved on SLED 10 (which I tried yesterday). You can adjust your desktop properties as you do on Windows.

I have Gnome's version of SLED 10, but there's nothing like Display Properties.

---

### Post by simonn on 2006-08-09
> **H.E. Pennypacker said:**
> If only we could find distro-specific packages everywhere.  This proposition is for when you can't find packages.

Clearly. However, I would argue that there is not a lot that is not in a repositories that a newbie needs, please cite some examples.

> If life required learning everything, we'd all be wasting a lot of time.  We need most stuff done for us so we don't have to do it ourselves.   A newbie should not have to know what compiling software is.

I agree. I do not think a newbie needs to compile ANYTHING with Ubuntu.

A newbie will more than likely end up in dependency hell anyway if they try. Loads do for stuff they could simply download from a repository anyway, just read these forums.

> I am a regularl average Ubuntu user, and I seem to need to compile software almost on a daily basis.  For example, I wanted to switch to GBrowser (the file manager), but there is no .DEB; just the source.  This happens a lot to me...not being able to find a package.

So one package which provides some of the functionality already available in the distro by default?

> Most definitely.  It is very difficult as it is.

./configure && make && make install is not difficult. 

Finding the dependencies usually is for the target audience. Do you plan also to set up a repository of source code as well? This is what you would need to do. If this is the case, why not just contribute to the ubuntu package base for the one or two packages that you think are missing?

Seriously, I would suggest you become more familiar with linux and autotools in particular - you should know all this stuff before trying to improve it. Autotools is more complicated than you think it needs to be for a reason.

> This obsession with trusted repositories is weird, at least in my opinion.  Linux users have this need to trust just about every source they download software from.  Coming from a Windows background, none of this makes sense that much, and it was never that important.  With Windows, I'd search any website, and download packages without necessarily confirming whether the website was safe to use or not.

I wish to bring some of this "I don't care about safety" mentality to Linux.  I know this upsets a lot of people, but safety is not all that important. 

[shocked stunned look] I would suggest that your opinion is f&c*e^H^H^H^H^Hmisguided, particularily for a budding developer.

It is not about safety per se. 

Windows is a bit like a single distro. To a large degree you can expect important libraries and the kernel to behave the same way, configuration information to be in the same place and guarantee them to be binary compatible on all installations. 

The same is not true of linux. The above can be vastly different from distro to distro. (On a side note this is the reason why closed source commercial software companies have a hard time supporting their products on "linux"). 

You almost have to treat an individual distro as it's own operating system compared to another distro, much like you would think of say windows 2000 compared windows XP or windows 98 etc etc, but often with more incompatibilities.

This is why different distros (and even different versions of distros) have different repos. 3rd party repositories are the cause of the RPM "hell" that many people experience in the redhat world (package management software does the same thing, particularily dpkg and rpm). Ubuntu does not have this problem because there are very few 3rd party repositories (and none that I know of with conficting packages). This is a good thing.

---

### Post by MetalMusicAddict on 2006-08-09
> **H.E. Pennypacker said:**
> This obsession with trusted repositories is weird, at least in my opinion.  Linux users have this need to trust just about every source they download software from.  Coming from a Windows background, none of this makes sense that much, and it was never that important.  With Windows, I'd search any website, and download packages without necessarily confirming whether the website was safe to use or not.

I wish to bring some of this "I don't care about safety" mentality to Linux.  I know this upsets a lot of people, but safety is not all that important.

This is why virus's/spyware are rampant in windows.

I like being able to trust a repo. I scanned everything I downloaded in windows. I surely dont miss that.

---

### Post by lefty.crupps on 2006-08-09
Pennypacker you magnificent bastard!  Go for it.  Even if it had been done before, if you are learning PHP this sounds like a good excersize and will help you to refine your skills as you learn what works and what doesn't.  Both ideas sound great, and until SLED programs are in the Ubuntu repositories, I'd say that second one would be mighty useful! (KDE/Kubuntu 6.06 has a pretty good setup now, but still too far-flung in the System Settings).

Xubuntu would really benefit from the second idea.  The Xubuntu Settings menu has the following selections, each two clicks down from the Applications menu (three clicks total; it gets frustrating trying to find a setting in these options):
   Desktop Settings
   User Interface Settings
   Window Manager Settings
   Window Manager Tweaks
   Workspaces Settings
And almost all of them have two tabs across the top.  There could be a great demand for one Xubuntu Settings application that would list each of these on the left with their respective settings on the right side, ever updating as i select a new option...  almost sounds as nice as KDE ;)

---

### Post by David Marrs on 2006-08-10
> **simonn said:**
> 
*What are people compiling from source (genuine question)?
New releases that I'm not prepared to wait up to 6 months for. I've got the backports repo enabled but I never seem to get updates through it.

---

### Post by David Marrs on 2006-08-10
> **H.E. Pennypacker said:**
> > If only we could find distro-specific packages everywhere.  This proposition is for when you can't find packages.

If life required learning everything, we'd all be wasting a lot of time.  We need most stuff done for us so we don't have to do it ourselves.   A newbie should not have to know what compiling software is.
But the point is a valid one. Packages exist because compiling is hard. If a newbie needs to compile software then he's got some barriers to overcome and there's not very much that can be done about it.

A better idea is platform agnostic package mangement, such as autopackage (which is really good, btw). That also requires distro-wide standardisation so that things like dynamic libraries can be guaranteed to be in the same directory across platforms, for example. I believe this is what the linux standards base is about. But autopackage also has adoption problems and is unsuitable for python apps.

---

### Post by Note360 on 2006-08-10
> **H.E. Pennypacker said:**
> Before I do anything "major" (I should laugh at myself for saying something like that being a Python newbie), I wanted to know if someone already had done something like the following programs I wanted to create in Python.  It would be a waste of time to duplicate someoneelse's work if that work has already been done under GNU GPL.

1.  I was thinking of something that would automate the following commonly used commands for compiling source pacakges.  A. ./configure. B. Make. C. checkinstall.  Instead of asking a Linux beginner to open up the terminal every time, what if a beginner simply right-clicked on an executable and selected "Compile."  This program would then just do then automate these commands (./configure, make, checkinstall).  There would be a GUI with step-by-step instructions so that a beginner would never know what was going on (not willing to compromise on this - the beginner should not know what's happening).  

2.  I want something similar to Windows' "Desktop Properties."  It would bring together just about everything related to the desktop in one place.  Check out this picture for an example:

[http://www.optimizingpc.com/i/i/bb2.gif](http://www.optimizingpc.com/i/i/bb2.gif)

Please let me know if these two have already been done.

Thats where I got the idea. I got the name from Ubuntu System Panel Since I work so closly with those guys actually chanders helped me debug it. I could change the name, but I kinda like it. I could call it 

Linux Easy Compiler (LEC)
Debian Easy Compiler (DEC)
Easy Compiler (EC)

---

