---
title: "[SOLVED] Is there anyway to make dialup connections work better in Ubuntu?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Vunutus on 2008-11-10
Thanks to several people on the forums I finally got my USB modem up and running. It connects and works fine (I'm posting from Ubuntu now), but is very rough around the edges.

Here's a preliminary list of my problems:

1. It connects automatically without asking me, which is inconvenient if I need my phone line for something else.
2. I have no idea WHEN it is connecting or when it disconnects (randomly, as dialup does sometimes).
3. The only way I can find out if I'm connected or not is to actually try to use it.

I messed around with the Gnome panel things and found two widgets that supposedly should help me. The "Modem Monitor" sounds somewhat like what I need; unfortunately, it doesn't do anything. The "network monitor" shows up and monitors my ppp0 (dialup) connection and lets me know when it it sending/receiving, but does nothing more than that.

My goal is to have it work like it does in Windows. I tell it when to connect and I tell it when to disconnect, with adequate feedback in between.

---

### Post by phidia on 2008-11-10
Use your package manager to get the gnome-ppp package. Install and configure that and that should help.

During the orginal set up you must have selected or editing a file that has ppp start when you boot up. Did you keep notes of what you did? You can open network manager and check your settings there.

---

### Post by Vunutus on 2008-11-10
Thanks, gnome-ppp seems to be almost exactly what I was looking for. I wonder why it isn't included by default?

---

### Post by abooks on 2008-11-10
I can't find gnome ppp in the 8.10 package manager. Is it not there, or is it somewhere else? I'm trying to find a way to do dialup, and can't find anyplace to put the data.

---

### Post by oldsoundguy on 2008-11-10
> **abooks said:**
> I can't find gnome ppp in the 8.10 package manager. Is it not there, or is it somewhere else? I'm trying to find a way to do dialup, and can't find anyplace to put the data.

It's there .. System> Adminstration> Synaptic Package Manager> sign in .. put ppp into your search box>  Have at it.

---

### Post by abooks on 2008-11-10
D'oh, it IS there. . .but how do I open it?

Homer

---

### Post by Bartender on 2008-11-10
abooks -
Are you unfamiliar with Synaptic Package Manager?  You have to be online.  Click on the "ppp" package, click OK, Apply, let Synaptic get the package and install it.  GnomePPP will then appear in Applications>Internet.

---

### Post by abooks on 2008-11-10
Yes, I'm a serious noob. . .so if I have to be online to get the package that would allow me to go online, I'll have to get it on another machine, put it on a thumb drive and hook that up to the machine I want to make onlinable.

I presume synaptic goes to Ubuntu to get it? Can humans do that too?

---

### Post by redseventyseven on 2008-11-10
> **abooks said:**
> Yes, I'm a serious noob. . .so if I have to be online to get the package that would allow me to go online, I'll have to get it on another machine, put it on a thumb drive and hook that up to the machine I want to make onlinable.

I presume synaptic goes to Ubuntu to get it? Can humans do that too?

Erm... not quite. From what I understand you don't need that app to get online using dialup. It just makes it easier to manage your online time. So provided you can get online once the hard way, you'll be able to install it, and then manage your dialup sessions as you would like to.

If you can see the app in Synaptic, I would imagine you would have been online to fetch the list of available applications, so you should be able to install it.

---

### Post by abooks on 2008-11-10
There's the catch 22. . .I've been trying for three days to get this machine connected, and it appears the only way I can do it is to get something online on another machine and put it in. The version of 8.10 I have doesn't have "Network" in its System/Administration (only "Network Tools", something completely different) So I'm trying to do an elaborate work-around. With very little knowledge, I might add.

---

### Post by abooks on 2008-11-10
There's the catch 22. . .I've been trying for three days to get this machine connected, and it appears the only way I can do it is to get something online on another machine and put it in. The version of 8.10 I have doesn't have "Network" in its System/Administration (only "Network Tools", something completely different) So I'm trying to do an elaborate work-around. With very little knowledge, I might add.

---

### Post by abooks on 2008-11-10
There's the catch 22. . .I've been trying for three days to get this desktop connected, and it appears the only way I can do it is to get something online on my windows laptop and put it in. The version of 8.10 I have doesn't have "Network" in its System/Administration (only "Network Tools", something completely different) So I'm trying to do an elaborate work-around. With very little knowledge, I might add.

---

### Post by abooks on 2008-11-10
There's the catch 22. . .I've been trying for three days to get this desktop connected, and it appears the only way I can do it is to get something online on my windows laptop and put it in. The version of 8.10 I have doesn't have "Network" in its System/Administration (only "Network Tools", something completely different) So I'm trying to do an elaborate work-around. With very little knowledge, I might add.

---

### Post by Vunutus on 2008-11-11
> **abooks said:**
> There's the catch 22. . .I've been trying for three days to get this desktop connected, and it appears the only way I can do it is to get something online on my windows laptop and put it in. The version of 8.10 I have doesn't have "Network" in its System/Administration (only "Network Tools", something completely different) So I'm trying to do an elaborate work-around. With very little knowledge, I might add.

You posted that 4 times FYI :)

I too am fairly new to Linux/Ubuntu and just finished getting my dialup configured. I have come to the conclusion that a thumbdrive and ye olde sneakernet are requirements for getting a modem to work on Ubuntu.

It seems to vary greatly from modem to modem but the best advice I can give you is that there are a multitude of PPP configuration utilities, but they aren't all means to the same end. I learned this the hard way. I used about 3 different utilities, both command line based and graphical, before I found one that worked for me (which turned out to be "dgcconfig", which I think is specific to my variety of modem).

---

