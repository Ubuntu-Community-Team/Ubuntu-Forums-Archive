---
title: "[NEED HELP] install *.deb file post-install with script"
date: 2015-04-30
forum: Packaging and Compiling Programs
---

### Post by wally00 on 2015-04-30
I hope this is in the appropiate forum.

So the story is that i want to build a custom installation cd/usb, for using to install on more than one pc, and my question is if is there any method to install some *.debs from a folder within the install media, and not the internet since the install will be made offline on all the PCs? 

I want to fully automate the installation, i already automated the ubuntu install with kickstart and preseed, but i am not able to find a simple method to install packages, without creating a new repository on the media.

I read something  about making an executable script containing all the commands but i don`t know if the "dpkg -i package.deb" command is enough, and how exactly to specify the path to the package on the media, and what extension should the script have.

Any help is appreciated. TY

PS: and is there a way to download the apt-get packages without installing them, for use from the cd/usb?

---

### Post by Stefan_Vukanovic on 2015-05-01
For the first question, I think you should first assume that the user's current directory is your installation media, CD/USB. So, you just have to make something like this:
#!/bin/bash
dpkg -i <filename>
Now, as for downloading, try sudo apt-get download <package name>.
Good luck!

---

