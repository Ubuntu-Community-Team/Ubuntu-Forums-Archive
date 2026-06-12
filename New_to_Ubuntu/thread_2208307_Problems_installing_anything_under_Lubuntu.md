---
title: "Problems installing anything under Lubuntu"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by ra7411 on 2014-02-27
I'm a long time Win user who is trying to get acquainted with Linux, and I thought a good way to start would be to switch over an old laptop to Ubuntu. 
(Dell Lattitude D400 : Intel Mobile Pentium 1.4GHz processor, 32 bit, 512MB of DDR memory, a 40GB hard drive.)

I wiped out the old XP o/s, and installed Lubuntu. During this, there was some sort of issue involving "pae" about the cpu, and it had to adjust something - I don't remember the details.

Anyway, I got Lubuntu installed, it seems to be working ok, but there is a problem about getting new applications installed. I'm used to to downloading something, looking for a "setup or install".exe, and clicking and getting it done.

With this Lubuntu o/s, I have tried to install Thunderbird and Open Office with no apparent results.
1) I've tried both by downloading files over the GUI, uncompressing, then looking for an "exe" file that starts the install, with no success - there's nothing to click on that installs anything.
2) I've tried both by using command line "sudo's" on the LXTerminal with a lot of apparent activity on the terminal, a read this license thing at the end, but if anything is actaully installed I can't find it either on the menu or file manager.

What's going on and how do I get these programs installed?

Thanks

---

### Post by Rex Bouwense on 2014-02-27
Just open Lubuntu Software Center from the main menu.  There you will find various catagories.  Libre Office can be found under Office and Thunderbird can be found under Internet.  Just add the application to apps basket and when you are done click install and wait for the applications to be installed.  There are other ways but this is the easiest.

---

### Post by mörgæs on 2014-02-27
.exe files only work in Windows.

For the PAE problem there are workarounds:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Your present install is likely to be 12.04 which is unsupported.

---

### Post by ra7411 on 2014-02-27
In the Lubuntu software center, I'm seeing "sylpheed" as a mail handler, and "Abiword, Gnumeric" etc as office programs. 
These I already have installed, they installed along with the o/s.
No Thunderbird or Open Office is showing up on my screen in the Lubuntu software center.
The problem is, the Gnumeric spreadsheet seems to have a hard time loading a large SS file I use a lot.
Maybe I'll just have to settle for this. Beats me.

---

### Post by monkeybrain20122 on 2014-02-27
> **ra7411 said:**
> In the Lubuntu software center, I'm seeing "sylpheed" as a mail handler, and "Abiword, Gnumeric" etc as office programs. 
These I already have installed, they installed along with the o/s.
No Thunderbird or Open Office is showing up on my screen in the Lubuntu software center.
The problem is, the Gnumeric spreadsheet seems to have a hard time loading a large SS file I use a lot.
Maybe I'll just have to settle for this. Beats me.

There is no OpenOffice, most Linux distros now provide LibreOffice. Thunderbird is in the repo. Lubuntu comes with the synaptic package manager, it is much better than the lubuntu software centre.

---

### Post by SeijiSensei on 2014-02-27
Let's make sure you followed the correct path when you used the terminal.  You should have entered commands like this:

```

sudo apt-get update
sudo apt-get install libreoffice thunderbird

```
After you enter the first command you'll be prompted for your password, the same one you use to log into Ubuntu.

"Sudo" runs commands with the privileges of the "superuser" ("super user do"), known as the "root" user on Unix derivatives like Linux.  Adding and removing packages is one task that only the root user can do.

Both commands use a program called "apt-get" to manage your installed software.  The first command tells apt-get to check with all the "repositories" where Ubuntu software resides and update its lists of the most recent packages.  The next line installs LibreOffice and Thunderbird.

If you want to know whether a package is installed, use the command "dpkg -s package_name" like "dpkg -s thunderbird".  You will get back a lot of information if it installed, none if it is not.

When you install packages they will insert themselves into the program menu.  If Thunderbird is installed, it will appear in the "Internet" section of the menus.  LibreOffice unsurprisingly appears in the Office category.

---

### Post by ra7411 on 2014-02-27
I've used those commands, I believe correctly. I just did it again with thunderbird. Everything looked right on the terminal screen, I got a read file with <ok> at the end. Still, nothing installed, no menu item inserted.

---

### Post by monkeybrain20122 on 2014-02-27
Why don't you just use synaptic?

---

### Post by vasa1 on 2014-02-27
> **monkeybrain20122 said:**
> Why don't you just use synaptic?
But why should synaptic work when the other routes fail?

---

### Post by vasa1 on 2014-02-27
> **ra7411 said:**
> I've used those commands, I believe correctly. I just did it again with thunderbird. Everything looked right on the terminal screen, I got a read file with <ok> at the end. Still, nothing installed, no menu item inserted.If you want help here, you'll have to be more informative, for example, by providing the output you get when you say "Everything looked right on the terminal screen, I got a read file with <ok> at the end."

I've never got "a read file with <ok> at the end." in the few years I've used Ubuntu.

---

### Post by monkeybrain20122 on 2014-02-27
> **vasa1 said:**
> But why should synaptic work when the other routes fail?

No, but in synaptic you won't mistype.And usually if something is wrong the error message is prominent enough that even a newbie won't miss it.

---

### Post by SeijiSensei on 2014-02-28
Could you have installed something else recently like restricted-extras or just the Microsoft TrueType fonts?  The web fonts require that you accept the Microsoft EULA which appears on screen during the installation with an <OK> field at the bottom of the screen that you must select to move forward.  You can use the tab key to highlight that field, then hit Enter.  If you began to install this package in the past, then aborted, you'll be asked about it again every time you try to install something until you select OK.

Other packages put up similar screens during the installation process. For instance, MySQL asks repeatedly to create a password for its root user.  If you find yourself looking a page of text with <OK> at the bottom, use the tab key to highlight it, then hit enter.

---

### Post by monkeybrain20122 on 2014-02-28
> **SeijiSensei said:**
> Could you have installed something else recently like restricted-extras or just the Microsoft TrueType fonts?  The web fonts require that you accept the Microsoft EULA which appears on screen during the installation with an <OK> field at the bottom of the screen that you must select to move forward.  You can use the tab key to highlight that field, then hit Enter.  If you began to install this package in the past, then aborted, you'll be asked about it again every time you try to install something until you select OK.



If you don't accept the eula then it just wouldn't get installed. When this came up during installation of restricted-extras I always rejected and had no issue. I only install it in 13.10 because pipelight requires msfont as a dependency.

---

### Post by SeijiSensei on 2014-03-01
Won't it depend on where and how you abort the installation process?  If you hit Ctrl-C when the EULA is on the screen, then run apt-get later, won't you get prompted again?  

I was trying to point out situations where an "OK" appears during installation as the OP reports.  It's rare, but it does happen.

---

