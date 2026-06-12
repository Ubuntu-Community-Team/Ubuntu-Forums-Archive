---
title: "Updating programs to newer versions"
date: 2009-08-30
forum: Recurring Discussions
---

### Post by snipazer on 2009-08-30
I've been using Ubuntu on and off for a few years now. I really like it but theres something that really annoys me and I've been meaning to ask why Ubuntu, Linux in general I guess, does this.

In the default Ubuntu 9.04 installation, Firefox 3.0.x is installed, not 3.5. Thats fine. But if I want to upgrade to 3.5, I have to add some PPA lines, which isn't too much of a hassle. But once its installed, its called Shiretoko. I understand that its the codename for the 3.5 build. But my question is, why can't I just update to 3.5 when it comes out with having to jump through some hoops to get a work around? In Windows and Mac (I understand Linux isn't either), you just download and install. Its simple, no hassle. I don't have to think about it. 

Another example would be VLC. The version in the repo's is 0.9.9a. But I want 1.0.0. So I look how to install it. I have to add some PPA lines and import a key. The key doesn't work (I blamed this on VLC, not Ubuntu). But still, why doesn't the update manager just see that I have a later version and just update?

I hear all the time about how cool Linux is because it can update all your programs from one place, but whats the point if you can't get the newer version without some type of work around? I'm not looking to bash Linux, Ubuntu, or anything. I'm just really wondering why we have this system of updating programs...

---

### Post by garvinrick4 on 2009-08-30
In 9.10 it is Firefox 3.5.2   The Shireiko is for 9.04  you can just have both for
a while.  Two different Icons. They keep the same settings. Two for the price of one. 
For all intents and purposes they are both Firefox just one is upgraded. Really do not
know why but must have been some good reason to do this I would imagine. 
     Have a nice day.

---

### Post by snowpine on 2009-08-30
Hi Snipazer, the answer is simple, really... Ubuntu is designed so that major updates are "lumped together" every six months. This makes your system more stable, because all of the applications are "frozen" at versions that are thoroughly tested to work well together. The next big update will be 9.10 Karmic Koala in October, which will include FF3.5, VLC 1.0, and lots of other good stuff.

You can certainly download and install the latest version of Firefox (or any other application) from their website, just as you would in Windows/Mac. I personally prefer to wait until the update reaches the Ubuntu repositories, because I know it is stable, tested, and trusted. I would rather wait until October than have an unstable system.

ps Every Linux distro is different in this regard. If you want the latest apps as soon as they come out, you can use a "rolling release" distro like Arch or Sidux.

---

### Post by raymondh on 2009-08-30
+1 on snowpine's thoughts.

---

### Post by snipazer on 2009-08-30
Hmm, thats an interesting way to look at it. Is there any way to get the updates, before the 6 month release cycle, and without adding PPA lines? I am willing to sacrifice a little stability to have the newer versions of these programs. Thanks for your replies. It really made no sense to me why it worked the way it did.

---

### Post by snowpine on 2009-08-30
> **snipazer said:**
> Hmm, thats an interesting way to look at it. Is there any way to get the updates, before the 6 month release cycle, and without adding PPA lines? I am willing to sacrifice a little stability to have the newer versions of these programs. Thanks for your replies. It really made no sense to me why it worked the way it did.

Adding PPAs is how most of us do it. The advantage of a PPA is it still uses Ubuntu's package management system, so you get dependency checking, updates, etc.

You can also do it the "Windows way" and download straight from the vendor website, for example just grab the latest Firefox from the Mozilla site. 

Linux is all about freedom; there's always more than one way to achieve your goal.

---

### Post by snipazer on 2009-08-30
> **snowpine said:**
> 
Linux is all about freedom; there's always more than one way to achieve your goal.

I guess I might want a little less freedom for simplicity...

---

### Post by snowpine on 2009-08-30
> **snipazer said:**
> I guess I might want a little less freedom for simplicity...

Simplicity means different things to different people. ;) For a lot of Ubuntu users, simplicity means a stable system with one big update every six months. For me, simplicity means a minimalist, rolling-release distro like Arch Linux. Most of us go through a process of experimentation to find the distro that best fits our personal philosophy...

PPAs aren't that hard though, really, and I think they are the best solution for your needs... Here is a good introduction: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

There is also the "backports" repository to consider: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Good luck!

---

### Post by snipazer on 2009-08-30
Oh wow, so what exactly can I do with the backport? Will it allow me to upgrade to 3.5 with the official branding? Not shiretoko I mean.

---

### Post by snowpine on 2009-08-30
> **snipazer said:**
> Oh wow, so what exactly can I do with the backport? Will it allow me to upgrade to 3.5 with the official branding? Not shiretoko I mean.

No, it will still be called Shiretoko. 

Who cares though, really, as long as it is good at browsing web pages. (For that matter, I've yet to find a web site that requires FF3.5.) :)

---

### Post by snipazer on 2009-08-31
> **snowpine said:**
> No, it will still be called Shiretoko. 

Who cares though, really, as long as it is good at browsing web pages. (For that matter, I've yet to find a web site that requires FF3.5.) :)

Thats true, but adblock plus does require 3.5 which is kinda big for me. And you're right, it doesn't really matter to me if Shiretoko is the name. Its just that, isn't the point that Ubuntu is trying to be more user friendly? This doesn't seem like a very user friendly part of the distro. This is obviously just my opinion.

---

### Post by madjr on 2009-08-31
> **snipazer said:**
> Thats true, but adblock plus does require 3.5 which is kinda big for me. And you're right, it doesn't really matter to me if Shiretoko is the name. Its just that, isn't the point that Ubuntu is trying to be more user friendly? This doesn't seem like a very user friendly part of the distro. This is obviously just my opinion.

well the PPA are being integrated to the upcoming "ubuntu software store" (or atleast thats the plan)

if there is a PPA, there's also a .deb package right there you can download freely (in case you want to store the installer)

anyway i am glad we have shiretoko in 9.04

i just upgraded firefox 3.0 to 3.5 in windows vista and many of my extensions still don't work (specially an accessibility extension i need for my low eyesight and that of my dads)... :/

that means i will have to uninstall ff 3.5, go to the mozilla site and redownload ff 3.0 and get things working like before :/

in ubuntu u get to "try" before you buy :) , well i mean try versions alongside before making the jump (mostly for critical software).

yea, it's not a perfect system, but has it's advantages. Also the windows/mac style of packaging are getting more popular (with less security issues), which is a plus.

soon enough we should have enough packages, download sites, ppas, etc for most peoples needs.

in sites like [http://getdeb.net/](http://getdeb.net/) people can also contribute packages not found in the official repos

unfortunately most distros will need to keep the 6 month dev cycle for a while to catch up with proprietary systems. Once the bases are robust enough we can pass to 1 year cycles (or longer) then updated packages should be a lot easier to grab (kinda like mac. and just like any upgrade some software still doesn't work with snow leopard).

FOSS is getting really robust. FF3.0 is too good and i will only upgrade to ff3.5 mostly because of html5. Also i'll be more than happy to wait till karmic. by then all extensions should work and html5 will be more extended.

---

