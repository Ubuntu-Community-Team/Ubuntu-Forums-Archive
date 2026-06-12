---
title: "A place to start"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Nitefang on 2008-09-17
Hi I am very new to Linux, and I am runny Ubuntu 8.04 (Hardy heron I believe). 

 I can tell Ubuntu will be my OS from now on but I can do hardly anything. I have done some basic tweaks to the layout and downloaded a few things I found in a tutorial to flash up my desktop but that's it. 

  What I really need is a list of things a Ubuntu Guru would do if he were installing Ubuntu again.

  What would be some programs I should definitely get. Are there any patches that are very important?
 
 What would be useless programs that come pre-installed that can be removed?

 Is there anyway to install programs that were not made for Ubuntu, or will I need to either repurchase or pirate(I'd rather not) all of the programs I had on Vista?

 Are there any rules that no one should ever do unless they were trying to destroy their computers? Is there anything I need to do?

And if anyone has any tips on using Ubuntu they would be more that welcome.

 I did read the "Start Here Thread" and it was rather helpful but it felt as though it was written by the people who made Ubuntu while I am looking for more of a veteran user aspect.

  Thank you very much.
   The Linux community already looks to be a lot more friendly and helpful than the Windows one.

---

### Post by tuxxy on 2008-09-17
I think you should start at the help guide, then ask more detailed questions once you understand it a little more, your basically asking what programs should I have on my system for the first two questions, we cant answer this

To run windows apps you would need to use WINE or a virtual windows isntallation

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by Nitefang on 2008-09-17
Thank you I'll check it out. If anyone has anymore advice anything would be appreciated.

---

### Post by Tatty on 2008-09-17
> **Nitefang said:**
> What would be some programs I should definitely get. Are there any patches that are very important?
 
 What would be useless programs that come pre-installed that can be removed?


Well that entirely depends on what you want.  Theres no need to install anything unless you need it.  

Likewise a default ubuntu install doesnt tend to come with much junk like a proprietry OS does, so unless you really want to remove default things, theres not much to gain from it.

The only one thing you may need to consider is multimedia support.  Due to lots of legal grey areas, most common multimedia formats are not supported "out of the box" in ubuntu, but they are pretty easy to set up if you want to.

[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)  This page is a good start

> **Nitefang said:**
> 
 Is there anyway to install programs that were not made for Ubuntu, or will I need to either repurchase or pirate(I'd rather not) all of the programs I had on Vista?


Yes and no.  There is an application called Wine which can run windows applications in linux.  However it is not perfect there is no guarentee that software will work in it.  Have a look at the AppDB at the wine website to see if others are managing to run the software you are interested in.

[http://www.winehq.org/](http://www.winehq.org/)

> **Nitefang said:**
> 
 Are there any rules that no one should ever do unless they were trying to destroy their computers? Is there anything I need to do?


Never log in as root.  In Ubuntu it is simply not needed.  This page will explain it to you, and is an important read for a new ubuntu user.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **Nitefang said:**
> 
And if anyone has any tips on using Ubuntu they would be more that welcome.


Read through the official help file posted above by tuxxy.  After you have read the official help (in the 8.04 tab on the page) then the community tab should help you through a great many other things.

Keep an eye on these forums and in the community, because linux is always changing and the community is the best place to learn about it.

---

### Post by Iowan on 2008-09-17
> **Nitefang said:**
>  Are there any patches that are very important?
...

 Are there any rules that no one should ever do unless they were trying to destroy their computers? Is there anything I need to do?

...First, Ubuntu has an Update Manager that (unless you disable it) will periodically inform you of new security, etc., updates.

Second, understand what commands do before you blindly follow them.  There are **man**(ual) pages for most commands. Some, like **sudo rm -rf** can wreck a system if not used very carefully. Read the Announcement at the top of this (Beginner) forum.

---

### Post by Sef on 2008-09-17
If there is something you want to do and can't find an application in Add/Remove (Applications > Add/Remove) or Synaptic (System > Administration > Synaptic Package Manager), then ask us here.

---

### Post by Nitefang on 2008-09-17
Thank you everyone those last three posts were very helpful.

---

### Post by lovinglinux on 2008-09-17
Damn, I was writing a gigantic reply and hit some button I shouldn't hit and were all gone...starting over.

> **Nitefang said:**
>   What I really need is a list of things a Ubuntu Guru would do if he were installing Ubuntu again.

I'm not a Ubuntu guru, since I'm heading towards my first month using it, but I guess I can give you some advice from my experience so far.

A very good way of learning things is reading all posts in this forum and the General Help forum. Save the RSS feed and read them all. You probably won't use all the info posted daily, but this you help you to get familiarized with how things work on Linux. Eventually you will find some thread that explain something really cool that you didn't even know was possible to do.

Be organized. Save posts and tutorials that you might use in the future (Firefox Scrapbook extension will help do that) and subscribe to threads that you want to follow. You can also organize your forum subscriptions in folders. 

If you didn't already is a good idea to [**mount your /home directory in a separate partition**]("http://www.psychocats.net/ubuntu/separatehome"). This will allow you to keep all personal settings after re-installation. Another useful feature available is the ability to save a list of all installed applications, so you can download them all at once again.

> 
To replicate your packages selection on another machine (or restore it if re-installing), you can type 

dpkg --get-selections > ~/my-packages 

move the file "my-packages" to the other machine, and there type 

sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

With a separate /home partition and the list of installed applications you will be able to "restore" your system to practically the same condition before re-installing, with the benefit of a fresh install.

> **Nitefang said:**
>  What would be some programs I should definitely get. Are there any patches that are very important?

Is hard to recommend software if we don't know what you need. I recommend that you first think which ones were very important to you on Windows, then try to find alternatives in the repositories. You will find that all applications in the Add/Remove manager are categorized by popularity, so it's a good start for comparison.Most likely that will find very good alternatives or even better ones. If you don't, then create a new thread here for each kind of application you need. If people know what you are looking for they will help you.

Last case scenario, try to run Windows applications with Wine.

After installing everything you can't live without, then go fishing new stuff. If you have the guts to read a very long list, I recommend [[COLOR="Red"]**this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=382137&highlight=applications").

I guess all updates are important. Anyway, is hard for us newbies to tell if an update is important or not and they won't occupy too much space, so do it if the manager ask you to update.

> **Nitefang said:**
>  What would be useless programs that come pre-installed that can be removed?.

You don't have to remove anything yet. Deleting won't save you too much space and the default programs won't slow down your system if left alone.

> **Nitefang said:**
> Is there anyway to install programs that were not made for Ubuntu, or will I need to either repurchase or pirate(I'd rather not) all of the programs I had on Vista?

I guess already answered this question. You are in the open source software realm now. Try to free yourself from Windows applications, even if the Linux alternatives looks different or work different. Soon you will be very comfortable with them.


> **Nitefang said:**
>  Are there any rules that no one should ever do unless they were trying to destroy their computers? Is there anything I need to do?

Try not following tutorials that use commands without understanding what the commands do. Read the sticky about dangerous commands in the top of this forum.

> **Nitefang said:**
> The Linux community already looks to be a lot more friendly and helpful than the Windows one.

The community is awesome. My RSS feed reader is always busy downloading new threads and most of my questions are kindly replied and solved. So I try to give something back, even not being a Linux expert. 

Sometimes you use a program for something nobody realized that could be used for or a different way of doing things, so don't be afraid to contribute.

---

### Post by pbpersson on 2008-09-17
One of the important differences between Ubuntu and Windows.....in Windows if you wanted 15 different applications, you would need to go to 15 different web sites, pay for all the applications, download them, install them, and then when you wanted updates remember how to get back to those 15 different web sites....and then perhaps you would need to renew some subscription to get your update. :(

In Ubuntu, if you want 15 applications or 1500 (I have over 1800 installed here) you pick them all from the same list in your package manager, they are all installed in a matter of minutes while you go for a walk, they are all free, AND the system automatically keeps track of all the updates and will update ALL your packages when YOU tell it to.

This aspect of Ubuntu just blows me away. :lolflag:

---

