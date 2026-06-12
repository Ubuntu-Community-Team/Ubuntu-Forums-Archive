---
title: "New to Linux- A lot of questions-here are two."
date: 2008-07-17
forum: New to Ubuntu
---

### Post by nremondelli on 2008-07-17
I have always had Macs so I am new to Linux.  I have a few questions:

First and foremost, how do you install programs?  Does it all have to be done from the terminal?  For example, if I see a program on a website what steps do I need to get it up and running on the computer?

Next question: I need to figure out how to network with my desktop iMac.  It doesn't seem easy to do. Any programs that will show all of the computers on the network.

Thanks!

---

### Post by seagullplayer77 on 2008-07-17
Installing programs is actually pretty easy in Ubuntu. You *can* do it through a terminal if you'd like to, and in some cases it's easy to if you have a tutorial that tells you how. Usually, if you're doing it in a terminal, you can use a command like "aptitude" or "apt-get install" to install a program from the official Ubuntu repositories. Also, there's a tool in Ubuntu called Synaptic that lists all the packages, libraries, and programs on the repos, and it's very easy to install using Synaptic. Just select the packages you want installed and it'll do the rest.

As for the networking, I'm not sure I can help you on that one. I can connect to my Windows network without a hitch using Samba, but I'm not sure how you'd connect to a Mac network. The way I connect is by going into Places > Network and then selecting my network. Maybe it'll work for you too?

---

### Post by m_ad on 2008-07-17
I'm still new also, but I can answer part of the first question.

In Ubuntu, to install applications, you simply click your Applications menu -> Add/Remove.. you can search by categories or keywords. As for finding applications on a website, you should try and find it in the repositories (the Add/Remove.. tool I told you about earlier) or at least a .deb file. Most widely used software for Linux is available through the repositories.

As for networking, sorry but I can't help there.

---

### Post by SlalomMan on 2008-07-17
Also, for programs; some sites will give out a .tar.gz file or something similar; this is an archive. Most of the time you have to extract this, then go into a terminal and run the following commands "./configure" "make" and "make install" in that order. That should install it.

I don't know much about Macs so I can't help you there.

---

### Post by Vivaldi Gloria on 2008-07-17
Welcome to linux. The linux way of installing things is very different. You use synaptic to install programs. It's in the top panel, system menu > admin.

Start synaptic, enable restricted and multiverse repositories from the repository settings. Then click refresh. Then search & install whatever you want in synaptic.

If synaptic doesn't have what you want, only then consider downloading from the net. In this case you can download a deb file and double click on it to install it.

---

### Post by ugm6hr on 2008-07-18
Try the start here... link below for general advice (including links on installing programs).

OSX supports SMB (Windows networking protocol) too, so it should be possible to use that with Ubuntu.  Maybe ask in the Mac sub-forum for a more complete guide.

---

### Post by hansdown on 2008-07-18
Welcome nremondelli. The folks here are very helpful. Just ask if you have any problems. You'll see some honestly good humour also.

---

### Post by hyper_ch on 2008-07-18
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by billgoldberg on 2008-07-20
> **nremondelli said:**
> I have always had Macs so I am new to Linux.  I have a few questions:

First and foremost, how do you install programs?  Does it all have to be done from the terminal?  For example, if I see a program on a website what steps do I need to get it up and running on the computer?

Next question: I need to figure out how to network with my desktop iMac.  It doesn't seem easy to do. Any programs that will show all of the computers on the network.

Thanks!

There are a lot of ways to install programs on Ubuntu.

The easiest would be to go to "applications -> add/remove". 

Make sure, in the drop-down menu on the top, you enable all available software.

--

Another way, more advanced, is by going to "system -> administration -> synaptic package manager". 

Search for the package, tag it and press apply.

--

You can also download files from the internet.

The easiest way to install packages offered on website is by downloading the .deb package.

Installing that is as easy as double clicking the file.

--

If only a .tar.gz is offered, then you'll have to compile it yourself from the command line. Most of the time instruction will be given on how to compile it.

--

If you want to install packages from the command line instead of using synaptic, you can do so by using the command

```
sudo apt-get install packagename
```

--

Some times a link will be offered, when you click it it will offer to install the package on your computer.

This is done by using apt-url.

You must know that all software you install by using "add/remove", "synaptic" or "apt-get" comes from the ubuntu repositories. These repositories are managed by the ubuntu team itself so all software in it is tested and safe.

apt-url uses the same repository, so it's completely safe and is no security thread at all.

Lets say a website talks about the audio player bmpx, then it could also include a link wich will let you download and install it like this:

[link]("apt://bmpx")


----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------

On the connecting to your osx box.

I believe you can do it with samba, but to be honest, I find SSH much easier.

Just install "openssh-client" and "openssh-server" on your ubuntu box.

Use the     
```
sudo apt-get install openssh-server openssh-client
```
command.

To install openssh on osx:

[http://www.securemac.com/macosxopenssh.php](http://www.securemac.com/macosxopenssh.php)

To connect to you mac computer from ubuntu, this might come in handy:

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

To connect to your ubuntu box from osx, I can't help, but I guess it won't be much harder then the other way around.

--

I set this up (on two ubuntu machines) in 1 minute, so it can't really get much easier.

---

### Post by a0u on 2008-07-20
Like what other users have already said, Add/Remove and Synaptic are the primary methods of installation and for keeping track of what your system contains.

Some extra info that may be useful:

Community Docs has a [detailed page]("https://help.ubuntu.com/community/InstallingSoftware") on installing software.

If you haven't already, be sure to become familiar with the [concept of repositories]("https://help.ubuntu.com/community/Repositories"), a major feature of Linux that neither Mac OS nor Windows have.  Add/Remove and Synaptic utilize repositories to obtain software packages; the main advantage of installing via repositories is so that the Update Manager can handle updates to individual applications in addition to the base system.

Installing from binaries is the preferable method for a beginner, but sometimes those are not available (in which case [compiling from the source code]("https://help.ubuntu.com/community/CompilingSoftware") becomes necessary).
> **SlalomMan said:**
> Also, for programs; some sites will give out a .tar.gz file or something similar; this is an archive. Most of the time you have to extract this, then go into a terminal and run the following commands "./configure" "make" and "make install" in that order. That should install it.
For the above instructions to work, you must first install some tools that are not included  in Ubuntu by default.
```
sudo apt-get install build-essential automake
```

---

### Post by raydeen on 2008-07-21
I've always used FTP to get files from one place to another. The only problem I've ever had with Macs on my network is that I couldn't do any FTP from the Mac, only to it. If you go to the Sharing section of the Mac's System Preferences, you'll get your Mac's IP address. Just activate FTP on your Mac and you should be able to send and receive files to it from Windows or Linux machines. I must be missing something but I've always gotten the message on the Mac saying I didn't have permission to modify the remote computer. If I go from the other computer to the Mac, there's no prob. Weird.

---

