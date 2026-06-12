---
title: "Programming"
date: 2006-07-30
forum: Programming Talk
---

### Post by miller0521 on 2006-07-30
Ubuntu says it is Linux for Human Beings, so I am wondering if it is still useful for a person such as myself who does alot of development. I write lots of programs in C, C++ and Java... and then web programming as well... is Ubuntu able to do all of that? Or no?

---

### Post by VirtuAlex on 2006-07-30
What do you think all this software is written under windows?

---

### Post by miller0521 on 2006-07-30
I know that the first time I installed Ubuntu and tried to compile something with gcc it wasn't avaiable. I am not use to a Linux distro not having development tools by deafult, so I wonder if its ever avaiable for Ubuntu. Or is Ubuntu simply for people who want a 'Desktop OS'

---

### Post by 23meg on 2006-07-30
```
sudo apt-get install build-essential
```will give you GCC.

---

### Post by tseliot on 2006-07-31
moved to a more appropriate section

---

### Post by thumper on 2006-07-31
Yes, ubuntu and derivatives is perfectly fine for doing development in.

I has packages for almost every language you could possibly want to develop in.

The decision to not have gcc by default was not made to say that ubuntu wasn't available as a platform for development, but to not dump packages on a user who won't program.

---

### Post by X.Cyclop on 2006-07-31
> is Ubuntu able to do all of that? Or no?
Yes, why not?:p 

Install Gcc and an IDE (Code::Blocks, Eclipse).;)

---

### Post by miller0521 on 2006-07-31
So java is supported? Is it done using Sun JRE ?

---

### Post by VirtuAlex on 2006-07-31
Yes. [https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html](https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html)

---

### Post by X.Cyclop on 2006-07-31
> **miller0521 said:**
> So java is supported? 
Yes.

> Is it done using Sun JRE ?
I'd use an IDE, Eclipse.;)

---

### Post by Lord Illidan on 2006-07-31
As an aside, you might also want to improve your attitude. I got the feeling you were a bit rude in your initial posts.

Also, try anjuta and kdevelop, two good C/C++ IDEs.

---

### Post by miller0521 on 2006-07-31
> **Lord Illidan said:**
> As an aside, you might also want to improve your attitude. I got the feeling you were a bit rude in your initial posts.

Also, try anjuta and kdevelop, two good C/C++ IDEs.

I'm sorry you got the feeling I was rude in my initial posts. That was no my intention, I've used Ubuntu before, but left it for Debian because it seemed to me that Ubuntu wasn't really designed for developers. So I am simply just trying to figure out the facts. Because Ubuntu does seem to stay more up to date than Debian, though less packages I guess? Anyways, sorry you got the wrong impression!

---

### Post by Lord Illidan on 2006-07-31
> **miller0521 said:**
> I'm sorry you got the feeling I was rude in my initial posts. That was no my intention, I've used Ubuntu before, but left it for Debian because it seemed to me that Ubuntu wasn't really designed for developers. So I am simply just trying to figure out the facts. Because Ubuntu does seem to stay more up to date than Debian, though less packages I guess? Anyways, sorry you got the wrong impression!

Ok, no offense meant or taken :D
Ubuntu **is **more up to date, partly because it uses the unstable version. Also, unlike the Debian devs, we do not port to exotic architectures like ARM, etc. We prefer to stay focused around x86 and ppc.

There are less packages, but not very much. At last count, there are around 17,000 packages (if you include universe and multiverse).

---

### Post by miller0521 on 2006-07-31
> **Lord Illidan said:**
> Ok, no offense meant or taken :D
Ubuntu **is **more up to date, partly because it uses the unstable version. Also, unlike the Debian devs, we do not port to exotic architectures like ARM, etc. We prefer to stay focused around x86 and ppc.

There are less packages, but not very much. At last count, there are around 17,000 packages (if you include universe and multiverse).

Thanks for the discussion, this has been a great help. Here is the dilema I am trying to figure out. I have tested Ubuntu and Debian, I thought Ubuntu didn't have the ability to compile programs and use java etc, however I was wrong about that, I see that I need build-essential, and then follow the wiki on installing java.  I want a distro that just works desktop wise out of the box, meaning networking works.. my other hard drives are mounted etc etc. Easy to install my TTF into, and as up to date as possible yet steering clear of OS crippling bugs. 

My personal opinion is that if I want a distro that I have to tinker around with to get things working, I'll go with Gentoo, but honestly I don't have the time it takes to get everything just right on that distro, though don't get me wrong, it is a nice one. So I am just trying to decide between Debian, and Ubuntu. I don't really like using sudo, I like to log into the DE as root at times, but I think that can be changed in Ubuntu correct? And it won't harm my system? 

Bascially I'm just stuck trying to figure out which is better for me. I'm leaning towards Ubuntu, especially if I can enable the root account. Also, this community just seems quicker to respond to concerns/questions/thoughts etc. 

Thanks for helping
Mitch

---

### Post by Lord Illidan on 2006-07-31
> **miller0521 said:**
> Thanks for the discussion, this has been a great help. Here is the dilema I am trying to figure out. I have tested Ubuntu and Debian, I thought Ubuntu didn't have the ability to compile programs and use java etc, however I was wrong about that, I see that I need build-essential, and then follow the wiki on installing java.  I want a distro that just works desktop wise out of the box, meaning networking works.. my other hard drives are mounted etc etc. Easy to install my TTF into, and as up to date as possible yet steering clear of OS crippling bugs. 

My personal opinion is that if I want a distro that I have to tinker around with to get things working, I'll go with Gentoo, but honestly I don't have the time it takes to get everything just right on that distro, though don't get me wrong, it is a nice one. So I am just trying to decide between Debian, and Ubuntu. I don't really like using sudo, I like to log into the DE as root at times, but I think that can be changed in Ubuntu correct? And it won't harm my system? 

Bascially I'm just stuck trying to figure out which is better for me. I'm leaning towards Ubuntu, especially if I can enable the root account. Also, this community just seems quicker to respond to concerns/questions/thoughts etc. 

Thanks for helping
Mitch

Generally we don't recommend the root account. Sudo is more secure.. What issues do you have with sudo?

---

### Post by miller0521 on 2006-07-31
> **Lord Illidan said:**
> Generally we don't recommend the root account. Sudo is more secure.. What issues do you have with sudo?

My issue with sudo might seem a bit stupid, but once I change a theme in Gnome, everytime I open a 'root' program such as synaptic, the theme is changed back to some really old looking default Gnome theme, like crux or something bad like that. I tried to run gksudo gnome-theme-manager but that tells me that it can't laod gnome-settings-daemon or something like that. So I figure the only way to deal with that, is to log in as root.

---

### Post by Thirsteh on 2006-07-31
Resist the urge for eye-candy. Enabling root and ESPECIALLY logging in as it just to see glamerous details is down-right stupid -- sorry for the colourful choice of words.

In terms of development, Ubuntu is a user-friendly distribution, but remains as hardcore for geeks as most other distributions. If you --want-- to go Gentoo-style for performance, et cetera, Ubuntu won't prevent you from doing that.

I compile a lot, and I sure as well code a lot. I don't remember a single occasion where I couldn't just apt-get the package needed for compiling something. 

You might want to consider installing GCJ, the GNU Java compiler. It's not included in build-essentials because.. well, in my biased opinion, Java programmers should really go check out Python and ditch Java for good :)

I'd take Ubuntu. Then again, biased opinion. Your choice.

---

### Post by VirtuAlex on 2006-07-31
> **miller0521 said:**
> I want a distro that just works desktop wise out of the box, meaning networking works.. my other hard drives are mounted etc etc. Easy to install my TTF into, and as up to date as possible yet steering clear of OS crippling bugs. 

My personal opinion is that if I want a distro that I have to tinker around with to get things working, I'll go with Gentoo
You just described Ubuntu. Gentoo is for control freaks. I do not think installing developer's packages should be considered tinkering and installing them by default is not right thing. Average desctop user is not developer. You may try Suse, it gives you point-and-click interface to choose pograms during installation, but I think it is oversized and slow in comparison to Ubuntu.

---

### Post by Lord Illidan on 2006-07-31
> **VirtuAlex said:**
> You just described Ubuntu. Gentoo is for control freaks. I do not think installing developer's packages should be considered tinkering and installing them by default is not right thing. Average desctop user is not developer. You may try Suse, it gives you point-and-click interface to choose pograms during installation, but I think it is oversized and slow in comparison to Ubuntu.

Amen to that.
Search the forums, there was a howto somewhere where you can make the sudoed apps use the theme you are using. But do not run as root.

I think zenwalk is also good for you, perhaps. I am using it atm, I like it!

---

### Post by VirtuAlex on 2006-07-31
> **miller0521 said:**
> My issue with sudo might seem a bit stupid, but once I change a theme in Gnome, everytime I open a 'root' program such as synaptic, the theme is changed back to some really old looking default Gnome theme, like crux or something bad like that. I tried to run gksudo gnome-theme-manager but that tells me that it can't laod gnome-settings-daemon or something like that. So I figure the only way to deal with that, is to log in as root.
That's not an issue with sudo, it is issue wiht themes in gnome. You probably just "overtinkered" something. Logging in under root in x to improve its visual appearance is inadequate. You should try to open another thread just for this and may be someone will help you to return things back to normal.

---

### Post by X.Cyclop on 2006-07-31
Look at here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo);)

---

### Post by miller0521 on 2006-08-01
> **Lord Illidan said:**
> Amen to that.
Search the forums, there was a howto somewhere where you can make the sudoed apps use the theme you are using. But do not run as root.

I think zenwalk is also good for you, perhaps. I am using it atm, I like it!

Does zenwalk come easily configured for the x server and all that stuff? Like Ubuntu is? And does it have a root account?

---

