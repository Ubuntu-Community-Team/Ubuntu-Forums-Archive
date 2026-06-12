---
title: "HOW TO: Setup Usenet binary downloading (NZB + PAR + RAR) without CLI or terminal use"
date: 2007-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by LANjackal on 2007-04-27
I wrote this tutorial as just about every post I've seen regarding the above involves the user tangling with the command line. If you grew up on GUIs like me, you probably absolutely detest dealing with the terminal and just want something you can click through. That's what this post is about.

That said, please bear in mind that this may not result in the most absolutely efficient way of dealing with the subject matter. That title probably belongs to [Hellanzb]("http://www.hellanzb.com/trac/"). Hellanzb requires command line encounters, though.

**Platform Details**

OS: (X)ubuntu 7.04 Feisty Fawn 32-bit (the guide should work for Ubuntu and Kubuntu, however)
CPU: Pentium III

**List of Needed Applications**

[LIST=1]
[*]KLibido or Pan
[*]PyPar2
[*]RAR
[*]Xarchiver (already installed by default)
[/LIST]

**Steps**

With that lengthy preamble, we can now begin the simple point-and-click process I mentioned at the outset. I won't go into the details of specifically setting up each program as, not only is it simple and intuitive, it's very likely that if you've reached this topic, you're probably already capable of doing so yourself. If you've done binary downloading from Usenet via NZB before, you probably know that there are 3 basic software functions/steps involved:

1 - Downloading the binaries 

This is handled by a newsreader. I recommend [KLibido]("http://klibido.sourceforge.net/") or [Pan]("http://darrenalbers.com/Pan/"). Both can be installed via Synaptic. Pan is more fully featured, but if you're really interested in binary downloading only, KLibido's your ticket. Both support multiple servers and multiple connections per server.

2 - Checking binary integrity using PAR files

Use [PyPar2]("http://pypar2.silent-blade.org/"), a frontend for the par2 CLI utility. It can also be found on the repositories or downloaded directly from their website as a .deb. Installing PyPar2 will install the par2 dependency also, so no need to worry about that.

3  - Decompressing RAR files

a - Install RAR via Synaptic.

b - Use Xarchiver (ships with Ubuntu, serves as a frontend to the RAR application) to decompress downloaded RAR files: 

- Applications -> Accessories -> Xarchiver
- Click "Open"
- Browse to archive location and click "Open". Note that this will NOT extract the archive, it only generates a list of files the archive contains
- In the generated list, select the files you want extracted and click "Extract"

And you're done. No, this is not an all-in-one solution, but it involves zero command line/terminal use :). Also, Step 3 is pretty much how you can handle RAR files in Ubuntu via GUI for any purpose, not just newsgroups.

Enjoy!


**EDITS**

2007-04-27
- (Thanks frodon) Removed window manager specific references to KLibido and Pan to prevent confusion. KLibido should also work on Gnome.
- Changed CPU details of machine from Pentium 4 to Pentium III

---

### Post by frodon on 2007-04-27
If you wish i wrote a really simple nautilus script with a GUI for par2 verify and repair operations, it allows you to run a check/repair just right clicking on the par2 file under nautilus :
[http://ubuntuforums.org/showthread.php?t=394585](http://ubuntuforums.org/showthread.php?t=394585)

About rar files, i am able to unrar them just right clicking on them and choosing "extract here" though i have rar installed as well.

Klibido works for gnome as well (not really clear the way you wrote it) ;)

---

### Post by LANjackal on 2007-04-27
> **frodon said:**
> If you wish i wrote a really simple nautilus script with a GUI for par2 verify and repair operations, it allows you to run a check/repair just right clicking on the par2 file under nautilus :
[http://ubuntuforums.org/showthread.php?t=394585](http://ubuntuforums.org/showthread.php?t=394585)
Thanks, but the entire point of my post was to avoid the use of the command line/scripts/**anything besides point-and-click, installation and setup process included**. I'm a GUI person ;).

> **frodon said:**
> About rar files, i am able to unrar them just right clicking on them and choosing "extract here" though i have rar installed as well.
Does that happen by default after you install RAR? Everything else I've read suggests that you have to use Xarchiver as a frontend if you want GUI-based extraction.

> **frodon said:**
> Klibido works for gnome as well (not really clear the way you wrote it) ;)
Edited to reflect that, with credit to you :). Thanks.

---

### Post by frodon on 2007-04-27
hehe, maybe i can find a way to package my nautilus script in a .deb file :mrgreen: ,  PyPar2 looks great and it supports par2 file creation, the only thing missing would be a right click feature but it's a really complete tool.
Anyway if you are interested by a .deb package for my script i can search how to do that if you thinks it would help. It's not important in my eyes but i trust you when you say it's important for you and many users.

About rar files what i said is true for Gnome however i don't know if other desktops offer the same feature but they should offer it  as well. Don't you have an "extract here" option when right clicking a rar file ?

---

### Post by LANjackal on 2007-04-27
> **frodon said:**
> hehe, maybe i can find a way to package my nautilus script in a .deb file :mrgreen: ,  PyPar2 looks great and it supports par2 file creation, the only thing missing would be a right click feature but it's a really complete tool.
Anyway if you are interested by a .deb package for my script i can search how to do that if you thinks it would help. It's not important in my eyes but i trust you when you say it's important for you and many users.
I'd appreciate that and add it to the guide, since it fits what I'm looking for. Where would you host it, though?

> **frodon said:**
> Don't you have an "extract here" option when right clicking a rar file ?
Actually I do :)

Also, it appears that Xarchiver chokes on password-protected archives. It throws an error message about a password required, but doesn't give the user any way of inputting one.

---

### Post by flyingbrass on 2007-04-29
> Also, it appears that Xarchiver chokes on password-protected archives. It throws an error message about a password required, but doesn't give the user any way of inputting one.
I haven't tried any password protected archives, but often encounter the "password protected" notice on regular rar archives. Some parts are corrupt.  Run par2 on it, then extract again.

---

### Post by LANjackal on 2007-04-29
> **flyingbrass said:**
> I haven't tried any password protected archives, but often encounter the "password protected" notice on regular rar archives. Some parts are corrupt.  Run par2 on it, then extract again.
This is the part where I mention that I have a Windows XP Pro SP2 machine (see my signature) on which I successfully extracted the password-protected archive ;) *being cheeky*

It wasn't a case of corruption. The archive really did require a password.

---

### Post by PacShady on 2007-05-07
Does anyone know if there's a way to make these newsreaders work through TOR? Or if there are other newsreaders in Linux that can be set up to use a proxy for TOR?

'Shady

---

### Post by frodon on 2007-05-08
> **PacShady said:**
> Does anyone know if there's a way to make these newsreaders work through TOR? Or if there are other newsreaders in Linux that can be set up to use a proxy for TOR?

'ShadyI think this is against the TOR code of conduct please avoid asking such questions here, the purpose of TOR is not to make you anonymous while downloading.

Further posts about this will be removed.

---

### Post by PacShady on 2007-05-08
> **frodon said:**
> I think this is against the TOR code of conduct please avoid asking such questions here, the purpose of TOR is not to make you anonymous while downloading.

Further posts about this will be removed.

Actually, I thought the entire purpose for TOR's existance was to make one anonymous REGARDLESS what they're doing. It can be integrated into BitTorrent programs and other various filesharing programs, which are DESIGNED for downloading. Anything that can run through the TOR proxy is fine, according to the website. Sure, using it for ILLEGAL purposes like downloading illegal content or spamming might not be intended and frowned upon by the developers, but we're not talking about that here, otherwise this entire thread dedicated to downloading potentially illegal content from newsgroups would be deleted for the same reason you threaten to delete my post. Newsgroups can be abused, just as BitTorrent, Gnutella, FastTrack, even HTTP, can be abused.

Indeed, I put it to you that you are, in fact, more in breach of TOR's stance on freedom of speech than I am in breech of any code of conduct for asking a simple question of privacy. TOR was made to make one anonymous on the net, if not then you tell me what it's designed to do. And you'd better tell the developers too, because I'm sure they're waaaaay off track!

'Shady

---

### Post by frodon on 2007-05-08
> **PacShady said:**
> Actually, I thought the entire purpose for TOR's existance was to make one anonymous REGARDLESS what they're doing. It can be integrated into BitTorrent programs and other various filesharing programs, which are DESIGNED for downloading. Anything that can run through the TOR proxy is fine, according to the website. Sure, using it for ILLEGAL purposes like downloading illegal content or spamming might not be intended and frowned upon by the developers, but we're not talking about that here, otherwise this entire thread dedicated to downloading potentially illegal content from newsgroups would be deleted for the same reason you threaten to delete my post. Newsgroups can be abused, just as BitTorrent, Gnutella, FastTrack, even HTTP, can be abused.

Indeed, I put it to you that you are, in fact, more in breach of TOR's stance on freedom of speech than I am in breech of any code of conduct for asking a simple question of privacy. TOR was made to make one anonymous on the net, if not then you tell me what it's designed to do. And you'd better tell the developers too, because I'm sure they're waaaaay off track!

'ShadyWell, I read on other forums that using TOR for peer to peer is in violation with the TOR code of conduct because it ruins the TOR server bandwidth, this is not about what you are downloading but more about the limited TOR server bandwidth. If everyone use it for P2P they will just spend some energy to filter P2P packets, i think you will agree that TOR devs should better put their energy in improving TOR.
It is why TOR invite every user to run a TOR server and thus add more bandwidth ;), hopefully one day there's will be enough bandwidth to avoid such restrictions.

If i can find the exact text i will try to send you a copy (i'm interested as well to see if the text has been updated).

---

### Post by PacShady on 2007-05-09
I would be interested in finding that out too. I couldn't find it anywhere on the site, but there again I wasn't specifically looking for that, I assumed by "breach of code of conduct" you meant illegal or immoral activities such as copyright infringement or spamming.

I'm not necessarily looking for TOR to be used for downloading (indeed, I've found that TOR can be quite slow downloading large files, so I usually don't bother using it for large files). But I was interested in using it to read newsgroups and such, simply for privacy sake. I'd much rather use BitTorrent anyway for large files, which I usually DON'T use TOR for ;)

'Shady

PS: I'd offer to run a TOR server myself, but I'm having trouble getting it working on my IPCop firewall (where I installed it, figuring it would be good to run from there and use it as a client as well for my computers). Someday I'll figure out how to get it working, and do my part to support the TOR community :)

---

### Post by LANjackal on 2007-05-11
> **PacShady said:**
> Does anyone know if there's a way to make these newsreaders work through TOR? Or if there are other newsreaders in Linux that can be set up to use a proxy for TOR?
Ummm... usenet is pretty anonymous for the most part, especially if you're using a 3rd party provider. Unless you live under a repressive regime (in which case usenet is probably the least of your 'net concerns), TOR is really NOT necessary for it at all.

Oh yeah, and that's unrelated to the topic of this thread. Please try to keep focused on the subject. Thanks :)

---

### Post by dibon on 2009-03-01
Does anyone know how i *can* do this **in the terminal**?

I'm kinda tired of the nzb GUI.

- O

---

### Post by mikodo on 2009-05-12
> **LANjackal said:**
> This is the part where I mention that I have a Windows XP Pro SP2 machine (see my signature) on which I successfully extracted the password-protected archive ;) *being cheeky*

It wasn't a case of corruption. The archive really did require a password.

I have never downloaded Binaries. Does the above statement mean that this is an incomplete guide for it in Ubuntu Linux and that one must extract the password-protected archives from a Windows machine?

Other than the quote, this looks like something I could use being a greener than green Newbie Ubuntu User.

Thanks

---

