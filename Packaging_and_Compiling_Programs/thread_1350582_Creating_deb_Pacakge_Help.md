---
title: "Creating deb Pacakge Help"
date: 2009-12-09
forum: Packaging and Compiling Programs
---

### Post by dani_b1 on 2009-12-09
[COLOR=black][FONT=Verdana]Hi[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am using Ubuntu 9.10[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I would like to build a deb package.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]the pacakge will contain:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1. kernel driver[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2. script - i would like it to be install in /etc/init.d [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]3. application - I would like it ot be install in /usr/bin directory[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I understand there are three component [/FONT][/COLOR]
[LIST=1]
[*][COLOR=black][FONT=Verdana]debian-binary[/FONT][/COLOR]
[*][COLOR=black][FONT=Verdana]control.tar.gz[/FONT][/COLOR]
[*][COLOR=black][FONT=Verdana]data.tar.gz[/FONT][/COLOR]
[/LIST][COLOR=black][FONT=Verdana]Can someone send me instruction of how to build deb package[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]thank you [/FONT][/COLOR]

---

### Post by SevenMachines on 2009-12-09
In my opinion the best place to start is to look at the [Ubuntu Packaging Guide]("https://wiki.ubuntu.com/PackagingGuide/Complete"). You can also look at the [Debian New Maintainers Guide]("http://www.debian.org/doc/maint-guide/") if you need more information, which is more comprehensive. 

It can also be helpful to look at the packaging of other deb's from the repositories, either simple examples like hello, or if you can find a package that does something similar to yours, look at that too. This can be done by enabling the source repository (in synaptic if you like) and then
$apt-get source <some-package-name>

and of course, if you get stuck and need some advice theres always these forums for a hopefully helping hand :)

---

### Post by gradinaruvasile on 2009-12-09
Use checkinstall. You can use it to create .debs from source code.
Typical installation of source code:
./configure
make
sudo make install

Here u do:

./configure
make
sudo checkinstall

And if make is succesful you should have a .deb file.

---

### Post by foresto on 2009-12-11
checkinstall can produce a really quick and dirty .deb package from most configure/make/install projects that only need to place files on the filesystem.  (Emphasis on the word dirty; you won't want to distribute such a package professionally.)

If your project has to do something more complicated like modifying system files or creating users at install time, or if you want a high quality deb package that follows debian/ubuntu policies, be prepared to spend a few days with the packaging guides and debian policy manuals.

---

