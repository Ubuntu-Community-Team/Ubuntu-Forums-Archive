---
title: "A few issuse with graphic driver and running OS"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by charles17 on 2014-01-22
The computer I'm on is a Dell Dimension 2350 1.8gb processor and 1gb Ram, The chipset is the Intel 845gl. The issue with the graphics driver is that the pc don't have one and I need to be able to install one. That is one issue, another issue is that the Ubuntu 13.10 i386 I have installed will boot but it only boots to a blank screen that all you see is the wallpaper. I created a new folder giving me limited options.  I'm on that pc now. I can only access firefox by acting like I want to install something with firefox. Visiually it don't look like it has a graphics issue until you try to watch a video. I can't install anything because I don't have a program to do that, the archive manager don't help at all, and if I try to use the sudo apt-get it can't locate what I want installed. These are the first couple issues that I would like help with. Any help at all would be great. Thank you.

---

### Post by deadflowr on 2014-01-22
The driver is already installed.
It's built into the system.

Your problem is more of the fact that it is an old card and not the best for running Ubuntu.
You might have better luck with a lighter Ubuntu variant such as [lubuntu]("http://lubuntu.net/") or [xubuntu]("http://xubuntu.org/").

On my other box I have the 910gl card(or something like that) it's the oldest intel card I've gotten to run Ubuntu.
On a box I have since let go, I had the 845gl card and like yourself, it ran like garbage.
Lubuntu, however ran perfectly.

---

### Post by charles17 on 2014-01-22
I have been working on computers for over 10 years, it don't have the graphics drivers because someone destroyed the system before I got it. I had to rebuild some of it and the drivers for the graphics is always an issue when I replace the OS. I have to reinstal everytime. I have thought about a lighter version to this Ubuntu but I guess I could try the lubuntu.

---

### Post by deadflowr on 2014-01-22
Like I said, the graphics drivers are built into the operating system.
It's part of the xorg packages.
Intel graphics drivers are part of that package.

With exception of someone physically damaging the hardware, whether or not they destroy the software is irrelevant. The drivers will be installed when the system is installed.

---

### Post by charles17 on 2014-01-22
I installed Lubuntu. Now, after the update it won't let me use my password and log into the system. It's acting as though it's stuck in a loop at the log in. How do I fix this?

---

### Post by deadflowr on 2014-01-22
> **charles17 said:**
> I installed Lubuntu. Now, after the update it won't let me use my password and log into the system. It's acting as though it's stuck in a loop at the log in. How do I fix this?

I think the standard procedure is to check to see if the .Xauthority file is owned by the user.
Despite the loop going on, you can still access the system by running this
press crtl+alt+F1, or F2> up to F6.(any of these will do)
Now, you should have a login prompt.
enter the username and then, when asked the user's password.
You should now have a session going.
then follow this
[http://askubuntu.com/questions/189399/cannot-get-past-login-screen](http://askubuntu.com/questions/189399/cannot-get-past-login-screen)

See if that helps.

---

### Post by charles17 on 2014-01-22
I tried all the same ways as the others and no luck. I am thinking about reinstalling and updating at the same time to see if that renders a better result with the log in. Unless there is another way that I can do it to save time other than the fore mentioned.

---

