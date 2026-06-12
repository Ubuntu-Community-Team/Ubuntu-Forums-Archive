---
title: "Where to install .bin files"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by xSilverhandx on 2011-09-14
So Im new to Ubuntu and all. Im getting used to terminal and using sudo or sudo -i when needed. So I was trying to install some .bin files like adobe reader and java for example. Since the file system has permissions only to the root user, where do I put the files that I need to install?

Do I become root user and put them in /usr/bin?

Help would be appreciated.

I should also ask as well is there a more proper way to install .bin files and put them somewhere to be installed properly then just placing them on the desktop?

---

### Post by cgroza on 2011-09-14
Hello. Since you already learn the terminal, this should be easy for you.
You need to know that .bin files are similar to .exe installers.
Put the .bin file in your home folder.
and then make it executable:
```
chmod +x file.bin
```
and now run it:
```
./file.bin
```This should start the installer, and guide you through the process.
You may need to elevate your privileges with sudo.

---

### Post by westie457 on 2011-09-14
> **xSilverhandx said:**
> So Im new to Ubuntu and all. Im getting used to terminal and using sudo or sudo -i when needed. So I was trying to install some .bin files like adobe reader and java for example. Since the file system has permissions only to the root user, where do I put the files that I need to install?

Do I become root user and put them in /usr/bin?

Help would be appreciated.

I should also ask as well is there a more proper way to install .bin files and put them somewhere to be installed properly then just placing them on the desktop?

Usually there is no need to install .bin files. The programs you have mentioned Adobe reader - the Ubuntu equivalent is Document Viewer, this opens PDF files and is already installed and Jave is available through Software Centre.


Beaten again by a more elegant solution - read simple. Damn my slow typing speed.

---

### Post by Frogs Hair on 2011-09-14
Adobe Reader is in the Ubuntu software center and is best installed from there. There are many java programs and installation methods may vary. See if the one you need is in the software center , if not use Google and the forum search .  there is a lot information regarding installation of java programs in Ubuntu 

To move a file in or out of the file system anywhere other than home use this command in the terminal followed by a password ```
gksu nautilus
```

---

### Post by xSilverhandx on 2011-09-14
Ok I have looked through the Ubuntu Software Center and did not find Java specifically so I can always search the forums.

Ok so really a kind of direct answer to my question but again,

If I really had to install a .bin file by hand which as I see now is small, where should I place it? Just my home folder? Where is my home folder exactly ^.^ sorry little folder noobish. 

Im making Ubuntu computers at school for kids who cant afford computers and Im used to windows folder setup and not Ubuntu's. 

Should I place the .bin files in my home folder if I want the program to be used for all users?

---

### Post by Chiel92 on 2011-09-15
> **xSilverhandx said:**
> 
If I really had to install a .bin file by hand which as I see now is small, where should I place it? Just my home folder? Where is my home folder exactly ^.^ sorry little folder noobish. 

Should I place the .bin files in my home folder if I want the program to be used for all users?

Your home folder is /home/[yourUsername]. You can put your bin file right there. That does not affect the way it is installed, e.g. wether it is available to all users or not.

But I would also suggest installing java via apt-get or via the software center. It is more common and easier. Look at this how-to:
[URL="http://www.javalobby.org/java/forums/t72809.html"]http://www.javalobby.org/java/forums/t72809.html
[/URL]

---

### Post by 3rdalbum on 2011-09-15
If something is distributed as a ".bin" file (or a ".run" file) then that file is probably an installer. You run the installer as root and it puts the real program into the correct location in the filesystem.

If I were you I'd probably forget Acrobat Reader (or Adobe Reader as it's known now). The default Ubuntu PDF viewer is actually more reliable, and you can actually print properly from it unlike the real Adobe Reader program.

---

