---
title: "Raspberry Pi4 (8GB): Unable to type text to search bar in Ubuntu"
date: 2021-08-07
forum: New to Ubuntu
---

### Post by tombeithemist on 2021-08-07
Hello, I am a complete newbie to ubuntu. I have just purchased my first Raspberry Pi4 (8GB) and installed Ubuntu 21.04 64 bit. Gnome Version 3.38.5 Windowing System - Wayland. I have booted the system up and have the basic desktop display on my Sony TV.
I have a number of issues that I cannot seem to resolve: 1). Everything seems to run really, really slow, incredibly long lag between clicking and any response. 2). I have registered my email address to connect to my online Google account but I cannot connect to my YouTube or Gmail accounts. It seems Ubuntu will not let me type text into the registration (email) field. 3). Unable to type text into Firefox search field or any other search field.
I have taken out the Sandisk Ultra 32GB SD card and re-formatted and re-installed Ubuntu but have the same issues still. I would be most grateful if anyone could suggest a remedy for this. By the way, I have zero programming skills!
Thanks in advance.

---

### Post by monkeybrain20122 on 2021-08-08
Login to xorg session. I think there is some issues with input in wayland. In the login screen click your user name, then click the ubuntu symbol in the lower right corner and choose ubuntu-xorg

---

### Post by tombeithemist on 2021-08-08
> **monkeybrain20122 said:**
> Login to xorg session. I think there is some issues with input in wayland. In the login screen click your user name, then click the ubuntu symbol in the lower right corner and choose ubuntu-xorg

Hi there! Thank you very much for your advice, I made the changes as suggested and it has solved the text entry issue, however applications are still slow to activate and YouTube is very laggy and screen image freezes quite often. Also resolution seems pretty poor even on 1080HD. Any suggestions as to why this is or am I expecting a little too much from the RPI4?
Thanks again for the assistance.

---

### Post by monkeybrain20122 on 2021-08-08
> **tombeithemist said:**
> Hi there! Thank you very much for your advice, I made the changes as suggested and it has solved the text entry issue, however applications are still slow to activate and YouTube is very laggy and screen image freezes quite often. Also resolution seems pretty poor even on 1080HD. Any suggestions as to why this is or am I expecting a little too much from the RPI4?
Thanks again for the assistance.
Sorry man don't know anything about RP. Hopefully someone more knowledgeable  can help you. Maybe you can start a new thread with a title more informative about your current issue with the RPI4.

---

### Post by ActionParsnip on 2021-08-08
I'd suggest a lightweight session like LXDE rather than the default Ubuntu session. It will use fewer resources and give you a more responsive desktop environment

---

### Post by TheFu on 2021-08-08
> **ActionParsnip said:**
> I'd suggest a lightweight session like LXDE rather than the default Ubuntu session. It will use fewer resources and give you a more responsive desktop environment

+1.  Gnome is terribly bloated on a Core i7 computer, I couldn't imagine running it on a R-Pi.  On my Ryzen, I find all DEs too bloated and run a simple WM-only setup. That's probably too hard for someone new, so you should look at xubuntu, lubuntu or Ubuntu-Mate desktops.  Please understand that cheap ARM SBCs are cheap and relatively low power compared to almost any x86-64 you could buy the last 5 yrs.  I have a 2015 Celeron that was $50 for the CPU+cooler and $50 for the motherboard, then $26 for RAM and it will blow away any raspberry pi.

---

### Post by tombeithemist on 2021-08-09
Thanks everyone for your assistance and suggestions. I think I need to go back to the drawing board and investigate those alternative desktop environments.
Cheers!

---

