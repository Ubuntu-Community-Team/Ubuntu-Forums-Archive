---
title: "Ubuntu Software Centre"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by MiloWhippet on 2011-10-15
I cannot get Ubuntu Software Centre to work on this laptop. I am using a wireless connection for a home network. I can use email and surf the net but whenever I try to use Ubuntu Software Centre I try to click in an icon and all I see is an annoying symbol which never disappears. This means I cannot download any software from Ubuntu Software Centre.

---

### Post by westie457 on 2011-10-15
> **MiloWhippet said:**
> I cannot get Ubuntu Software Centre to work on this laptop. I am using a wireless connection for a home network. I can use email and surf the net but whenever I try to use Ubuntu Software Centre I try to click in an icon and all I see is an annoying symbol which never disappears. This means I cannot download any software from Ubuntu Software Centre.

Welcome to the Forum.

Which particular annoying symbol would that be. Could you post a screen shot of it please. To take a screenshot either press the PrtSc key or Alt+PrtSC. Then in a new reply click on the Paperclip at the top of the pane and follow the prompts to upload.

Thank you.

---

### Post by MiloWhippet on 2011-10-15
Thanks for your interest. I am having problems trying to use print screen to capture the image of this symbol but a verbal description should suffice. This is an animated symbol with lines radiating out to form a  small circle. Each line flashes in turn and at the moment they will go on flashing forever. 

I never get to see the next screen with icons for different applications.

When I was living at home I used the blue cable from my internet hub and I put it straight into the back of my computer. Ubuntu Software Centre worked fine but I am staying with my mother for a few weeks. She is 81. I do not want to upset her by messing around with her hub, especially as I do not quite know what I am doing.

The local computer technician showed me how to get the wireless connection up and working. I have mail and I can use Firefox but I cannot use Ubuntu Software Centre. If need be I can live with this until I go home but I curious to know if there is a solution.

---

### Post by westie457 on 2011-10-15
> **MiloWhippet said:**
> Thanks for your interest. I am having problems trying to use print screen to capture the image of this symbol but a verbal description should suffice. This is an animated symbol with lines radiating out to form a  small circle. Each line flashes in turn and at the moment they will go on flashing forever. 

I never get to see the next screen with icons for different applications.

When I was living at home I used the blue cable from my internet hub and I put it straight into the back of my computer. Ubuntu Software Centre worked fine but I am staying with my mother for a few weeks. She is 81. I do not want to upset her by messing around with her hub, especially as I do not quite know what I am doing.

The local computer technician showed me how to get the wireless connection up and working. I have mail and I can use Firefox but I cannot use Ubuntu Software Centre. If need be I can live with this until I go home but I curious to know if there is a solution.

Absolutely no idea why it takes so long to load, things do speed up when it has been loaded a few times.

A lot of users prefer Synaptic Package Manager and/or the command line to install things.

Open a terminal -Ctrl+Alt+t and type in ```
sudo apt-get install synaptic
``` you will be asked for your password. Nothing will show on the screen as you type.

Everything is there except for pay to use apps.

With Synaptic you get to see exactly what is installed with the app you want.

---

### Post by MiloWhippet on 2011-10-16
Everything was fine in terminal until this message appeared. 

Reading package lists...Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This is a new installation of Ubuntu. Am wondering whether I should reinstall. Very little data on disc.

---

### Post by d4m1r on 2011-10-16
> **MiloWhippet said:**
> Everything was fine in terminal until this message appeared. 

Reading package lists...Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This is a new installation of Ubuntu. Am wondering whether I should reinstall. Very little data on disc.


Restart the PC and try it again. Are you on wireless? Make sure your internet connection is stable but that might be a 1 time error...

---

