---
title: "Flashing Screen after boot menu on Old PC"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by MandelaPhilo on 2013-03-01
So, I just installed lubuntu on my friend's old HP 8500 Pentium 3 450Mhz/256MB Ram and I'm having an issue.  I selemct Ubuntu from the GRUB boot menu, and it begins the load screen.  After this it begins flashing a black screen with the following things on it:

*Checking battery state...                                                                                           [OK]
*Stopping System V runlevel compatibility                                                                      [OK]
*Starting                                                                                                                  [OK]


It never gets past this point.  I'm pretty savvy logistically, but I don't know programming or hardware lingo very well.  I should be able to figure out anything procedurally, but I won't be able to work with obscure reference points or extremely technical language.  This is my first time working with Linux.

I'm doing this for a friend before I leave town tomorrow morning, so any quick answers or hypotheses would be super great so I can try to work it out tonight.

Thank you all for your help in advance :-)

-Eric

---

### Post by tgalati4 on 2013-03-01
Can you boot into the rescue terminal?  It's in the GRUB menu that shows up right after the BIOS does it's RAM check.  Your machine barely has enough horsepower to run Ubuntu.  You would be better off running Lubuntu or Linux Mint MATE 32-bit.  It's possible that your processor does not support PAE--physical address extension, needed for the latest versions of Ubuntu.  If this is the case, then you would have to go back to an earlier version or find a distro that does not rely on PAE such as Puppy Linux.  You also need a swap partition (1 GB at least) because 256MB of RAM will run slooooow.

---

### Post by MandelaPhilo on 2013-03-02
The issue is with lubuntu.  If that is still too intensive a system, I suppose I should move on to Puppy Linux.  I don't know if I can get it on before I leave, but hopefully I can walk my friend through it.  Thanks.

---

### Post by mörgæs on 2013-03-03
It's very unfortunate that the PAE ghost is still popping its head up. Seems like a catch-all for any given hardware problem. 

There's no PAE problem here, as all Pentium 3's support PAE. In fact it's supported all the way from Pentium Pro except a certain branch of Pentium M.  

The problem here is lack of memory. You might be able to install using an alternate Lubuntu ISO, but the system will not be a pleasure to use.

---

