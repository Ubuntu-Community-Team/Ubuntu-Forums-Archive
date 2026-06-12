---
title: "Microsoft font popup"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by alex233 on 2014-07-30
Every time I run a command line with apt-get, this screen comes up in the terminal and I can't make it go away!  I just bought this laptop and it came with Windows 8 but I installed Ubuntu on it, therefore no more Windows. How do I fix this???

---

### Post by lisati on 2014-07-30
Click on the popup to get it in focus, press the TAB key to highlight the "<OK>", press enter, and it should go away.

---

### Post by Bashing-om on 2014-07-30
alex233; Hi !

That screen is not to intuitive at all ! .. You must accept the licence agreement in order for the non-free (MicroSoft) software installation to complete.

Try as the tab key to move the focus to the "ok" and the space key to accept- or perhaps the enter key . Once accepted the install should proceed.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by alex233 on 2014-07-30
Don't I feel ridiculous...Thank you so much! Do you know why that pop up occurred?

---

### Post by grahammechanical on 2014-07-30
That screen comes up when we use the terminal and the apt-get install command to install ttf-mscorefonts-installer. I do not see that when I run apt-get on my machine..

The MS core font installer cannot be installed unless we agree to the Microsoft End User License Agreement (EULA). If you accept the terms and conditions imposed by Microsoft then you should use the tab key to highlight <ok> and then press enter.

Then the installer will install and start to download and install each of the Microsoft core TTF fonts in accordance with the Microsoft EULA. Perhaps you are installing Wine through the terminal. Wine brings in the MS TTF core fonts and that is why we get the dialog box.

Something similar happens when we use the Software Centre to install Wine. Look for a dialog box requiring out acceptance of the Microsoft EULA. It may be hidden behind the software centre application window.

Regards.

---

### Post by Vladlenin5000 on 2014-07-30
The same TT fonts are included in *ubuntu-restricted-extras*.

---

