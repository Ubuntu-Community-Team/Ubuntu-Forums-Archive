---
title: "downloaded ppp, can't install"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by abooks on 2008-11-12
Can't get my 8.10'ed desktop to install the ppp-2.4.4.tar I downloaded from another machine. Apparently there is no Network under system admin, the Network manager can't be found. . .I've tried every command I could find in the forums sudo make, sudo install, sudo apt-get, etc, etc. After three days, I'm beat!

---

### Post by randy78 on 2008-11-12
The README files included with source packages usually have instructions on how to build and install the program...

When you download a source package, right-click on it>extract here

Open a terminal and navigate to the program folder
EXAMPLE
cd /home/yourUserName/Desktop/ppp.2.4.4

Next, type: ./configure

Then, type: make

Finally, type: sudo make install

As I stated above, you may want to read the README file, if it's included, as it will usually have specific instructions for building the program...

Good Luck :)

---

### Post by cariboo on 2008-11-12
PPP is install by default, so there is no need to compile it from source. use wvdial to detect your modem. In a Applications-->Accessories-->Terminal type:

```
sudo wvdial
```

This should detect your modem if the proper driver is installed. Wvdial will also allow you to dial your isp's phone number and connect. When I was on dial-up, many years ago I found that kppp was the best appliction to use to setup your dial-up configuration.

Jim

---

### Post by abooks on 2008-11-12
Entered sudo wvdial and got "WvDial: Internet dialer version 1.68/ Cannot open /dev/modem: no such file or directory".

Could there be pieces missing from my copy of 8.10? I seem to be getting a lot of these.

By the way, Cariboo, see my reply at Monty40 Installing Windows drivers to your question.
Leaving no stone unturned.

PS

---

### Post by abooks on 2008-11-12
The Readme file says "Assuning you are running a recent series kernel, the kernel source code will contain an up-to-date kernel ppp driver. If the ppp driver was included in you kernel configuration when your kernel was built, then you need only install the user-level programs. Otherwise you will need to get the souce tree for your kernel version, confgure it with the ppp included, and recompile." And so on. Nothing like "terminal, type. . ." which is my speed.  There are references to a ppp driver in 8.10, but none seem to appear or run when you ask them.

---

### Post by abooks on 2008-11-12
I should add, Randy78, that I tried every permutation of cd/home/your username/desktop that I could thing of, and all it said was no such file found. Tried doing after Extract and got the same message.

Thanks for trying, y'all! Don't give up!

PS What's the difference between Quick Reply and New Reply?

---

### Post by ugibuntu on 2008-11-12
You need to configure wvdial first
$ sudo wvdialconf
or configure it manually
$ sudo gedit /etc/wvdial.conf (refer to manual)

If you need GUI Version of dialup tool find gnome-ppp in ubuntu repository.
(Sorry my bad english)

---

### Post by randy78 on 2008-11-12
> **abooks said:**
> I should add, Randy78, that I tried every permutation of cd/home/your username/desktop that I could thing of, and all it said was no such file found. Tried doing after Extract and got the same message.

Thanks for trying, y'all! Don't give up!

PS What's the difference between Quick Reply and New Reply?

cd means Change Directory, there is a space between cd and the location...
cd/home/user/books =incorrect 
cd /home/user/books =Correct

[http://degreedirectory.org/articles/13_Of_the_Best_Linux_Tutorials_and_OpenCourseWare_on_the_Web.html]("http://degreedirectory.org/articles/13_Of_the_Best_Linux_Tutorials_and_OpenCourseWare_on_the_Web.html")

---

### Post by abooks on 2008-11-13
OK, I tried cd space home abooks, etc, and got the same message.

Per Ugibuntu, I tried sudo gedit, etc, and got prompts for "Dialer Defaults" phone, usrename, password, and New PPP=yes.

Then I tried sudo wvdial and it still said "not found."

Assuming I need to get a driver for my modem, how would I get it and how would I install it?

Somebody elese said from Live CD "you can open terminal and set up WV config- from terminal then wvdial and you will get modem online online and can download gnome ppp." I put in the CD, looked and couldn't find "terminal" or "Wv" or "Wv config." By setting up the "dialer defaults" am I doing a config? Then what do I do with it?

Forgive the density: it's past my bedtime. . .

---

