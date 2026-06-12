---
title: "GnuPG?"
date: 2006-01-13
forum: Repositories &amp; Backports
---

### Post by seakiwi on 2006-01-13
Hi

I've been trying to find GnuPG in my repositories but all I can find is one that says "in development, not recommended for general use".

Can someone please tell me how I can install whichever version is the latest stable release?

I've tried apt-get GnuPG but it doesn't find anything?

Is there a free PGP version for Linux btw?

---

### Post by encompass on 2006-01-13
HAHA, oh yeah... very much so.... linux IMO is the best at these keys.  I would google how to create your own gpg key.  I use it alot in my business for added security.  gpg not pgp  there may be a pgp key maker, but I don'&#228;t even know the difference right now.
look up gpg in synaptic.  There are many options.

---

### Post by seakiwi on 2006-01-14
[QUOTE=encompass]HAHA, oh yeah... very much so.... linux IMO is the best at these keys.  I would google how to create your own gpg key.  I use it alot in my business for added security.  gpg not pgp  there may be a pgp key maker, but I don'ät even know the difference right now.
look up gpg in synaptic.  There are many options.[/QUOTE]

I already have keys. I've been using both PGP and GnuPG in Windows for years now so I'm familiar with the concept.

I did a search with Synaptic but only came up with one entry for GnuPG - with a note that it was still under development and not recommended for general use. 

What I need to know is where to find a version that **is** stable for general use, then I need some help with installing it and setting it up, especially if it's a command line version. I'm new to Linux - learning fast but still far from being a geek ;)

---

### Post by jsmidt on 2006-01-14
I suggest the package GPA.  It handles all your GnuPG stuff for you. And is graphical. :)

---

### Post by seakiwi on 2006-01-14
[QUOTE=jsmidt]I suggest the package GPA.  It handles all your GnuPG stuff for you. And is graphical. :)[/QUOTE]

OK, thanks for that. I installed it and it looks like what I was looking for **but** something's not right with what I've done. I imported my keyrings ok - both my keys and other public keys I need. But how do I set up the actual GnuPG part of this? I need to somehow get my passphrase into it. I've installed GnuPG and it's there, but I don't have a clue how to run it or access it to tell it what my passphrase is.  Nothing will work without it obviously.

I'm guessing that somehow I have to open GnuPG via terminal and set up options in it before using it via the GUI, but nothing I've tried works. My knowledge of commands is pretty basic - how do I do this? :???:

EDIT: OK, rather than mess around for hours trying to figure out how to do this, I just created a new key. But something's still not right. 

1. I can't decrypt any messages I've encrypted and sent. I've always preferred to save sent encrypted messages encrypted so that's the option I selected, but if I try to decrypt them I get a bad passphrase error.

2. Recipients can decrypt my messages but there is no signature validation field anywhere for "good" or "bad" signature, so they can't tell if the message has been tampered with.

3. I'm using Kmail (as part of Kontact). When I go to configure Kmail, then Cryptobackend, Open PGP (gpg) is checked there, but the "configure" button is greyed out. I can't get in there to configure anything. There is no right click menu or anything if I click on the Open PGP (gpg) entry.

Maybe there's something else I need - a dependency or plugin - that I haven't got installed? When I installed GnuPG and GPA I made sure I checked all the required and suggested dependencies but maybe I missed something?

This is driving me crazy!  Can somebody **please** help me sort this out?

---

### Post by jsmidt on 2006-01-14
Try these packages, kgpg and seahorse.  Kgpg is like gpa for KDE.  Seahorse is like gpa for gnome.

---

### Post by seakiwi on 2006-01-14
[QUOTE=jsmidt]Try these packages, kgpg and seahorse.  Kgpg is like gpa for KDE.  Seahorse is like gpa for gnome.[/QUOTE]

OK, I installed Kgpg and much prefer it to gpa but I still can't get this to work with KMail. 

Can someone please tell me how to set it up so that I can use GnuPG directly from within KMail?  Is just will not work the way I'm used to in Windows - maybe it's not supposed to but it's making me nuts!

More questions ... sorry :( 

1. If I choose to save encrypted messages I've sent - in their encrypted form, rather than in plain text - HOW do I decrypt them again if I want to read them? So far I cannot manage to do this without saving them to a file, decrypting them from there, then copying them back into my mail folder. Needless to say that's a novelty that will wear off **very** quickly! 

I want to be able to select a sent encrypted mail, decrypt it within KMail, read it, then have it remain encrypted in my Sent folder once I've finished with it. How do I achieve this?

2. Recipients are still getting no indication of "good" or "bad" signature - which kind of defeats the purpose of encrypted email. Is this normal behaviour under Linux?

3. Does anyone know of a tutorial anywhere on integrating GnuPG with KMail? I've read the manual but I can't see anything in there to indicate that I've done anything wrong or omitted anything.

4. Which mail client do most of you use with GnuPG? If there is a better one that has better integration with GnuPG - then I'd be happy to switch.

I'm sorry for being a PITA but I really need to get this working properly. ANY suggestions gratefully received.

Many thanks!  O:)

---

### Post by maxomai on 2006-01-14
I can't seem to find kgpg for some reason? :(

Apparently I'm not the only one who's had this problem recently either -- did they just put a fixed package out there?

---

### Post by seakiwi on 2006-01-14
[QUOTE=maxomai]I can't seem to find kgpg for some reason? :(

Apparently I'm not the only one who's had this problem recently either -- did they just put a fixed package out there?[/QUOTE]

I did an apt-get install kgpg and found it that way. I much prefer it to gpa.

I'm going to do some googling and see if I can find a tutorial on how to get this setup properly and working. If I find anything I'll let you know. What email client are you using just out of interest?

---

### Post by maxomai on 2006-01-14
[QUOTE=seakiwi]I did an apt-get install kgpg and found it that way. I much prefer it to gpa.

I'm going to do some googling and see if I can find a tutorial on how to get this setup properly and working. If I find anything I'll let you know. What email client are you using just out of interest?[/QUOTE]

I"m using KMail.

NB, apparently the fix has something to do with adding additional repositories to /etc/apt/sources.list. I'm googling for a solution myself right now, and I'll post here if I find it.

---

### Post by seakiwi on 2006-01-14
[QUOTE=maxomai]I"m using KMail.

NB, apparently the fix has something to do with adding additional repositories to /etc/apt/sources.list. I'm googling for a solution myself right now, and I'll post here if I find it.[/QUOTE]


OK, I've got it sussed! (I think) \\:D/ 

Firstly, this is assuming you have kgpg installed and your keys imported/created ok. Once you have that setup the way you want it, go to KMail and check that under Configure KMail, Security, Cryptographic Backends - check that Open PGP (gpg) is checked. I also have S/MIME (gpgsm) checked (not sure whether you need that or not or how it even got there)

Then, when you go to compose a new message, in the message composer window, check under Options, Cryptographic Message Format, and select Open PGP Inline (deprecated).

Then compose your message and when you're done, select the sign, encrypt or both buttons at the top, then hit Send. It will ask you which public key to encrypt to (if you're encrypting), then it will ask you for your passphrase. Once you've done that it will send the message.

If you look for that message in your Sent Folder, and you encrypted it, as soon as you click on it, a box will pop up for your passphrase - then it will show you the decrypted contents, plus the signature/encryption validation. If you only signed the message you can click on it and you'll see the message as usual with the signature validation. It's all very bright and colourful  ;) 

I've tested a signed and encrypted message with a friend - and it showed up fine with a good signature. The secret seemed to be checking the OpenPG inline (deprecated)  option. Unfortunately it seems that you have to check that for every message manually - doesn't seem to be an option to save that setting for all mail. 

Hope that helps!  **NOW **I can go have my breakfast!  Don't you hate it when you can't "put something down" until you've got it sussed?!  ;) :D

---

