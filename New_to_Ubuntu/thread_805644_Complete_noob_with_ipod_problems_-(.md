---
title: "Complete noob with ipod problems :-("
date: 2008-05-24
forum: New to Ubuntu
---

### Post by swedishpimp on 2008-05-24
Right, this is my first post and I'm only posting 'cos I've searched all over this forum looking for the answer and couldn't find it!!! :(

Right.  My Godchildren have managed to destroy three PCs through a potent combination of Limewire and pornography so I've installed Ubuntu on an old machine of mine so at least they'll have something to do their homework on.  Here's my problem...

They have iPods, and as a newbie, I've worked out that I need gtkpod to make them work.  I think I've managed to download the files I need to a USB stick but I don't know what to do from here.  In fact, there's a pretty good chance I *haven't* got the right files.  I've read the ReadMe files, double-clicked on all sorts on Install icons and nothing seems to be happening :-k

The machine I'm running Ubuntu on hasn't got access to the internet, so basically I'm looking for an idiot's guide walk-through on how to install gtkpod from either a stick or CD.  And when I say "idiot's guide", please feel free to be as clear/patronising as you like :lolflag:

I've also got another quick question.  If I connect their Epson C48 printer (via USB), will Ubuntu "see it"?  Does the OS come preinstalled with popular drivers or is this another little minefield for me to fall flat on my face on?

*Any* assistance would be of great help, but please be gentle with me - I've never used anything apart from Windows and I'm a happily self-procalimed Luddite.

If (and there's a pretty good chance) I've asked a question that's been asked and answered a million times before, then many apologies.  Mods - feel free to lock the thread but at least give me a link to the answer!

---

### Post by MattBD on 2008-05-24
As long as you've already added MP3 support by installing the package ubuntu-restricted-extras, you should just be able to add gtkpod and I don't think there's anything else you need.

You can install it by downloading it to your /home directory and entering the following at the terminal:
```
sudo dpkg -i *.deb
```
Make sure that there aren't any other deb packages in the directory as the * (wild card) means it will install any deb packages located there.

If their iPods have tracks in AAC format, you might need to install gtkpod-aac instead, which supports this format.

---

### Post by MattBD on 2008-05-24
Nearly forgot the printer - many peripherals will work straight away when you plug them in as the drivers are often included in the Linux kernel. Asa general rule, old hardware tends to work better as the drivers are more likely to be available.

---

### Post by clive littlewood on 2008-05-24
Hi

After installing the mp3 codecs ect. I would recommend installing Amarok player. This is a great program for ipod management and you can transfer songs both ways from and too your ipod, unlike itunes.
Amarok can be installed from add remove or synaptic.

Happy listening !!

Clive

---

### Post by StaceyRVC on 2008-05-24
I definitely recommend amarok, its what i use to sync all of my iPod's

---

### Post by MattBD on 2008-05-24
> **StaceyRVC said:**
> I definitely recommend amarok, its what i use to sync all of my iPod's

I'd go along with that, but getting Amarok set up on an Ubuntu install without an Internet connection could be problematic. In this case, probably the best thing to do is use Linux Mint instead of Ubuntu as it has all the codecs already and Amarok preinstalled.

---

