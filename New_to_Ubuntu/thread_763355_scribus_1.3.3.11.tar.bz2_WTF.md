---
title: "scribus 1.3.3.11.tar.bz2 WTF?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2008-04-22
I have been encouraged to download scribus's latest version from sourceforge and now have "scribus 1.3.3.11.tar.bz2" on the Archive Manager and not the slightest idea what to do with it. I have searched for rational explanations - why can't Ubuntu just download the damn program so I can use it - but any explanation is a whole lot of mumbo jumbo. People, man pages make very little sense to the newbie, it's like you have to learn a whole new language to use this OS! So anyone willing to send me in the right direction, thanks, I'm all about learning how to sort out this puzzle.

---

### Post by PeterJS on 2008-04-22
Have you seen this guide:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Also Scribus 1.3.3.11 will be included in hardy. So if you wait two days our so it will automatically update itself.

---

### Post by logos34 on 2008-04-22
Let's say you downloaded it to your home dir:

Open a terminal and type:

sudo tar xjvf scribus-1.3.3.11.tar.bz2

(or Edit>Extract here)

cd scribus-1.3.3.11

./configure

make

sudo make install

(See the 'INSTALL' file inside the folder)

There is a 1.3.3.9 version in the repositories (a deb pkg and a lot easier to install), but I guess you have a reason for wanting bleeding edge vers.

---

### Post by Crenfinkle on 2008-04-22
Just make sure, before you try to ./configure, to run

sudo apt-get install build-essential

Otherwise, you won't be able to compile from source.

---

### Post by arnicainthemembrane on 2008-04-23
Thanks for the advice, I'll stop whining.

Will my Gutsy automatically become Hardy when I update it in a few days, or do I have to do something fancy?

---

### Post by arnicainthemembrane on 2008-04-23
When I tried to configure I got

The required library libart could not be found. See the BUILDING file.

You may need to install some additional libraries or packages (on Linux,
that may mean -dev or -devel packages too). Also check your environment
variables. If you're on a 64 bit machine, maybe you need to add
--enable-libsuffix=64 to the configure arguments.
See the BUILDING file for further details and troubleshooting information. 
This library is required for Scribus to build. Configure will now terminate.

... how do I check the BUILDING file, and what are environmental variables?

---

### Post by PeterJS on 2008-04-23
> **arnicainthemembrane said:**
> When I tried to configure I got

The required library libart could not be found. See the BUILDING file.

You may need to install some additional libraries or packages (on Linux,
that may mean -dev or -devel packages too). Also check your environment
variables. If you're on a 64 bit machine, maybe you need to add
--enable-libsuffix=64 to the configure arguments.
See the BUILDING file for further details and troubleshooting information. 
This library is required for Scribus to build. Configure will now terminate.

... how do I check the BUILDING file, and what are environmental variables?

Configure never works the first time for exactly this reason, should have warned you in advance, sorry. The BUILDING file is just a file named BUILDING, which I would assume contain text describing how to build Scribus. How you chose to check it is up to you, it's just another file that contains text read it with what ever program you're familiar with. The important part of the error message is at the top:
> 
The required library **libart** could not be found.

This is letting you know that you'll want to install libart-dev. Also I would expect a couple more iterations of configure failing because you need to install some more library -dev packages.

---

### Post by ace007 on 2008-04-23
To answer your other question, yes, you can select upgrade from the update manager to upgrade to 8.04

---

### Post by arnicainthemembrane on 2008-04-24
I'm understanding this, insofar as for some reason I the user have to piece together the program like a lego set. But some of the pieces are kept hidden and I have to find them using the synaptic package manager. Then I have the computer put them all together piece by piece. By piece.

I don't get the efficacy in this. I guess it's nice for people who want to be able to put their programs together and tweak them as they please, but as with a lego set I don't get why the software isn't configured to the user can simply download it and use it, then pick it apart as s/he pleases.

---

### Post by PeterJS on 2008-04-24
> **arnicainthemembrane said:**
> I'm understanding this, insofar as for some reason I the user have to piece together the program like a lego set. But some of the pieces are kept hidden and I have to find them using the synaptic package manager. Then I have the computer put them all together piece by piece. By piece.

I don't get the efficacy in this. I guess it's nice for people who want to be able to put their programs together and tweak them as they please, but as with a lego set I don't get why the software isn't configured to the user can simply download it and use it, then pick it apart as s/he pleases.

That's the reason that people use binary packages and package management. If you stick to just binary packages you won't have to piece anything together. Another thing to bear in mind is that has difficult as it is to build from source under linux, windows is far worse as you don't have a package manager to fetch library headers for you, and there isn't a standard build environment.

So yes compiling by hand is a pain, that's why most people choose not to do it.

---

### Post by Irihapeti on 2008-04-24
Scribus also has a repository of its own. There are instructions on the website about how to add it to your sources.list.  I currently have 1.3.3.12 installed in Gutsy.

---

