---
title: "skype installation problem with version 14.04"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by Sailordirk on 2014-09-10
I have choosen to replace my Windowsz XP OS with a Linux distro (which I wanted to do already for quite a while now).
Looking on different sites and fora the Ubuntu 14.04 appears to be the latest one so I have taken that one to install onmy laptop.
Amongst several other apps I also wanted to install Skype, but didn't find the 'right' version for this distro. On the Skype site I only found versions for:
- Ubuntu 10.04 32 bit
- Ubuntu 12.04 mulltiarch
- Debian 7.0 multiarch
- Fedora 16 32 bit
- OpenSUSE 12.1 32 bit
- Dynamic (?)
Tried number 1 and 2 but didn't even manage to open it.
Somebody could tell me what to do to get it working properly?
Which version should I take?
I hope I don't need to install a Windows version in a separate partition just to be able to use Skype?!
As a motivated newcomer to the 'Linux world' I may come up with some problems which may look easy to solve for more experienced users, but for me any help will be highly appreciated.
Thanks!

---

### Post by verymadpip on 2014-09-10
Hi there.
I installed Skype on a laptop running Xubuntu 14.04 from Software Centre.  It's in there & it's probably the easiest, most user friendly way of installing it.
I haven't actually used it for anything meaningful yet, but it seems to launch okay.

Oh, actually, there's been a failed file transfer, but that has also failed on Windows 7 & an Android tablet, so I don't think it's a Skype on *buntu issue.

---

### Post by Impavidus on 2014-09-10
Don't try downloading and installing skype manually. Open the software centre, click edit &#8594; software sources and find the canonical partner repositories. Enable them and then search in the software centre for skype. It should install with a single click.

Skype isn't included in the default repositories for license reasons.

---

### Post by marco-parillo on 2014-09-10
I have followed the 32-bit instructions here many times: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
Always resulted in a successful install, though I have only tested text chatting.

Are you trying to install from the Skype web site instead of the Canonical partner repository?

---

### Post by Pelvur on 2014-09-10
Had similar problem with updating the skype from 4.2 to 4.3. After several unsuccessful trials to install it from the website, I did exactly what Impavidus is suggesting. Works like a charm.

---

### Post by Sailordirk on 2014-09-10
Thanks for your quick help, but as mentioned above I'm a complete newcomer, so need one more word to solve the problem.
I opened the Software center but then I can't find this step/button: 'click edit &#8594; software sources and find the canonical partner  repositories. '
So could you please help me out one more time?
Thanks

---

### Post by cressrt2 on 2014-09-10
When you have the Softwar centre open, at the top of the screen you should see "File, Edit, View Help", click on Edit, then at the bottom of the list you should see "Software Sources", click on this and a new box will open called Software & Sources, the second tab is "other Software", here you will be able to select the Canonical partner repositories.

---

### Post by stalkingwolf on 2014-09-10
it can also be done with those directions from synaptic package manager.  The only step i see missing is after you edit the sources to add the partner repository you need to click the reload button.

---

### Post by uRock on 2014-09-10
I made a quick video of how to edit the software sources for you. [https://www.youtube.com/watch?v=HsKg2dw304c&feature=youtu.be](https://www.youtube.com/watch?v=HsKg2dw304c&feature=youtu.be)

---

### Post by craig10x on 2014-09-10
And be sure to check both "partners" boxes...and as you exit it will want to reload, so let it do that...once done, you can open the software center and type in skype and it will come right up...then you can install from there...

---

### Post by uRock on 2014-09-10
> **craig10x said:**
> And be sure to check both "partners" boxes...and as you exit it will want to reload, so let it do that...once done, you can open the software center and type in skype and it will come right up...then you can install from there...

Why both? I set the one repo and Skype installed perfectly.

---

### Post by craig10x on 2014-09-10
Oh really? I though both needed to be checked...at least that is what i read in some article about installing skype on ubuntu...what is the difference between the two boxes or are they just kind of a duplicate of each other?

---

### Post by uRock on 2014-09-10
> **craig10x said:**
> Oh really? I though both needed to be checked...at least that is what i read in some article about installing skype on ubuntu...what is the difference between the two boxes or are they just kind of a duplicate of each other?

I'm curious about it, too. I'm not/wasn't trying to be argumentative. One of them is supposed to be source code, but I've never really looked into the difference either.

---

### Post by craig10x on 2014-09-10
Oh i realize that....no problem ;)
But after you mentioned it, i unchecked the second one and just left the first one checked and skype still comes up in the software center...

That's why i was wondering if there was any difference between the two since both say the same thing...except one says source code as you said...
Well, i think i will re-check both as it doesn't seem to make much difference...

---

### Post by verymadpip on 2014-09-10
I didn't know the Canonical Partner repo needed to be checked.
Luckily for me I must have checked it for some other reason prior to installing Skype.
Good to know nonetheless.

---

### Post by Mike_Walsh on 2014-09-12
I'm running six distro's, all 'buntu-based. For me, the easiest way to install Skype 4.3, the most recent version, has been via the terminal; 

```
sudo apt-get install skype
```

Works every time. This is for 64-bit, however; not sure if this will work for 32-bit. I know there's some dependency issue whereby you have to install the 32-bit version, then remove it with 'apt-get remove skype', THEN install the 64-bit version; I believe this leaves behind some dependencies which the 64-bit version ALSO requires to be able to function. However, this was back in May/June, when 4.3 had only just been released; it seems to install straight off nowadays, from that single command. ;)

Asfar as I can tell, this also installs and sets up the correct partner repositories. For some reason, I have NEVER been able to find it in the Software Centre (probably because I haven't got around to adding the necessary repos); but why bother, when a single line in the terminal does it for you?

Regards,

Mike.

---

### Post by craig10x on 2014-09-12
@mike: prior to checking the boxes in the software sources for canonical partners, when i would check the ubuntu software center, skype did not come up in the search....once i checked the boxes, and reloaded the software sources (which it tells you to do as you exit it's window) then i checked ubuntu software center and skype comes up in the search...apparently, checking them brings it in...i would imagine when you installed it via terminal, it probably enabled them first...

---

### Post by Mike_Walsh on 2014-09-13
More than likely! I can't remember how I first found the info for installing Skype, but I know it wasn't through the wikis, or anything like that; I believe I simply Googled "install skype in Linux". I think I found the info on the How To Geek website; I didn't jib at using the information from that site, as I've always found it to be solid and reliable. Chris Hoffman, who runs the site, always talks you through the approved ways of doing things, never the dodgy ones; and his recommendation was simply to use the terminal, if you wanted the easiest way to get it up-and-running...

Yes, I know the purists may perhaps sniff a little bit, and tut-tut, and say I'm not really playing the game by following the time-honoured way of doing things, but as far as I'm concerned, if it works, doesn't damage the system in the process, and lets me get on with what I want to do, then I'll use that method. Besides, it doesn't matter which OS you're running; Windows, Mac, Linux, FreeBSD, Solaris, et al (and I've looked at just about EVERYTHING over the last 30 years), they ALL have about a zillion different ways of performing any given action..! And Linux, more than most, positively encourages you to USE those different methods.

'Multiple redundancy', I think it's called..!

Regards,

Mike.

---

### Post by redrumrogue on 2014-09-13
Hi there - to Sailordirk - when you say "Tried number 1 and 2 but didn't even manage to open it." what exactly did you do to try and open it and what actually happened?  Did you simply double click on the .deb file?  Did the ubuntu software centre open and you clicked "install"?  Or did you try to install via dpkg -i command?  Installing via dpkg command line might shed some light on the issue as you should see some kind of error message in the terminal if the install fails.  I have just recently installed Ubuntu Gnome 14.04 on my machine and installed Skype 4.3 from the "ubuntu 12.04" download off the Skype website.  As far as I remember there was some issues with dependencies so had to resolve that after ... try this please:

1.  Download Skype for Linux (Ubuntu 12.04 mulltiarch) from Skype website to your Downloads folder.
2.  Press CTRL + ALT + T to open a terminal window.
3.  cd ~/Downloads
4.  sudo dpkg -i ./skype-ubuntu-precise_4.3.0.37-1_i386.deb  (obviously replace the .deb file name here with the one you downloaded incase you download a slightly different version)
5.  sudo apt-get -f install
6.  try to open Skype ... fingers crossed!

I actually had another issue with skype after installing the latest stable nvidia driver from the nvidia site (v340.32).  During the installation of that I chose not to install the support for 32-bit applications and this stopped Skype from working.  Something to do with 32 bit OpenGL libraries ... I found that even though Skype had apparently installed without any issues, when I tried to open Skype nothing happened.  I reinstalled the nvidia driver with the 32bit support and all worked perfectly after that.  Forgive me if this nvidia driver issue is irrelevant!

Hope this helps!

---

