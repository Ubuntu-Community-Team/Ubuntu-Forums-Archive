---
title: "The rationale behind Linux software installation philosophy"
date: 2009-09-10
forum: Recurring Discussions
---

### Post by harisund on 2009-09-10
Hey everyone 

See, in Windows, most softwares, even open source ones, the general installation procedure is 
1-> Go to software website
2-> Download software
3-> Run executable file 
4-> Click a couple of nexts
5-> Program found in Start menu. 

Ok, fine, I am not your typical, average user. I understand the flaws behind the above system. Yes, sometimes the software installs additional stuff that you might have to do a "custom install" and uncheck while installing. Sometimes I might have ended up downloading a malware etc unknowingly. 

But still, this is convenient. I am happy knowing I have the latest version of the software, and I am happy knowing I have the version the developers intended. I know all the software files normally reside in C:\Program Files\<software>, generally. 

In most cases, upgrading softwares is as easy as uninstalling them and reinstalling them. Some open source software automatically upgrade too.

Now let's come to the Linux scenario. I have to install only what is in the repository, and I have to install the version modified by the package maintainer for my OS. If I want to remove something, I have no idea what part of it is in \usr\share, what part is in \usr\lib, what part is in \opt whatever. 

Simple examples. Flash. New Windows install, go to a website that requires Flash, you are directed to a link, within seconds you have Flash working. New Linux install, go to a website that requires Flash, Firefox says "Manual installation required". Why is this? Or Sun Java Runtime Environment. 

Or, bigger softwares like OpenOffice. When OOo release a new version on their website, why can't I go to their website, download the latest version and get it on my machine, instead of having to wait till it is in the repository?
 
Is there any Linux that allows this kind of behaviour?

---

### Post by &#32 Greg on 2009-09-10
You can always go for a more up to date distro, such as Debian Sid or Arch Linux, or compile everything from source.

---

### Post by schauerlich on 2009-09-10
[GetDeb](http://www.getdeb.net/) provides something like that. Also, many sites provide a .deb download, such as Opera's. I'm sure there are other examples.

---

### Post by kk0sse54 on 2009-09-10
> **harisund said:**
> 
Or, bigger softwares like OpenOffice. When OOo release a new version on their website, why can't I go to their website, download the latest version and get it on my machine, instead of having to wait till it is in the repository?


You can. Nobody is stopping you.

---

### Post by Jesus_Valdez on 2009-09-10
How come unistall and reinstall something on windows is more rationale that automaticall upgrade in Linux?

You can go to add/remove programs and its a lot easier that the "go to software website" part, wich by the way is the thing you need to do in order to install flash.

Because you know "Manual installation required" normally is:

1-> Go to software website
2-> Download software
3-> Run executable file
4-> Click a couple of nexts
5-> go to youtube
Profit!

I think the point is, there are two different philosophies behind how to manage software under windows and Linux, thats one of the more visible part of "another operative system" part that you are acepting with the change.

---

### Post by Chronon on 2009-09-10
> **harisund said:**
> 
Now let's come to the Linux scenario. I have to install only what is in the repository, and I have to install the version modified by the package maintainer for my OS. If I want to remove something, I have no idea what part of it is in \usr\share, what part is in \usr\lib, what part is in \opt whatever. 


Given that you installed using the repositories, there's no need to go on a scavenger hunt like this.  Telling the package manager to uninstall it will do the job.  You should also be able to view details of the package (in the package manager) and it should tell you which files are located where on your system.

> 
Or, bigger softwares like OpenOffice. When OOo release a new version on their website, why can't I go to their website, download the latest version and get it on my machine, instead of having to wait till it is in the repository?
You *can* do this now: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

---

### Post by earthpigg on 2009-09-10
harisund - plenty of folks developing apps for Linux and/or Ubuntu do just this.

the process you describe was exactly the process by which i downloaded and installed World of Goo, a proprietary video game. (except i paid them $20 first :D .... $20 well spent, great game.)


many do not offer .deb files for ubuntu because **linux users generally do not want to download/install software like this**.

when you install binary software (.exe or .deb) from someone, you are trusting them.

if you only get stuff from ubuntu's repos, you are only trusting ubuntu.

the more people you trust, the more likely you are to end up with malware.



download/install random .deb files if you want - just like a windows user - but please do not act surprised when your system is hosed.

---

### Post by harisund on 2009-09-10
Whoa. Those were some very quick replies !! Let me address them as best as I can > **C!oud said:**
> You can. Nobody is stopping you.

True, true, you are right, I apologize, I should probably rephrase my comment. 

When I install something my own way and need some help with it, and I come to the IRC channel or forums or whatever, everybody seem to say stuff along the lines of "we don't support doing that" or "wait till it becomes available in the repositories and then someone will post a set of commands for you to copy and paste" 

Well, that's not really what I want. I want to find a group of more like minded people. Don't mistake me, Ubuntu is the first distribution I would recommend to any one not familiar with Linux, but it almost feels as if Ubuntu is dumbing it down for the masses (which is a great thing) and that once you want to do anything the non-Ubuntu way, you are on your way, and nobody encourages you to be different. 

> **Jesus_Valdez said:**
> 
I think the point is, there are two different philosophies behind how to manage software under windows and Linux, thats one of the more visible part of "another operative system" part that you are acepting with the change.

ok this I agree with. I guess it's just that I am being more accept-ful of something I am more familiar with and comfortable with. 

> **  Greg said:**
> You can always go for a more up to date distro, such as Debian Sid or Arch Linux, or compile everything from source.

haha, I wish I could do that. For some reason, I have been using ubuntu since its' start (you can see by my join date on these forums) and I just like Ubuntu, but somehow I just feel its only audience is users new to Linux and not users willing to change things around, kind of like Apple

---

### Post by Ric_NYC on 2009-09-10
This is a good site where you can find software and install it with "clicks"...

[www.allmyapps.com](www.allmyapps.com)

---

### Post by harisund on 2009-09-10
> **earthpigg said:**
> 

many do not offer .deb files for ubuntu because **linux users generally do not want to download/install software like this**.
And therein lies the problem. I am not your general Linux user. 

> download/install random .deb files if you want - just like a windows user - but please do not act surprised when your system is hosed.

Now this, I believe is more of a design philosophy. I should be able to install a .deb file as a user and as root. If I install as root, it should install in system wide directories, as usual. If I install as a user, it should install somewhere in my home directory (say /home/$USERNAME/opt) or something, and it should have no potential to hose my system. That's what after all makes Linux so much more powerful, right?

---

### Post by kk0sse54 on 2009-09-10
> **harisund said:**
> Whoa. Those were some very quick replies !! Let me address them as best as I can 

True, true, you are right, I apologize, I should probably rephrase my comment. 

When I install something my own way and need some help with it, and I come to the IRC channel or forums or whatever, everybody seem to say stuff along the lines of "we don't support doing that" or "wait till it becomes available in the repositories and then someone will post a set of commands for you to copy and paste" 

Well, that's not really what I want. I want to find a group of more like minded people. Don't mistake me, Ubuntu is the first distribution I would recommend to any one not familiar with Linux, but it almost feels as if Ubuntu is dumbing it down for the masses (which is a great thing) and that once you want to do anything the non-Ubuntu way, you are on your way, and nobody encourages you to be different. 
In a way I agree with you and it's one of the reasons why I don't use Ubuntu however for Ubuntu's goals I do agree with it's package management. When having a unified package manager  and attempting to present a beginner friendly OS, software quality is absolutely key. This includes using stable software to ensure a pleasant experience without crashings and such. As for deviating from the standard method of package installation, by all means you can do what you want but from a logistic point of view, it's harder to provide support if you're using non standard methods.

> 
haha, I wish I could do that. For some reason, I have been using ubuntu since its' start (you can see by my join date on these forums) and I just like Ubuntu, but somehow I just feel its only audience is users new to Linux and not users willing to change things around, kind of like Apple

It sounds like you might be interested at looking into one of the more up to date distros like Fedora, Sidux, Arch, Gentoo etc etc. Explore around you might find something you like ;)

---

### Post by earthpigg on 2009-09-10
> **harisund said:**
> And therein lies the problem. I am not your general Linux user. 

I should be able to install a .deb file as a user and as root. If I install as root, it should install in system wide directories, as usual. If I install as a user, it should install somewhere in my home directory (say /home/$USERNAME/opt) or something, and it should have no potential to hose my system. That's what after all makes Linux so much more powerful, right?

Actually, i would say Freedom 3, the last of the Four Fundamental Software Freedoms, is what makes linux so powerful:

> Freedom 3: The freedom to improve the program, and release your improvements (and modified versions in general) to the public, so that the whole community benefits.


it _**is**_ possible to have software that will 'install' without you being root. usually its stuff that comes in a .tar.gz with an executable shell script that runs the rest.

you have access to the source code. if you see a .deb that you want to be able to run like that? go for it. 

the only limitation is your own determination.

or, you can write the devs of the specific program you want like that, and request that functionality. or, you can let Ubuntu know how you feel via launchpad and ask for an "install as user" graphical option when you right click a .deb.



heck, you can make your own distribution.


you already realize, of course, why this has not already been done for you:

> **harisund said:**
> And therein lies the problem. I am not your general Linux user. 

if only 1% of the Linux user-base wants this functionality, and **_none_** of that 1% are willing to develop it or pay someone else to, then it will not happen.

recall how Linux started: a dude named Linus wanted to run UNIX on his 386. so, he went ahead and built it himself.

im sure many people (say, 1% of UNIX users?) before Linus wanted to run UNIX on their 386, but *none where willing to put forth the effort*.

That little story was inspirational enough for me to cause me to create what is linked in my signature, however humble & doomed to obscurity that project may be.

---

### Post by purgatori on 2009-09-10
I really fail to see what is supposed to be "convenient" about the Windows methodology.  I find trawling websites for programs to be tedious, as is having to check whether you've got the latest version, and then going through a not-always-so-smooth upgrade process, when I could accomplish all of that with one or two commands from the terminal. Having used both Windows and Linux extensively, I definitely know which approach I find more efficient and convenient.

---

### Post by aysiu on 2009-09-10
> **purgatori said:**
> I really fail to see what is supposed to be "convenient" about the Windows methodology.  I find trawling websites for programs to be tedious, as is having to check whether you've got the latest version, and then going through a not-always-so-smooth upgrade process, when I could accomplish all of that with one or two commands from the terminal. Having used both Windows and Linux extensively, I definitely know which approach I find more efficient and convenient.
I'm with purgatori on this.

I've seen only Windows power users as the ones who want to download from websites and get the latest versions of software on release day.

---

### Post by Whiffle on 2009-09-10
> **purgatori said:**
> I really fail to see what is supposed to be "convenient" about the Windows methodology.  I find trawling websites for programs to be tedious, as is having to check whether you've got the latest version, and then going through a not-always-so-smooth upgrade process, when I could accomplish all of that with one or two commands from the terminal. Having used both Windows and Linux extensively, I definitely know which approach I find more efficient and convenient.

Ditto.  Usually when I install apps on windows, I install, and then just use them until I reinstall.  I never make an effort to go down the list and check that everything is up to date. 

And there isn't any reason you can't do almost the same thing in linux as you do in windows.  With a little creative unpacking, most apps can be run from a user's home directory.  

And why do people always get all riled up about not knowing where the files go?  Who cares?  They go where they need to go, and I honestly can't remember the last time on linux I had to find a file from application X for any reason...package manager installs them, and removes them when the time comes.  easy as pie.

---

### Post by Chronon on 2009-09-10
> **Whiffle said:**
> 
And why do people always get all riled up about not knowing where the files go?  Who cares?  They go where they need to go, and I honestly can't remember the last time on linux I had to find a file from application X for any reason...package manager installs them, and removes them when the time comes.  easy as pie.

I don't know either.  Your package manager knows where each file is located if you care to ask it.

---

### Post by SunnyRabbiera on 2009-09-10
Why dont we just switch to .exe to shut everyone up, other then the obvious...

ARGH, Linux package management is fine... I dont get crap like this

---

