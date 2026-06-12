---
title: "Confusion on type of Ubuntu, and downloadable archived drivers."
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Mikesla on 2011-11-11
I am very confused concerning what I actually have here for Ubuntu.

I have Ubuntu 11.10 installed (windows installation), and I am having problems with getting my modem setup. Unfortunatly I must be missing some files somewhere. I can't use the make command because it's not installed I guess not too sure though because I can only guess.

 The reason for this post is that I am trying to figure out if there is a way to download programs outside of having to use the apt-get, or Software center, copy them over, then install them. Since I can't get my internal modem to work just yet I can't get access to the files repository.

Okay this is where I am really confused. I have found a site which hosts tons of dev software but I don't know which type of Ubuntu to start looking in so what is this 11.10 version of Ubuntu?

Is it...

1: Hardy?
2: Lucid?
3: Maverick?
4: Natty?
5: Oneiric?
6: Precise?

Meaning: What does Universe mean? Does it mean that it's compatible with all versions or types of Unbuntu?

I think I have become corrupted by how easy Windows is. I have invested too much time into working on Ubuntu, and I'm not going to give now.

---

### Post by Rodney9 on 2011-11-11
11.10 is Oneiric

Internal modems can be difficult. This site may help -   [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

### Post by grahammechanical on 2011-11-11
This link will explain the names of the repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

The level of difficulty between Windows and Linux is not the problem. Our way of thinking is the problem. You are in the Windows mind-set. The Linux developers are not copying Microsoft. They have their own way of doing things and they use their own words as labels. In time ( a short time) you will pick-up the Linux jargon.


Regards.

---

### Post by JayKay3OOO on 2011-11-11
One simple rule...

installer files are (mostly) .deb not .exe

---

### Post by critin on 2011-11-11
> a way to download programs outside of having to use the apt-get, or Software center, It depends on your expertise.

When you get your internet working, install Synaptic from the Software Center.  As for downloading programs, these two (synaptic and software center) have everything you'd ever need or want, and they do the installing and setting up for you.  You don't have to worry if they'll work on your version or not.  If you do want something else, look for the .deb version.  Opera has a .deb for instance.  Software Center will extract and install it if you ask it to.  Easy.

You can find out what your version is by checking The System Monitor. 

 > I have found a site which hosts tons of dev software but I don't know which type of Ubuntu to start looking in

What site is it?  

I find linux so much more interesting than Windows--hope you will too.

---

### Post by Mikesla on 2011-11-11
> **critin said:**
> It depends on your expertise.

When you get your internet working, install Synaptic from the Software Center.  As for downloading programs, these two (synaptic and software center) have everything you'd ever need or want, and they do the installing and setting up for you.  You don't have to worry if they'll work on your version or not.  If you do want something else, look for the .deb version.  Opera has a .deb for instance.  Software Center will extract and install it if you ask it to.  Easy.

You can find out what your version is by checking The System Monitor. 

 

What site is it?  

I find linux so much more interesting than Windows--hope you will too.

Thanks for the reply.

 The site is [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Haaa, boy how I am trying...my brain cells are becoming tuckered out.

Okay before I go on any further I have two types of Ubuntu installed. One is via VMware, and the other is a Windows install. I first test out on my Vmware install to get a taste of what I am trying to do, and if it works I immediately copy all downloads to a directory I can get to for my windows install.

Now here is a small problem I am being forced to get my head wrapped around, and that is I am trying to test install wvdial (.deb). Unfortunately when I do try to install it it is telling me that certain libs are not installed which are...

1: libssl0.9.8_0.9
2: libwvstreams4.6-base_4.6.1
3: libwvstreams4.6-extras
4: libuniconf4.6

..and the list will no doubt continue on just so I can install wvdial. Could someone one point me toward a full lib download so I don't have to download one file at a time?

This reminds me so much of my MSDOS days...

---

### Post by Mikesla on 2011-11-11
> **grahammechanical said:**
> This link will explain the names of the repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The level of difficulty between Windows and Linux is not the problem. Our way of thinking is the problem. You are in the Windows mind-set. The Linux developers are not copying Microsoft. They have their own way of doing things and they use their own words as labels. In time ( a short time) you will pick-up the Linux jargon.


Regards.

You have nailed it on the head, it's my mind set. Thanks for the reply, and the link I appreciate it.

---

### Post by Rodney9 on 2011-11-11
If you are use Synaptic package manager or the Software Centre they  will handle all the dependencies for you.

Rodney

---

### Post by critin on 2011-11-11
> The site is [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Haaa, boy how I am trying...my brain cells are becoming tuckered out.

Okay before I go on any further I have two types of Ubuntu installed.  One is via VMware, and the other is a Windows install. I first test out  on my Vmware install to get a taste of what I am trying to do, and if it  works I immediately copy all downloads to a directory I can get to for  my windows install.

Now here is a small problem I am being forced to get my head wrapped  around, and that is I am trying to test install wvdial (.deb).  Unfortunately when I do try to install it it is telling me that certain  libs are not installed which are...

1: libssl0.9.8_0.9
2: libwvstreams4.6-base_4.6.1
3: libwvstreams4.6-extras
4: libuniconf4.6

> .and the list will no doubt continue on just so I can install wvdial.  Could someone one point me toward a full lib download so I don't have to  download one file at a time?

Yes--Synaptic.

Okay, the site url you gave is Synaptic, don't download from that page.   In Software Center, search for 'synaptic'  and install it.  You can then reach it by typing Synaptic on search on Dash.

Then, search for wvdial on software Center and/or synaptic.  They will pull in all dependencies for you.  At least I know synaptic will, if they have it.  Don't worry about where to look for this in the long list.  Enter it on  the search bar with 'ALL' highlighted on the left of the screen.  If  it's there, it will come up.

Did you right click on the downloaded wvdia  .deb?  Right click should give you the option to 'let software center' do the work.

---

### Post by Mikesla on 2011-11-11
> **Rodney9 said:**
> If you are use Synaptic package manager or the Software Centre they  will handle all the dependencies for you.

Rodney

I don't have access to the internet via my windows install. I am trying to figure out a way to download all the files I require outside of Ubuntu, then installing them so I can eventually get my internal modem working (no luck so far).

Once I can get my modem working I will have no problem using the software center, until then I am working blind so to speak.

Thanks for the reply.

---

### Post by critin on 2011-11-11
> and if it works I immediately copy all downloads to a directory I can get to for my windows install.Okay, so you're working from windows trying to get the dialup to install to ubuntu?  Is that possible?   Is the vmware on the windows mach?  It should have internet if windows does, right?  No?  Is the other install a Wubi?   How were you able to install those?  I can see why your head hurts.  :P  You need an expert and that's not me.  I'll keep reading this one.

---

### Post by Mikesla on 2011-11-11
> **critin said:**
> Okay, so you're working from windows trying to get the dialup to install to ununtu?  Is that possible?   Is the vmware on the windows mach?  It should have internet if windows does, right?  No?  Is the other install a Wubi?   How were you able to install those?  I can see why your head hurts.  :P  You need an expert and that's not me.  I'll keep reading this one.

Haaa, I'm definitely the same way.

The windows install is by Wubi. I want to test out certain things in the vmware installed version, then try to get them to work in the Wubi install.

 I guess this whole problem I am having is not getting my modem to work. That is the only thing that is stopping me from really installing a full copy of Linux.

 Of course with Ubuntu installed in VMware I have access to the internet, but that is not where I want to be before I make a full decision to install a full copy of Ubuntu. If I can't get my modem to work, then there is no point in me even looking any further into linux simply because VMware install won't give me what I am looking for (It's slow), and I can't take full advantage of my system.

 Supposedly linux out preforms windows by a very large margin which I hope I will be able to experience once I can get my modem working.

 Modem first, and everything else will fall into place it's that simple.

Thanks for the reply.

---

### Post by Mikesla on 2011-11-12
A thought just occurred to me, has anyone tried setting up an internal modem by using Wine?

 All my modem drivers are for windows, and since wine runs windows wouldn't this also apply to hardware as well?

---

