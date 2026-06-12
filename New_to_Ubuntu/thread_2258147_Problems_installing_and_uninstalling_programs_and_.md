---
title: "Problems installing and uninstalling programs and finding directories"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by MAFinOKC on 2014-12-25
Brand new to Ubuntu. Running Lubuntu 14.10 on a Toshiba laptop. Looking for a PDF program better than "Document Viewer." I installed Adobe Reader from the Adobe FTP site. It put an icon in my start menu, but clicking on the icon does nothing. I decided to uninstall it, but it's not on the list of installed programs. I then tried to install Okular from the Software Center. According to the Software Center, it installed, but it isn't in my start menu, it doesn't open PDF files, and trying to open it by using an executable in a program directory does nothing. I don't know what I am doing wrong.

Finally, I tried to install onedrive-d, which involves using the Terminal. I got as far as getting the setup files onto my computer, and being able to go to the onedrive-d folder with the cd command, but entering the install command "./inst install" as instructed causes an error message that there is "no suchfile or directory."

I would very much appreciate some assistance in figuring out what the problem is/are.

---

### Post by flaymond on 2014-12-25
Some of the goods PDF reader -

1. Okular
2. gv
3. kpdf
4. xpdf
5. acroread
6. evince

here are some links to configure the one-drive -

[http://www.omgubuntu.co.uk/2014/06/one-drive-ubuntu-integration?utm_source=feedly&utm_reader=feedly&utm_medium=rss&utm_campaign=one-drive-ubuntu-integration](http://www.omgubuntu.co.uk/2014/06/one-drive-ubuntu-integration?utm_source=feedly&utm_reader=feedly&utm_medium=rss&utm_campaign=one-drive-ubuntu-integration)

and make you sure you install Java

---

### Post by grahammechanical on 2014-12-25
I have just visited this site

[http://get.adobe.com/uk/reader/otherversions/](http://get.adobe.com/uk/reader/otherversions/)

and it does not list a version of Adobe Reader for Linux, let alone one packaged for Ubuntu. What version did you download? Was it a Windows version and are you installing it under Wine? And you will need to provide a link to those onedrive-d instructions. How can we know if the instructions are correct or that you are following them correctly without seeing the instructions for ourselves?

Ubuntu does not have a start menu. What operating system are you using if it is not Ubuntu? What flavour of Ubuntu.

Edit: The Ubuntu Software Centre lists 3 Okular packages.

1) okular Document Viewer = provides a backend for Okular to view OpenDocument Presentation (ODP) documents.
2) Okular (okular-extra-backends) Document Viewer = These plugins allow Okular to view additional document formats.
3) Okular (okular) Document Viewer = Okular is a universal document viewer with support for advanced document features, such as annotations, forms, and embedded files.

Is number 3 installed?

Regards.

---

### Post by vasa1 on 2014-12-25
> **grahammechanical said:**
> ... What operating system are you using if it is not Ubuntu? What flavour of Ubuntu.

Regards.
From the first post: "Running Lubuntu 14.10 on a Toshiba laptop"

---

### Post by vasa1 on 2014-12-25
OP, as far as possible please ask for help on one issue per question. It will help others as well.

[s]Re. KDE apps, from my little experience with them, they may have a line in the corresponding .desktop file with something like "OnlyShowIn: KDE" meaning you won't see them listed in the menus of other desktop environments.[/s]

Looks like I misremembered :(
```
07:00 PM /usr/share/app-install/desktop $ grep -l OnlyShowIn *.desktop
```didn't list okular or for that matter as many KDE apps as I anticipated.

---

### Post by Holger_Gehrke on 2014-12-25
> **MAFinOKC said:**
> Brand new to Ubuntu. Running Lubuntu 14.10 on a  Toshiba laptop. Looking for a PDF program better than "Document  Viewer." I installed Adobe Reader from the Adobe FTP site. It put an  icon in my start menu, but clicking on the icon does nothing. I decided  to uninstall it, but it's not on the list of installed programs.
Of  course it's not in the list of installed programs. Only programs you  install using the package manager get put into that list. Using a  installer like adobe (used to) offer is the same as copying the program  file somewhere and putting a link into the menu yourself in windows.  There should a file named "README" in the Archive which explains how to  install and uninstall the program. The newest version of Acrobat Reader  on the ftp I could find was 5.10 from 2004, and that had to be installed  from the command line; it looked it's age but worked. Version 9 is  available through the Software Center but you might have to change the  sources from which Software Center is allowed to get programs to include  software with restrictive licenses (multiverse)

> 
 I  then tried to install Okular from the Software Center. According to the  Software Center, it installed, but it isn't in my start menu, it doesn't  open PDF files, and trying to open it by using an executable in a  program directory does nothing. I don't know what I am doing wrong.

Try calling it from the shell. The command is 

```

okular

```

okular might not be the best choice, unless you chose a lightweight variant of Ubuntu just for fun. It pulls in a lot of KDE that it needs to work (~40 MB Download, 130 MB unpacked). 

IMHO evince (which is probably exactly what you already have - the "Dokument Viewer") is really great. It only fails on PDF files that absolutely positively need all the newest features (and those will fail in acrobat reader too, since the version in the repositories is older than the current Windows Version) and it has a clean and easy to use GUI.

> 
Finally, I tried to install onedrive-d, which involves using the  Terminal. I got as far as getting the setup files onto my computer, and  being able to go to the onedrive-d folder with the cd command, but  entering the install command "./inst install" as instructed causes an  error message that there is "no such file or directory."

I would very much appreciate some assistance in figuring out what the problem is/are.

Shouldn't that be './**setup**.sh install" ? At least that's what it says at [https://github.com/xybu/onedrive-d](https://github.com/xybu/onedrive-d) ...

You might just look at the stuff in the onedrive-d folder in your file manager to check.

---

