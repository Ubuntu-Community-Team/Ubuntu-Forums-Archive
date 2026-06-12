---
title: "Making softwear and Programs."
date: 2010-07-21
forum: Programming Talk
---

### Post by jwflammer on 2010-07-21
I have been getting interested in the making of programs for Ubuntu. i don't know Java but i Know C++ pretty well. i have code::blocks installed, and i have got that down. I would like to build a program that just dose simple stuff for now,and i have know idea were to start. Id like to see it be close to a windows .exe as possible i.e. when i double click the file it opens and runs. Any suggestions were to go or were to start? id like to make my first playing card game then go from there.


thanks jonny5

---

### Post by shadylookin on 2010-07-22
sudo apt-get install build-essential

that will give you the g++ compiler. If you used the standard libraries you can take the programs you have written for windows and compile it on Ubuntu. 

You'll have to change the permissions to allow for executing before you can actually run it though.

---

### Post by jpmelos on 2010-07-22
> **shadylookin said:**
> You'll have to change the permissions to allow for executing before you can actually run it though.

I don't think it's necessary if you are just testing a program after compiling it... When I compile my programs, I just run the command to run the program (**./a.out**, for instance) and it runs... Unless when I send it to some folder in the PATH to be executed as a simple command calling the name of the file, which I have to do **sudo chmod +111 /some/folder/a.out** to make it executable...

---

### Post by nvteighen on 2010-07-22
> **jwflammer said:**
> I have been getting interested in the making of programs for Ubuntu. i don't know Java but i Know C++ pretty well. i have code::blocks installed, and i have got that down. I would like to build a program that just dose simple stuff for now,and i have know idea were to start. Id like to see it be close to a windows .exe as possible i.e. when i double click the file it opens and runs. Any suggestions were to go or were to start? id like to make my first playing card game then go from there.


thanks jonny5

If you're talking about graphical apps, you should know that to achieve that, you'll need to use any of the GUI "toolkits" available: GTK+ (GNOME, Xfce), Qt (KDE) or others such as Motif, GNUStep, whatever. Bear in mind that nothing prevents to use any GUI toolkit in any Desktop Environment... the correlations I've written above just reflect what DE uses as its "default" or "official" GUI toolkit.

---

