---
title: "install a printer on ubuntu..."
date: 2007-07-18
forum: Other OS Talk
---

### Post by hockey97 on 2007-07-18
HI I have a network in my house I used windows xp to create the network, the network also contains a networked printer, my dad's computer is windows 2000 pro and is the one that is hosting the printer, I have a network name which I used to install the printer on my other computers.

I need help becuse I done that in windows xp, my sister labtop I just installed ubuntu 7.04, and I want to install the printer my dad's computer is sharing, but don't know how to do it in ubuntu, 

my goal is to get my sister ubuntu laptop, to be on our network, that can see the shared files and shared printers on the home network.

---

### Post by lisati on 2007-07-18
One place to start is from the "System" menu - choose "Administration" then "Printing". Many popular printers are already supported by Ubuntu without the need for running to a driver disk, and there is an option for setting up a network printer. Let us know how you get on.

---

### Post by jonathanmotes on 2007-07-18
You have to install Samba on your Ubuntu machines before you can share files or printers hosted on Windows computers. Here's a pretty good tutorial for printing: [http://doc.gwos.org/index.php/Print_Windows_XP_machine](http://doc.gwos.org/index.php/Print_Windows_XP_machine)

Post if you have questions. I have done this a couple of times.

---

### Post by hockey97 on 2007-07-19
HI I was following that tutorial, when I go to my package manager thing, I get an error sayin VMware didn't install properly please reintall VMware, this also is shown when I click updates,
but when I go and try downloading VMware again and installing it I get an error, no permission or file is cruppted.

---

### Post by jonathanmotes on 2007-07-19
Well, I'm not sure what you mean - is it preventing you from installing Samba? Just uninstall VMware (using Add/Remove programs from the Applications dropdown) and continue on with installing Samba if you don't need VMWare for anything. I'm sort of a beginner myself, so I don't really know what you would do to fix the problem your having with it...sorry!

---

### Post by hockey97 on 2007-07-20
lol, well, what I am having is an error that won't let me run packag manager nor update manager.
I tried deleting it in the terminal, with ```
sudo apt-get remove VMware-player
```

is said that it done it , then I get an error saying that I need to reinstall VMware , missing archives.

and when I tried redownloading it and installing it I get an error no permissiosln or cruppted file, please redownload.

and I cleared the download window that firefox has.

I need somthing that I can fully  delete all files that relates to VMware.

right now I can't download nor update anything becuse of this error, becuse right after the error display's it then closes the program like update manager or package manager.

I really need the help,

---

