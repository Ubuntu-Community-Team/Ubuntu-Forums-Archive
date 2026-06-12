---
title: "Network traffic analyzer"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by speedzor on 2008-08-24
hi,

as I like reading things like data, I'd like to have a program that analyses all the network traffic, not just on my pc, but the whole homenetwork. A GUI is preferred.
Does anyone know some sort of program like this?

I'm using Ubuntu 8.04 with gnome.

greetings,
speedzor

---

### Post by Too Late on 2008-08-24
[http://www.wireshark.org/](http://www.wireshark.org/)

You can install it with Synaptic.

edit: Btw. you have to run that with gksudo to get all the features.

---

### Post by porchrat on 2008-08-24
wow awesome piece of software that.  Thanks

---

### Post by speedzor on 2008-08-24
this program seems nice, but when I try to set this up to analyze my network, it doesn't work.
At every place where i can scan for devices, it doesn't show my network..

---

### Post by Too Late on 2008-08-24
> **speedzor said:**
> this program seems nice, but when I try to set this up to analyze my network, it doesn't work.
At every place where i can scan for devices, it doesn't show my network..
Yes, as I said above, the program must be launched with gksudo. That gives you the necessary root permissions. So go to terminal and type:
```
gksudo wireshark
```
If you want to change your menu item so that it always starts with root permissions, go to System -> Preferences -> Main Menu and right-click the wireshark entry and edit it as stated.

---

### Post by hyperhopper on 2008-08-24
sorry to but in, but i was trying this too, and what do you mean by "edit it as stated"

---

### Post by Too Late on 2008-08-24
> **hyperhopper said:**
> sorry to but in, but i was trying this too, and what do you mean by "edit it as stated"
Lol sorry I don't speak English very well, don't care about that.:popcorn:

Anyway, when I start wireshark without root permissions, I can't see any interfaces/devices/networks there, so I was sure that you had the same issue. But if you already tried gksudo and it still didn't work, I don't know.

---

### Post by hyperhopper on 2008-08-24
now im really confused. all I want to know is how do you have wireshark start by default with the root permissions?

---

### Post by speedzor on 2008-08-24
install wireshark by stated above how to. (sudo apt-get install wireshark).
Typ the following in terminal:
```
gksudo wireshark
```

now you'll be able to select the network you want.

after that, go to system, preference, main menu.
When clicking on the tab 'internet', you'll see wireshark as an available option.
Right click on it, and at the text field with 'wireshark' in it, and 'command' in front of it, you can typ 'gksudo wireshark'.

solve out?

---

### Post by Too Late on 2008-08-24
> **hyperhopper said:**
> now im really confused. all I want to know is how do you have wireshark start by default with the root permissions?
Well, I assume that you want to start it by going to Applications -> Internet -> Wireshark, right?

Ok, now go to System -> Preferences -> Main Menu. Select Internet from left. Press Wireshark with right mouse button, and select Properties. In the Command field, there is only "wireshark" by default. Add a word "gksudo" in the beginning of that field, so that there will be "gksudo wireshark" in the Command field.

edit: I was too late.

---

### Post by hyperhopper on 2008-08-24
lol! I must double thank you!

---

