---
title: "How to build custom Linux Distribution?"
date: 2009-12-19
forum: Programming Talk
---

### Post by Jasonx86 on 2009-12-19
Hi,

Please can someone give me a vague outline of how to go about building a custom Linux distribution based on Ubuntu?

What would need to be done to get community support and have it recognised as an official Linux distro?

What needs to be removed from Ubuntu to remove all Ubuntu specific dependencies? i.e. Synaptic Package Manager, Ubuntu Software Centre, Ubuntu One, etc...

Also, where can documentation on the current structure of the Linux kernel be found? i.e. detailing how the kernel pieces together.

Thanks

---

### Post by grayrainbow on 2009-12-19
> **Jasonx86 said:**
> Hi,

Please can someone give me a vague outline of how to go about building a custom Linux distribution based on Ubuntu?

What would need to be done to get community support and have it recognised as an official Linux distro?

What needs to be removed from Ubuntu to remove all Ubuntu specific dependencies? i.e. Synaptic Package Manager, Ubuntu Software Centre, Ubuntu One, etc...

Also, where can documentation on the current structure of the Linux kernel be found? i.e. detailing how the kernel pieces together.

Thanks
Hmm, that's sound a bit like oxymoron. How it is supposed to build distro base on Ubuntu by removing everything Ubuntu related? Plus - it's pretty bad idea to try 'official' distro base on Ubuntu, couse Ubuntu is already base on Debian(one of the biggest 'official' distros, the idea of .deb packages come from there). So just make flavor of *buntu or for something like more 'real distro' go base on Debian, Fedora, openSuSE, Slackware, Gentoo, or the very definition of distro - just the kernel and what you want around it.
Few standard links:
[http://kernel.org/]("http://kernel.org/")
[http://tldp.org/]("http://tldp.org/")
You could also try something like:
[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")
And probably 'the most easy' way nowadays:
[http://susestudio.com/]("http://susestudio.com/")

---

### Post by Jasonx86 on 2009-12-19
[grayrainbow]("http://ubuntuforums.org/member.php?u=898364"), thanks for your informative reply.

Building a flavour of Ubuntu sounds ideal.

I suppose my only reservation for not wanting to work on a flavour of Ubuntu is because I'm uncertain of the future of *buntu Oses - if Canonical withdrew its support would Ubuntu still be around? (lol a question for another thread).

thanks again.

---

### Post by dwhitney67 on 2009-12-19
Read this:  [http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)


Still interested?  It's a lot of work, and undoubtedly you will encounter a lot of problems.  But this is how Linux is built... from the basic components... and then all of the other stuff (eg. X11, web browsers, etc) is added on afterwards.

---

### Post by grayrainbow on 2009-12-19
> **Jasonx86 said:**
> [grayrainbow]("http://ubuntuforums.org/member.php?u=898364"), thanks for your informative reply.

Building a flavour of Ubuntu sounds ideal.

I suppose my only reservation for not wanting to work on a flavour of Ubuntu is because I'm uncertain of the future of *buntu Oses - if Canonical withdrew its support would Ubuntu still be around? (lol a question for another thread).

thanks again.
Well, Slackware is still around, Debian is still around, Arch is still around...basicly(as usual for open source stuff) if there are enough people to like some distro, and they have time and desire, it will be around for years.

---

### Post by Jasonx86 on 2009-12-22
Thanks for your replies.

I've been tinkering with Suse Studio for a little while and thinks it's great for creating customizable bare-bone OS images like JeOS etc.

What would need to be done to create similar OS images with Ubuntu? i.e. Suse Studio uses Kiwi ([http://en.opensuse.org/Build_Service/KIWI/Cookbook](http://en.opensuse.org/Build_Service/KIWI/Cookbook)) to create its OS images, what tool would need to be used to create Ubuntu images?

Thanks

---

### Post by kennethadammiller on 2009-12-22
Actually, remastersys would probably be your best bet if what you want to do is create custom distributions. It's made to do just what you're asking for. All you have to do is install ubuntu, install remastersys. Then just make the changes to the current ubuntu system you just installed, run remastersys and it will produce a duplicate live cd that will install a system just like yours.

So basically you can make your own live cd. And I'm sure if you make enough changes you can achieve what you want with this tool.

And if you're planning to start your own ubuntu based OS, your going to have to have some kind of special professional skill. Debian became huge in the first place because a guy with a wife named Debora(h) (hence debian) decided to make package like installers, much the same as what the exe is. So this is no small undertaking in the least.

---

