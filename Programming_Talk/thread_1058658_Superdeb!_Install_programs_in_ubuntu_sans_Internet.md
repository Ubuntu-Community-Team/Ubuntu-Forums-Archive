---
title: "Superdeb! Install programs in ubuntu sans Internet"
date: 2009-02-03
forum: Programming Talk
---

### Post by hammer v2 on 2009-02-03
Hi guys,
I've created a way to install deb files in any ubuntu 8.10 based distro windows-style without the internet. I've called it superdeb. I'm about to unleash it onto the world but first I wanna be sure it's working correctly.

I've bundled pingus (a lemmings-type game) into a superdeb. You can download it from here;

[http://superdeb.googlecode.com/files...-2-UB0810.sdeb](http://superdeb.googlecode.com/files...-2-UB0810.sdeb)

Would you guys be so kind as to try and install it for me? just download the file, double-click on it and follow the prompts. It's not pretty but seems to be working ok over here.

Please let me know how you guys go! Give me as much feedback as you want.

Hope you're all well.
H.

---

### Post by ProgramErgoSum on 2009-02-03
Which part of 'download and install' approach does it improve upon ? Packages are still to be downloaded even with sdeb, right ?

---

### Post by Npl on 2009-02-03
well... I can just doubleclick downloaded .deb Files or install via commandline. What exactly does your superdeb add?

---

### Post by Caduceus on 2009-02-03
Also, without the internet how is one supposed to get these packages to install in the first place?

---

### Post by aanderse on 2009-02-03
I think the most important thing to bring up here is the fact that you should not be downloading and installing programs from the internet- it breaks the entire free software inherent security design.

If you only install software from your *trusted* vendor (canonical/ubuntu in this case) you'll never install a virus. If you download and install (as sudo/root) joe blows home brew (secret virus infected) version of pingus you're screwed.

One reason free software systems are so darn secure is that you only download trusted software. The average user cannot trust anything unofficial.

ps.
I have a bad feeling gnu/linux is going to have a very painful experience with malicious software once it hits high enough market penetration because people are used to downloading untrusted software from the internet. **DON'T LET THIS HAPPEN. UNLESS YOU *REALLY* KNOW WHAT YOU ARE DOING, ONLY INSTALL SOFTWARE FROM SYNAPTIC/ADD REMOVE PROGRAMS**

---

### Post by andybruk on 2009-02-03
Add/Remove programs works so well, as does using aptitude etc on the command line, why would you want to change that functionality? I have no wish to download your deb or any other deb that modifies functionality that I do not need on my system.

Sorry, but I can not see any use for it at all.

---

### Post by ajackson on 2009-02-03
The only use I can see is if the machine with Ubuntu can't connect to the internet for some reason so you have to download the deb on another machine but then you could already install from a local deb. Then again if someone wants to write an app to do the same then why not?

---

### Post by hammer v2 on 2009-02-03
> **ProgramErgoSum said:**
> Which part of 'download and install' approach does it improve upon ? Packages are still to be downloaded even with sdeb, right ?

Nope. The desired package and all of it's dependancies are bundled together into the .sdeb. No extra downloading necessary.

---

### Post by hammer v2 on 2009-02-03
> **aanderse said:**
> I think the most important thing to bring up here is the fact that you should not be downloading and installing programs from the internet- it breaks the entire free software inherent security design.

If you only install software from your *trusted* vendor (canonical/ubuntu in this case) you'll never install a virus. If you download and install (as sudo/root) joe blows home brew (secret virus infected) version of pingus you're screwed.

One reason free software systems are so darn secure is that you only download trusted software. The average user cannot trust anything unofficial.

[/B]

I agree man. But what if you're out in the countryside on dialup or in a developing country with no internet? This whole project started because I was trying to develop a Lao ubuntu distro. The distro never took off cause no one could install anything as the internet is crappy and too expensive (most people earn $2 a day in Laos).

Maybe I'll add a warning into the sdeb setup letting people know of the security risks.

---

### Post by hammer v2 on 2009-02-03
> **Npl said:**
> well... I can just doubleclick downloaded .deb Files or install via commandline. What exactly does your superdeb add?

You don't need internet access to install the dependancies. They're already in the sdeb.

---

### Post by slavik on 2009-02-04
how are sdebs created? seems like the creation tool would be very useful ...

---

### Post by hammer v2 on 2009-02-04
> **slavik said:**
> how are sdebs created? seems like the creation tool would be very useful ...

Easy! I've created a gui program that does all the work. Easy to use, easy to install...all good!
I would like to get some feedback on my test sdeb file first though before I post the creation tool for mass downloads.

Anyone installed the pingus sdeb yet?

---

### Post by nvteighen on 2009-02-04
Ok, all dependencies are bundled into one .sdeb file, but how do you get that .sdeb without the internet?

Anyway, such a .sdeb format could be very interesting in itself.

---

### Post by blackgr on 2009-02-04
how can you have a stable system after all if you keep installing different versions of libs.It would make linux chaotic 'windows like'.One of the biggest pros linux has is stability through controlled libraries and system files with regular bug fixes over them through the repository. My system after one year is as clean and fast as it was in the first day i installed it.On the other hand, other oses who use that technique after a while become unstable and bloated!

---

### Post by hammer v2 on 2009-02-04
> **blackgr said:**
> how can you have a stable system after all if you keep installing different versions of libs.It would make linux chaotic 'windows like'.One of the biggest pros linux has is stability through controlled libraries and system files with regular bug fixes over them through the repository. My system after one year is as clean and fast as it was in the first day i installed it.On the other hand, other oses who use that technique after a while become unstable and bloated!

Sure! I agree! Sdeb isn't supposed to replace .deb files or the repository system. Sdeb is complimentary to the whole apt-system. It IS the apt system.

 All sdeb does is create a repository then installs the .deb files via apt-get. If the libraries are already there, or there's newer versions already installed, apt will take care of it because we're essentially still dealing with deb files.

The repo system rocks, but ONLY if you're online. Sdeb gives ubuntu users an easy way to install programs (using apt) OFFLINE. Sdebs can be given to friends, burnt to CD, Sold, emailed and they'll install everytime.

Once an sdeb is installed, everything shows up in synaptic. the moment you get back online, it can all be updated via the real repositories.

Sdebs are created in a custom distro with a special dpkg status file. Which tells the program to download everything bar X.org and the base ubuntu system. The downside to this is that sdebs will be large. the upside is that they'll install on just about anything. It's for desktop users. Obviously servers will probably not be using X.org but then, who ever is driving them won't need sdeb anyway.

---

### Post by blackgr on 2009-02-04
Well if offline status is such a big problem why dont you try to pull together all the repos available into dvds? Here is an example. 
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch)
You can grub deb with apt-get from the dvd even if you are offline. Distributing these kind of dvds could be vital for the community and i find osdisc.com totally wrong with the idea of selling those.

Edit: the only advantage i see in this idea, is the ability to run debs in all debian based systems and not only ubuntu

---

### Post by hammer v2 on 2009-02-04
> **nvteighen said:**
> Ok, all dependencies are bundled into one .sdeb file, but how do you get that .sdeb without the internet?

Anyway, such a .sdeb format could be very interesting in itself.

You need the internet to create the .sdeb. Superdeb Creator is the name of the program and it needs the net to download all the packages that make up an sdeb. Superdeb creator isn't for everyday users. It's sandboxed in a custom distro (.iso file) so it doesn't damage your system.

Once created, the sdeb files ARE for everyday users. Just double click and follow the prompts (sound familliar?) :p


It essentially does the same thing as apt on CD, just without CDs. The big benefit is that sdeb files are easier to distribute than CDs (email, thumbdrives, torrents...whatever), grandma can install them and they are generic, i.e they will install on any desktop variant of Ubuntu.

---

### Post by hammer v2 on 2009-02-04
> **blackgr said:**
> Well if offline status is such a big problem why dont you try to pull together all the repos available into dvds? Here is an example. 
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html?ad=distrowatch)
You can grub deb with apt-get from the dvd even if you are offline. Distributing these kind of dvds could be vital for the community and i find osdisc.com totally wrong with the idea of selling those.

Edit: the only advantage i see in this idea, is the ability to run debs in all debian based systems and not only ubuntu

Hmm...well your idea is cool man...but requires you to be a linux Jedi. I, alas am no jedi. With Ubuntu going mainstream, most users aren't either. 

Also you need DVDs for the repositories. In a few years DVD drives will be few and far between. It's old technology.

---

### Post by blackgr on 2009-02-04
> **hammer v2 said:**
> Hmm...well your idea is cool man...but requires you to be a linux Jedi. I, alas am no jedi. With Ubuntu going mainstream, most users aren't either. 

Also you need DVDs for the repositories. In a few years DVD drives will be few and far between. It's old technology.

Well dont forget blu rays :P

---

### Post by nvteighen on 2009-02-04
So, what you've got there is just a way to resolve dependencies for some package no matter if on- or offline (and not having the whole repo in a DVD).

---

### Post by aanderse on 2009-02-04
> **hammer v2 said:**
> I agree man. But what if you're out in the countryside on dialup or in a developing country with no internet? This whole project started because I was trying to develop a Lao ubuntu distro. The distro never took off cause no one could install anything as the internet is crappy and too expensive (most people earn $2 a day in Laos).

Maybe I'll add a warning into the sdeb setup letting people know of the security risks.

I commend you for what you are trying to do then! I'm not entirely sure of all the technical aspects of your project, but from your description it sounds like it is attempting to achieve the same thing APT on CD/DVD does.

From their website:
> APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection.

In the situation of pingus, you could download and package into an apt repository (on a cd) pingus and all of its dependencies- which is what you are trying to do? The only difference is with apt on cd you need to add the repository to your sources (which with synaptic is easy enough).

Please visit [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) and **decide if your project shares the same goals as apt on cd**, and if so consider contributing to apt on cd instead of competing with it.

Thank you for your effort to spread free software throughout the world!

---

### Post by hammer v2 on 2009-02-04
> **nvteighen said:**
> So, what you've got there is just a way to resolve dependencies for some package no matter if on- or offline (and not having the whole repo in a DVD).

Yup, pretty much! Sdeb simply makes the whole process easier. A user (installer) doesn't need to know anything about repositories or deb files or anything...just double click and install.

I'm thinking of newbies and developing countries (limited internet) as users of this idea.

---

### Post by hammer v2 on 2009-02-04
> **aanderse said:**
> I commend you for what you are trying to do then! I'm not entirely sure of all the technical aspects of your project, but from your description it sounds like it is attempting to achieve the same thing APT on CD/DVD does.

From their website:


In the situation of pingus, you could download and package into an apt repository (on a cd) pingus and all of its dependencies- which is what you are trying to do? The only difference is with apt on cd you need to add the repository to your sources (which with synaptic is easy enough).

Please visit [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) and **decide if your project shares the same goals as apt on cd**, and if so consider contributing to apt on cd instead of competing with it.

Thank you for your effort to spread free software throughout the world!

Aw thanks! 
My project is essenially the same as apt on CD except for 3 main things.

- An AptonCD CD doesn't install on every copy of ubuntu. It only works on the computer that created the CD. It might work on your friend's computer...it might not. It all depends on what libraries etc they have installed. 
A sdeb file installs on any ubuntu desktop (provided it's the same base i.e gutsy, hardy or intrepid...).

- AptonCD still needs synaptic. A sdeb file is completely self contained. It installs with a simple double-click.

- I am NOT a programmer! I'm really bad! I studied BASH scripts for months to make superdeb. I'd love to contribute to aptonCD! But I have no idea how! Apt on CD is written by real programmers! Not idiots like me! :D


P.S if anyone wants to see my (horrible) script, you can check it out here;
[http://docs.google.com/Doc?id=dghntsrk_182g3svd4fh](http://docs.google.com/Doc?id=dghntsrk_182g3svd4fh)

---

### Post by aanderse on 2009-02-04
You also may want to read over this post: [http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/) for interests sake.

---

### Post by hammer v2 on 2009-02-06
Here's something a bit more useful.
An ubuntu-restricted-extras sdeb (No flash or msft fonts)

[http://www.zshare.net/download/551500648bbc0c4c/](http://www.zshare.net/download/551500648bbc0c4c/)

---

### Post by AXeS on 2009-03-13
im still n0obish, dont have a direct ubuntu internet connection.

started using ubuntu 2 weeks today.im pretty glued to and so interested in it that i reseached a manual way of downloading install (.deb) files.
i did it the long way,1 dependency at a time then i found aptitude and just noted what i didnt have and download them 1 for 1 after...then today i saw you can generate a dependency script using synaptic...i wanted to compile all the dependencies for a multi-media ubuntu that can run mpeg avi and so on,so i could share it with my windows loving friends and family.but as most of them dont have a net connection they dare not dig any deeper than what they already know... (c0nditi0ned/brainwashed
microsoft dr0nez)

anyway and now this cool superdeb.
i thank you greatly...

but whens the program due to mass download or do i use the script you posted?
not sure how to use it.

---

### Post by Bartender on 2009-03-16
I've been dinking around with Keryx and KeryxPortableApps the last couple of days.  Not sure if I have it working or not but might be getting there.

Keryx's basic concept is, I think, superb - you install Keryx to a USB thumb drive, ask it to catalogue all the packages on your target PC, then take the thumb drive to some place with broadband and pop the thumb drive into a Windows or Linux PC.  You should then be able to open Keryx and ask it to update, search for optional packages, etc.  Bring the thumb drive home and install the data.

How does sdeb differ?  I'm not grasping your description...

---

