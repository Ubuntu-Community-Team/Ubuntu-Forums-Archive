---
title: "How do installations work in Ubuntu/Linux?"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by asmith2306 on 2013-04-03
Hi,

could someone explain to me how software/program installations/removals work on Ubuntu?  I know there is a software centre but some of the software I want isn't in it.  There is also the apt-get command but I am not entirely sure how that works.  For every program I want to install using apt-get there can be many different ways I find how to do it when I google it.  Everyone seems to have a different ways!  I assume apt-get is linked to a repository but how do I see this repository or find the repository a program I might want to install sits in, and its dependencies.  My biggest gripe when switching from Windows to Linux is the install process.  On windows, you download the installer, click run and bang it works.  When I want to remove a program I simply choose uninstall program in the control panel.  Why is it such a hassle in Linux?  If there is an easy way of doings things with apt-get that you would recommend to a newbie could you please tell!

Thanks,
Alan

---

### Post by ibjsb4 on 2013-04-03
>  When I want to remove a program I simply choose uninstall program in the control panel.  Why is it such a hassle in Linux?


Its not, just use the remove button in the software center.

---

### Post by cortman on 2013-04-03
As ibjsb4 said, it isn't a hassle. It's just different. Linux != Windows.
One tip that may help you understand is that the software center, apt-get, and such are all the same thing. The Ubuntu Software Center is just a graphical front-end for apt-get. It uses the same repositories and the same commands for installation.
Another graphical front-end (which I prefer to the USC) is Synaptic Package Manager. Both it and USC can install, remove, and upgrade your programs.

---

### Post by asmith2306 on 2013-04-03
> **cortman said:**
> 
One tip that may help you understand is that the software center, apt-get, and such are all the same thing. The Ubuntu Software Center is just a graphical front-end for apt-get. It uses the same repositories and the same commands for installation.


I didn't know this, thanks.  So how do I find and add repositories to the software centre?  Or even view existing ones?

---

### Post by ibjsb4 on 2013-04-03
One way would be your sources list.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Canonical_Partner_Repositories)

---

### Post by philinux on 2013-04-03
> **asmith2306 said:**
> Hi,
 I know there is a software centre but some of the software I want isn't in it.  
Alan

What software is it that you need?

---

### Post by bashhimup on 2013-04-03
Try looking around on the internet for some deb files (or tarballs) of the applications that are similar to the ones you want to use. If you have no luck with that, try [Wine]("http://www.winehq.org/").

---

### Post by mastablasta on 2013-04-03
> **asmith2306 said:**
>  On windows, you download the installer, click run and bang it works. 

well it's a bit more complicated than that isnt' it? 
1. You need to first check the system requirements - at the very least will it work on your windows version or not. imagine downloading 2 GB programme only to find out it doens't work.

2. you then proceed with download and either hope that no one added any malicious code in the file or you need to scan the file after download. this could take some time if the installer file is huge. it is usualyl done automaticly after download.

only then you proceed with install.

in ubuntu you have repositories - a key signed safe storage places where you get programmes with verified safe and stable code. these then also provide safe updates security or otherwise to the programmes.

this kind of package management has another good side - that you dont' need duplicated libraries - making linux version of programmes a lot smaller than windows.  since they use shared libraries. in windows libraries are also shared, but developers don't know which libraries you might already have so they include all necessary ones. which has it's good side. but also makes the programme a lot bigger than they should be. for example Ubuntu on install is about 6-7 GB big (this be reduced further) while windows needs at least 20GB space. probably 40-50 GB after you add some basic programmes ot it..

but if you feel adventurous there are other options.
- as mentioned before PPA (they are personal repositories) - no one guarantees they are safe so these need to be trusted (like windows download)
- .deb files - these are prepackaged executables - kind of like .exe files in windows. download, double click, enter password (to confirm it was you that executed it and not some malware) and away it goes.
.tar.gz these are like zip - you need to unpack them. they then inlcude instructions on how to install. often they include source code you can use to build the programme. sometimes thought they only have a .sh file that needs to be allowed to execute by the user. you then just double clikc it and there it is. to remove it you just delete the files.


now if you go repositories and command line - if you put man in fornt of command you will get a manual page for the command. with all the switches and such explained. try it:

```
man apt-get
```

have you noticed you can copy and paste commands into terminal?

---

### Post by snowpine on 2013-04-03
Ubuntu Software Center (or Synaptic, or apt-get) should always be your first choice for installing applications. These are tested and trusted applications that will keep your system running smooth and stable. Don't think of it like Windows; think of it like Apple iPhone/iPad App Store---one-click installation of safe applications designed specifically for your Ubuntu release.

If a specific application you're looking for doesn't appear in the Software Center, then start a new thread with a specific thread title such as "how do I install Handbrake in Ubuntu 12.10?" (for example) and you will get great advice every time. :)

Here's a helpful tutorial on various software install methods: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by cortman on 2013-04-03
> **bashhimup said:**
> Try looking around on the internet for some deb files (or tarballs) of the applications that are similar to the ones you want to use. If you have no luck with that, try [Wine]("http://www.winehq.org/").

With all due respect this is some very, very bad advice to a new user, and inadvisable even to an experienced user. There's no guarantee of binary compatibility even among debs, and tarballs typically mean compiling and manual dependency checking. Let's not send a new user there! :)
Not sure how Wine enters the equation at all, either.

---

### Post by mamamia88 on 2013-04-03
Ubuntu is Debian based.  It uses the command line tool apt to fetch and installl packages from remote servers.      Software Center and Synaptic are both just GUI front ends for apt.  They will both do the exact same thing. If you know exactly what you want to install it's often quicker to type sudo apt-get install name of package.  But it's case and spelling sensitive.  Therefore if you don't know what you are looking for I suggest the software center (which again when you hit install it's just running sudo apt-get install, but in the background).   If you need software not in the official repos or newer versions of stuff that is you can add ppas which blend seamlessly with all the other official repos on your system.  Hope that makes any sense

---

### Post by bashhimup on 2013-04-03
> **cortman said:**
> With all due respect this is some very, very bad advice to a new user, and inadvisable even to an experienced user. There's no guarantee of binary compatibility even among debs, and tarballs typically mean compiling and manual dependency checking. Let's not send a new user there! :)
Not sure how Wine enters the equation at all, either.
Ah. Sorry. Uhm.. OP, sorry for that post. I'm not sure what I was thinking. Ignore it. :(

---

### Post by asmith2306 on 2013-04-03
> **bashhimup said:**
> Ah. Sorry. Uhm.. OP, sorry for that post. I'm not sure what I was thinking. Ignore it. :(
No problem at all!  I read up on .deb packages as a result!  Thanks for the replies everyone.

---

### Post by asmith2306 on 2013-04-03
Very helpful, thank you!

---

### Post by bashhimup on 2013-04-03
> **asmith2306 said:**
> No problem at all!  I read up on .deb packages as a result!  Thanks for the replies everyone.
Ah, okay. You're welcome. :)

---

### Post by asmith2306 on 2013-04-03
Thank you, great reply.  So to how do I uninstall properly?  So no files are left over?

---

### Post by zrdc28 on 2013-04-03
**Thank you, great reply. So to how do I uninstall properly? So no files are left over? **

Open synaptic package manager, in the middle of the top screen is Search, tap it, search for the package you want to install or remove. when you find it, right
click on it and do as you wish.
Up close to the search to the left is the repositories open and look at them, choose what you want there.

---

