---
title: "Q for professional developers"
date: 2010-07-01
forum: Programming Talk
---

### Post by fashoom on 2010-07-01
Hi, I'm a java developer and I've always developed in a Windows environment. Question I have is -- when a shop says they do development on Linux, are they likely using 'raw Linux' and installing developer tools and such w/ pkgadd or does everyone use distributions like Ubuntu these days w/ a modern desktop where installing applications is rather 'Windows-like'? Again, I'm talking about software development shops here, not general users.

Thanks for any help.

---

### Post by wmcbrine on 2010-07-01
There's no such thing as "raw Linux". Everyone uses a distro of some kind, and always has. But of course the distros vary widely.

I'm not sure what "pkgadd" is, outside a Solaris context. Linux distros tend to fall into one of two camps, Debian-based (which includes Ubuntu), or RPM-based. There are also some distros outside these camps. What the shop uses will depend in part on what they're doing -- server stuff? embedded? -- and on whether they're developing "on" Linux, or merely *for* it.

Anyway, it doesn't matter. They will surely provide you with the tools you need, and in fact they might not let you handle your own installation.

Installation of apps in Ubuntu is not Windows-like at all, BTW. And if your real question is about GUI vs. CLI... you can install apps either way in Ubuntu, and in pretty much every other distro. Most distros can run with or without GUIs. (Server and embedded environments would tend to run without. Your development desktop is another issue.)

---

### Post by fashoom on 2010-07-02
OK tnx, that was super helpful. Can you explain what you meant by the last bit, "Your  development desktop is another issue"?

---

### Post by ad_267 on 2010-07-02
Hope you don't mind if I jump in and answer.

They mean that often you're developing an application that will be running on embedded Linux or on a Linux server. In that case it won't be designed to run on a desktop but you will usually be developing the application on a desktop machine. So you have two Linux environments to consider, the desktop Linux you're using for development and the target Linux system for the application.

The desktop Linux will usually be a common distribution like Ubuntu or Fedora but embedded Linux can be a lot different, I don't have any experience with embedded Linux though so can't expand on that. A Linux server will often be running a common distribution but will usually be headless so everything is command line only.

---

### Post by fashoom on 2010-07-02
The target platform is the Java VM which could be running on Linux, Windows, or any other OS that supports it. My concern is the development environment. It's a concern because I have zero experience developing in a Linux environment. I'm trying to determine whether that should be a consideration as I hunt for jobs. Another thing to learn that could potentially slow down my productivity on the job is a minus. But I'm trying to determine how significant/trivial it would be.

Maybe it's a different world on Linux but on Windows I'm always downloading and installing utilities for various tasks.

---

### Post by wmcbrine on 2010-07-02
Yes, it's a different world. But I don't think it should be a consideration. It shouldn't take you long to adapt.

---

### Post by fashoom on 2010-07-02
OK, and it would probably be adapting to a desktop environment like Ubuntu?

---

### Post by ad_267 on 2010-07-02
Yeah it won't be too hard to adapt, you'll be most likely using something like Ubuntu.

The main difference in Linux is that you usually download and install software from the repositories using a package manager like apt-get, synaptic or the Ubuntu software centre, rather than going to a website to get them. 

Other than that you can use an IDE like Eclipse for development which shouldn't be too different to anything you've used in Windows.

---

### Post by fashoom on 2010-07-03
Cool, I already do development on Eclipse. I'll install Ubuntu and play around. 

Thanks for all the help!

---

