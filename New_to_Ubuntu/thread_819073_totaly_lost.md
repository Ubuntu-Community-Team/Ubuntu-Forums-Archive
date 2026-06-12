---
title: "totaly lost"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by grey1 on 2008-06-05
Need some help. Have been trying to install, 8.04 LTS (Hardy Heron), that I downloaded off the net. Finally got the program installed, I think. I rebooted ater the install with disk out and I got a log in statment. Now I have a prompt as if I am in terminal.
All I find is sudo passwd root. Can't get out of this area to run anything....
:confused::confused::confused:

---

### Post by ramjet_1953 on 2008-06-05
Did you download and install the Desktop, or Server iso?

Regards,
Roger :cool:

---

### Post by HunterThomson on 2008-06-05
How did you install it? Through he winindw$ thing or did you reboot into the live cd and install in that.

---

### Post by grey1 on 2008-06-05
> **ramjet_1953 said:**
> Did you download and install the Desktop, or Server iso?

Regards,
Roger :cool:

***Desktop***

---

### Post by HunterThomson on 2008-06-05
> **ramjet_1953 said:**
> Did you download and install the Desktop, or Server iso?

Regards,
Roger :cool:

Aw... Yes that mite be what you did....

---

### Post by bumanie on 2008-06-05
Possibly a graphics card problem. Try ctrl+alt+F7, this should get you out of console mode and should start xserver. If not reboot and choose safe graphics at the grub stage. If you can then enter ubuntu go to System --> Hardware Drivers and install the restricted driver. Then reboot and see if things work.

---

### Post by grey1 on 2008-06-05
> **HunterThomson said:**
> How did you install it? Through he winindw$ thing or did you reboot into the live cd and install in that.

***Installed it off the CD that I burnt off from the download I got off the ubuntu site.***

---

### Post by grey1 on 2008-06-05
> **bumanie said:**
> Possibly a graphics card problem. Try ctrl+alt+F7, this should get you out of console mode and should start xserver.

**ctrl+alt+F7  has no responce , , I can't seem to get past** - **[SIZE="4"]Manual page sudo_root(8) line 96/124 (END)[/SIZE]** -

---

### Post by lisati on 2008-06-05
> **grey1 said:**
> ***Installed it off the CD that I burnt off from the download I got off the ubuntu site.***

There are a different kinds of download from the Ubuntu site, the "Server" version goes straight to the command prompt, the "Destkop" version normally provides the necessary extras to give you a "Desktop".

---

### Post by HunterThomson on 2008-06-05
> **grey1 said:**
> **ctrl+alt+F7  has no responce , , I can't seem to get past** - **[SIZE="4"]Manual page sudo_root(8) line 96/124 (END)[/SIZE]** -

I'd just reboot into the live desktop..... Then click the Install Icon on the desktop. Wehn you get to the partitioning section chose the manual install. Then click on the partition that is the ext3 Ubuntu partition and delete it. Then click make new partition make it 2000MB and select the SWAP format and then make a new partition and let it use all the free space all the free space (default) and name it "/" witch will be a root partition chose the ext3 format.

---

### Post by grey1 on 2008-06-05
[B]Rebooted the laptop with cd out, as prompted by the download. A dos looking screen loaded up andf asked for username and password, after which I get a :~$ and promt.  Now what ? ? All I know of ubuntu is that if I try anything TECH with it, I end up reloading from the CD once more to even get a screen back.
[/B]

---

### Post by darth_indy on 2008-06-05
OK, people, let's simplify it. Poor guy's new here. :-)

Here's a easy setup guide for installing Hardy, with step-by-step screenshots and everything.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

You only need to follow page 1 for the install, but it may be handy to do the rest of the guide. If you still don't get a desktop, and only get the CLI (Command-Line Interface, what you refer to as a "DOS-looking screen"), then post back, and we can get to work troubleshooting.

I do hope the above guide helps fix the problem though! It sounds like something went wrong in the installation.

---

### Post by grey1 on 2008-06-05
I must have downloaded a different program. I only got the first two window type screens then the rest were blue with white screen. All seem to go fine untill I restart the laptop. Then it's back to the CLI screen.

---

### Post by avtolle on 2008-06-05
> **grey1 said:**
> I must have downloaded a different program. I only got the first two window type screens then the rest were blue with white screen. All seem to go fine untill I restart the laptop. Then it's back to the CLI screen.
It does seem to me from your description that somehow you either have a server install on the HDD or for some very strange reason, the desktop isn't being installed. I'd bet on the first option, were I a betting man. 

Since you are at the command line, type "startx" without the quotes, of course, and let us know if you get an error message.

---

### Post by grey1 on 2008-06-05
The program 'startx' is currently not installed. You can install it by typing: sudo apt-get install xinit
-bash: startx: command not found

:~$ _

---

### Post by avtolle on 2008-06-05
> **grey1 said:**
> The program 'startx' is currently not installed. You can install it by typing: sudo apt-get install xinit
-bash: startx: command not found

:~$ _
Sounding more and more like somehow you have a server install going there. From terminal```
sudo aptitude update && sudo aptitude install xorg
``` which will install the X window system. Then, assuming this doesn't kick an error message saying it is already installed, from the terminal```
 sudo aptitude install ubuntu-desktop
``` to install the standard Gnome install.

Alternatively, you might download a fresh iso (Desktop or Alternate install), burn it to CD and install again, after reformatting the HDD to remove the current installation. I expect others to have solutions that may well be better, so fire away, folks.

---

### Post by grey1 on 2008-06-05
Now the screen says: Please select the mail server configuration type that best meets your needs

---

### Post by avtolle on 2008-06-05
> **grey1 said:**
> Now the screen says: Please select the mail server configuration type that best meets your needs
Yep, sounds like you've a server install there. At what point did you get that message (you can skip this, BTW)?

---

### Post by darth_indy on 2008-06-05
Yup, you've got a server install CD there. You'll need to download the desktop ISO and burn a new disc. Here's a link to one of the mirrors:

[http://mirrors.gigenet.com/ubuntu/8.04/ubuntu-8.04-desktop-i386.iso](http://mirrors.gigenet.com/ubuntu/8.04/ubuntu-8.04-desktop-i386.iso)

Then you can follow the guide. Good luck!

Edit: In reply to the message above, I'm not sure you'll need to reformat before using the new disc, just have the new disc reformat the partition itself.

---

### Post by avtolle on 2008-06-05
> **darth_indy said:**
> Yup, you've got a server install CD there. You'll need to download the desktop ISO and burn a new disc. Here's a link to one of the mirrors:

[http://mirrors.gigenet.com/ubuntu/8.04/ubuntu-8.04-desktop-i386.iso](http://mirrors.gigenet.com/ubuntu/8.04/ubuntu-8.04-desktop-i386.iso)

Then you can follow the guide. Good luck!

Edit: In reply to the message above, I'm not sure you'll need to reformat before using the new disc, just have the new disc reformat the partition itself.
Yep, Darth_Indy, as pointed out in your Edit; that's what I was inarticulately trying to say earlier.

---

### Post by tedrogers on 2008-06-05
Grey...when you get your i386 or Desktop whatever version installed...you will be impressed.

Just follow the guides suggested.

As a newbie I'm impressed by your determination to stick with this, even when faced with the command-line prompt from the start!!

If you see the 'X' in the middle of the screen then you know you're in business. :)

---

### Post by grey1 on 2008-06-05
> **darth_indy said:**
> Yup, you've got a server install CD there. You'll need to download the desktop ISO and burn a new disc. Here's a link to one of the mirrors:

[http://mirrors.gigenet.com/ubuntu/8.04/ubuntu-8.04-desktop-i386.iso](http://mirrors.gigenet.com/ubuntu/8.04/ubuntu-8.04-desktop-i386.iso)

Then you can follow the guide. Good luck!

Edit: In reply to the message above, I'm not sure you'll need to reformat before using the new disc, just have the new disc reformat the partition itself.


Well, tryed this and now the lap is loading the correct '8.04-desktop-i386.iso' now 
:grin:
Thanks

---

### Post by darth_indy on 2008-06-05
You're quite welcome! Always glad to help another member of the Ubuntu community.

---

