---
title: "Any ISO programs?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Graahl on 2008-06-13
Hello, I was wondering if there are any iso programs for Ubuntu. And if so, which are there to choose from?

---

### Post by _sphinx_ on 2008-06-13
I think I didn't understand your question but any ways Matlab comes with iso packed, also you can yourself make a program to be iso, mount it and run.

---

### Post by Graahl on 2008-06-13
Well I am looking for any mount programs like Deamon tools or PowerISO.

---

### Post by Joeb454 on 2008-06-13
What do you mean iso?

Do you want the program to create .iso files? Or do you want the program to be able to burn the .iso images to a disc?

Edit: Nevermind :p

---

### Post by mali2297 on 2008-06-13
See [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

---

### Post by Graahl on 2008-06-13
Thanks alot for the help, both of you :D

---

### Post by _sphinx_ on 2008-06-13
Ohk, well you can manually mount iso file by just one command. I mount Matlab with:
```

sudo mount file.iso /media/iso/ -t iso9660 -o loop

```
-t is for specifing  the file type. You can read man mount for more details.
Any ways I don't know anykind of program like daemon tool in linux

---

### Post by gtdaqua on 2008-06-13
> **_sphinx_ said:**
> Ohk, well you can manually mount iso file by just one command. I mount Matlab with:
```

sudo mount file.iso /media/iso/ -t iso9660 -o loop

```
-t is for specifing  the file type. You can read man mount for more details.
Any ways I don't know anykind of program like daemon tool in linux

This does what daemon tools or Alcohol does in Windoze. Linux is command line based and comes handy once you know it.

---

### Post by Bradtek on 2008-06-13
In Synaptic search for and install gmountiso
> 
This is Gmountiso, a PyGTK GUI to mount your cd images
Gmount-iso is a small tool written using PyGTK and Glade. It allows you to
easily mount your cd images. This is a frontend to the 'mount -o loop -t
iso9660 foo.iso /mountpoint' command

---

### Post by Joeb454 on 2008-06-13
> **gtdaqua said:**
> This does what daemon tools or Alcohol does in Windoze. Linux is command line based and comes handy once you know it.

1) Why use "Windoze"  It's just pointless...

2) Linux *can* be command line based, but it doesn't have to be, there's a GUI for most things nowadays, CLI things are just easier to give online.

---

### Post by atomkarinca on 2008-06-13
Check out [Acetoneiso2]("http://www.acetoneiso.netsons.org/").

---

### Post by hyper_ch on 2008-06-13
> **Joeb454 said:**
> CLI things are just easier to give online.

And faster than navigating through hundres of windows and menus and options ;)

---

### Post by Joeb454 on 2008-06-13
> **hyper_ch said:**
> And faster than navigating through hundres of windows and menus and options ;)

Well yeah that too :) Only problem is it puts some people off...

---

### Post by marcusfurius on 2008-06-21
If you want to mount iso images (or other types) you could try [Furius ISO Mount]("http://www.marcus-furius.com/?page_id=14"). It is a simple Gnome (gtk) application designed specifically for this purpose, and it doesn't require any KDE libraries unlike Acetone2.

---

### Post by bulletxt on 2008-06-22
AcetoneISO2 does NOT require any kde dependencie.

---

### Post by Troll_the_Great on 2008-06-22
You can try Kiso too...It's pretty good and has a nice interface.

---

### Post by Tomatz on 2008-06-22
Acetoneiso

Its like daemon tools (kind of). You can get it here:

[http://www.acetoneiso.netsons.org/](http://www.acetoneiso.netsons.org/)

---

