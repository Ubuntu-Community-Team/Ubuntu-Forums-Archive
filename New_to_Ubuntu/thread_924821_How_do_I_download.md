---
title: "How do I download?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by oz756c on 2008-09-19
I've been trying to download partygammon onto my laptop and am given a window which says, "You have Chosen to open PartyGammonSetup.exe which is a 'Bin File'". I'm given a choice to either "Cancel" or "Save File"...I chose Save File.

Next, a separate screen pops up under the heading of Downloads,allowing me to click on the aforementioned file which tells me that "the link needs to be opened with an application sent to:". I'm then presented with a list  of about 7 places to store the file. I opted for desktop. 

Yes, the file is on my desktop, but I cannot download the program. When I try to open, I just receive the same command message.

I know this issue must come across as completely idiotic, but I'm addicted to to this stupid game to the point that I shelled out big dollars for a new laptop when I could have had a quick (3 days) $100 fix for my old machine. Any help would be very much appreciated. Thanks,-oz756c-

---

### Post by howefield on 2008-09-19
partygammonsetup.exe is a windows setup file, are you trying to install into an Ubuntu setup ?

---

### Post by oz756c on 2008-09-20
Yes, sorry, it is Ubuntu I am trying to install onto. I take it that I will be unable install because it is a Windows program?

---

### Post by clive littlewood on 2008-09-20
Hi

This is a windows file and will not run in native Ubuntu.

Try installing WINE from add/remove programs and this is used to run windows programs on Ubuntu.

Hope this helps

cl

---

### Post by howefield on 2008-09-20
> **oz756c said:**
> Yes, sorry, it is Ubuntu I am trying to install onto. I take it that I will be unable install because it is a Windows program?

As the previous poster said, it may work in wine although I have just tried it and it didn't go well. Seemed to install but isn't working. YMMV.

To install Wine, go to applications > accessories > terminal and type the following two commands or use synaptic package manager.

sudo apt-get update
sudo apt-get install wine

Your best bet might be run it windows if you have such a machine, or a virtual machine.

---

### Post by howefield on 2008-09-20
Update to above, I tried it again in a 32 bit Ubuntu (previous install was 64 bit) and the game works fine as far as I can see. Just played my first backgammon game in years :) 

Needless to say, I lost.

---

### Post by oz756c on 2008-09-20
Got partygammon installed through WINE, but peculiarly, 1/4 of the playing board is sliced off. At the same time, the font of all my web pages have been reduced. Might there be a connection? Thanks

---

### Post by peterc26 on 2008-09-24
> **oz756c said:**
> Got partygammon installed through WINE, but peculiarly, 1/4 of the playing board is sliced off. At the same time, the font of all my web pages have been reduced. Might there be a connection? Thanks
oz756c, I had exactly the same problem a while ago with the side of the board missing and the wrong fonts and found it could be fixed by installing msttcorefonts:

sudo apt-get install msttcorefonts

However, as of yesterday Partygammon have released a new updated version of the client, and I've now encountered a completely separate problem.  The client will start and I can see the Lobby and the sign-in window, but when I sign in it just waits and waits without managing to sign in.  Any ideas anyone ?

---

### Post by peterc26 on 2008-09-25
I've managed to get the latest version of PartyGammon installed under Wine.  After trying many different things I found that it worked with Wine 1.1.5, but only after first installing IE6.  I haven't got it working perfectly yet - sometimes it struggles to join a game, but it's definitely a step in the right direction.

I used [PlayOnLinux]("http://www.playonlinux.com/en/") as a tool to try out different wine versions and different configurations - very handy.

---

