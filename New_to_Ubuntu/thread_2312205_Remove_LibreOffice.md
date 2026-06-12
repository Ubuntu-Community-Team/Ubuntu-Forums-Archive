---
title: "Remove LibreOffice"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by incurablegeek on 2016-02-02
When I follow these instructions, I am told "LibreOffice is not installed". That of course I know given the fact that Libre is embedded and not an add-on program

> 1) Copy (sudo apt-get purge libreoffice*) in terminal and hit enter then press y and enter again.
   
 2) Edit: As @muru pointed out ncdu command is not present by default so you have to install it as follows:  sudo apt-get install ncdu
 
 
 Run the following commands on your terminal: cd /
 ncdu -x -q
 
 
 Then, Navigate to the directories where these packages are present and remove them manually. But be careful because you don't want to remove anything other than libre-office packages.



Am I doing something wrong if I follow these instructions completely but am told LibreOffice is not installed?

Before posting (and annoying you folks), I checked to see of the topic had been addressed elsewhere. It was back in 2014 at "http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOffice"

> **sudo apt-get update** This will update your software sources.
**sudo apt-get install -f **This will attempt to repair broken packages.
**sudo apt-get remove --purge libreoffice* **This will remove libreoffice and purge the install information


I followed those instructions and was also told LibreOffice was not installed, yet of course I can open it as it embedded in Kubuntu 14.04

All suggestions welcomed. ](*,)

---

### Post by Vladlenin5000 on 2016-02-02
Are you sure you're opening some Libreoffice program (if so, which one?) and not [KDE's own office suite]("https://www.kde.org/applications/office/")? They're entirely different entities.

---

### Post by howefield on 2016-02-02
> **incurablegeek said:**
> I followed those instructions and was also told LibreOffice was not installed, yet of course I can open it as it embedded in Kubuntu 14.04

As well as posting the instructions that you are following, might be helpful to post your terminal commands and the output (in between code tags).

---

### Post by incurablegeek on 2016-02-02
The "embedded office", if you will, is indeed LibreOffice. I need to use the one downloaded from the Libre site and not the embedded version.

As for > might be helpful to post your terminal commands and the output (in between code tags) That sure as heck makes sense. Will do.

The attached will definitely appear chaotic because it represents all my failed efforts to remove the embedded LibreOffice.

---

### Post by Vladlenin5000 on 2016-02-02
The command to remove all traces of any Libreoffice related package is indeed
```
sudo apt-get remove --purge libreoffice*
```
Note the asterisk which is missing in the command you issued. Without it APT will only remove the 'libreoffice' meta-package. BTW, this isn't even installed by default because Ubuntu developers always preferred to include just the basic LO components only (Writer, Calc, Presentation). The 'libreoffice' meta-package can be later used to install the full suite.

And this is completely wrong: sudo apt-get remove --purge libreoffice-common delete libre office . You don't have any 'delete', 'libre' or 'office' packages installed, obviously, so the error messages following such command are correct and expected. Syntax matters and also, although not applicable here, Linux is case-sensitive.

In a nutshell, please try the above command including the asterisk at the end. If it replies with nothing to uninstall you can be sure there's no LO in your system. Also, it isn't "embedded" no matter how you stretch that definition, it's software like any other and not required by the OS itself. As such, it can be completely uninstalled anytime without consequences. What really looks like embedded (but it really isn't) is the KDE Office Suite, included by default in Kubuntu (or any other Linux distro using KDE), that I mentioned in the first reply.

---

### Post by bab1 on 2016-02-02
> **incurablegeek said:**
> The "embedded office", if you will, is indeed LibreOffice. I need to use the one downloaded from the Libre site and not the embedded version.

As for  That sure as heck makes sense. Will do.

The attached will definitely appear chaotic because it represents all my failed efforts to remove the embedded LibreOffice.
Embedded?  I don't think so.  LibreOffice is included in the OS installation image.  It is true that Libreoffice is installed (just as you would install any package) when you first install the OS.  Unless you have some major reason to use the a LibreOffice download to install this app, I would use the [K]Ubuntu package as it is developed to take into account any variations between the Upstream libreOffice/Debian packaging.

I have attached what I get when I test the purge of Libreoffice. From what I can see, you are not using the correct commands to purge Libreoffice.  I have attached a listing of what I get when I use this command```
sudo purge libreoffice*
```
Note that I have edited the first few lines which declare the items that are NOT installed since I have globing (*) to mean every libreoffice package.

---

### Post by incurablegeek on 2016-02-02
I shall try your commands and report back. However, the commands I used did come from this site. [URL="http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOff ice"]http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOff ice
[/URL]
And [**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732"), you are indeed persistent in your attempts to assist me. For that I must thank you!

----------

> **Embedded?  I don't think so.**  LibreOffice is included **in the OS installation image**. Actually I fail to see the difference, lest it be semantics.

---

### Post by bab1 on 2016-02-02
> **Vladlenin5000 said:**
> The command to remove all traces of any Libreoffice related package is indeed
```
sudo apt-get remove --purge libreoffice*
```
Note the asterisk which is missing in the command you issued. Without it APT will only remove the 'libreoffice' meta-package. BTW, this isn't even installed by default because Ubuntu developers always preferred to include just the basic LO components only (Writer, Calc, Presentation). The 'libreoffice' meta-package can be later used to install the full suite.

And this is completely wrong: sudo apt-get remove --purge libreoffice-common delete libre office . You don't have any 'delete', 'libre' or 'office' packages installed, obviously, so the error messages following such command are correct and expected. Syntax matters and also, although not applicable here, Linux is case-sensitive.

In a nutshell, please try the above command including the asterisk at the end. If it replies with nothing to uninstall you can be sure there's no LO in your system. Also, it isn't "embedded" no matter how you stretch that definition, it's software like any other and not required by the OS itself. As such, it can be completely uninstalled anytime without consequences. What really looks like embedded (but it really isn't) is the KDE Office Suite, included by default in Kubuntu (or any other Linux distro using KDE), that I mentioned in the first reply.
+1

@ incurablegeek -- The terms "sudo apt-get purge libreoffice*" and "sudo apt-get remove --purge libreoffice* are functionally the same.  The first one has less keystrokes.  What @Vladlenin5000 and I are telling you is; use the correct command and you can remove LibreOffice easily.

---

### Post by bab1 on 2016-02-02
> **incurablegeek said:**
> I shall try your commands and report back. However, the commands I used did come from this site. [URL="http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOff ice"]http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOff ice
[/URL]
And [**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732"), you are indeed persistent in your attempts to assist me. For that I must thank you!

I just skimmed the link you listed.  It also uses the same command.  If you want to test the command add an -s switch to the command like this```
sudo apt-get **[COLOR="#FF0000"]-s[/COLOR]** purge libreoffice* 
```

---

### Post by bab1 on 2016-02-02
> **incurablegeek said:**
> I shall try your commands and report back. However, the commands I used did come from this site. [URL="http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOff ice"]http://ubuntuforums.org/showthread.php?t=2239841&highlight=Remove+LibreOff ice
[/URL]
And [**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732"), you are indeed persistent in your attempts to assist me. For that I must thank you!

----------

 Actually I fail to see the difference, lest it be semantics.
Embedded means it is part of something.  LibreOffice is definitely not part of Lubuntu.  It is only a package that is installed by default.  It is stand alone.  Your problem is more than semantics however.

---

### Post by incurablegeek on 2016-02-02
> sudo apt-get remove --purge libreoffice*

In trying to input these commands, I fail because I **cannot input the asterisk (*)**, even though I have the usual QWERTY keyboard. The asterisk comes up as '. 

Ah, I only wish I drank!

.................

Having tried everything, LibreOffice still resides in my system. Please refer to screen shot.

---

### Post by Vladlenin5000 on 2016-02-02
There's no usual QWERTY keyboard... Again, semantics... There are HUNDREDS of different (regional) keyboard layouts with QWERTY where the English standard alphabet is in the same sequence but other characters are in different positions or may or may not exist. Examples are the (in)famous Ñ that you find in Spanish keyboards only. So, on top of other issues, you also have a layout mismatch. Had you selected the correct one during the installation and we wouldn't be having this conversation... Now... I have no intention of helping you with that also - hopefully somebody else will - and TBH I only replied to this thread because when I noticed you were the same guy as before it was too late already. I'm still here because I don't like leaving unfinished jobs.

So, in order to finish this one, please copy/paste to the terminal. Note: In the terminal you need to use CTRL+SHIFT+V (instead of CTRL+V) to paste -or- simply right-click where the cursor is and "paste". Doing this you won't need to find where your asterisk really is.
Good luck with your 'new' LO directly from their website (you'll need it) and if you ever want (you will) to reinstall the LO version available in the official Ubuntu repositories just do
```
sudo apt-get install libreoffice
```
(no asterisk needed this time)

---

### Post by incurablegeek on 2016-02-02
> Had you selected the correct one during the installation

Thank you for again assuming that I am "not too bright". Quite frankly I find that interesting. I must tell my friends at Caltech and MIT. They will also be amused.

As for the keyboard I selected during the installation, I selected the US English "Qwerty" keyboard, in lieu of other languages or the Dvorak keyboard, which though ostensibly more efficient, never caught on.

As for your rare, though appreciated, suggestion *sans sarcasm*: > sudo apt-get install libreofficemy associates in India are quite adamant that I first remove the embedded/packaged LibreOffice, which some have suggested is not even in Kubuntu (again, please see screenshot), and then install LibreOffice from [https://www.libreoffice.org/](https://www.libreoffice.org/)

---

### Post by vasa1 on 2016-02-02
People are trying to help you. Also, code is preferable to screenshots. Your use of "embedded" is not that common in the context of installing software.

---

### Post by incurablegeek on 2016-02-02
> code is preferable to screenshots

I quite agree. And that is why I posted the codes, actually many codes, I tried. I posted the screenshots for those who said LibreOffice was not contained in Kubuntu.

The problem at hand now is that I **cannot enter an asterisk * in Konsole**.

I am quite willing to try all suggested code if I can actually enter it in Konsole. I cannot.

--------------

Please let me remind everyone that I posted in the "fresh-faced" newbie section - and not in a high-level section. Some empathy, if you will, for a beginner.

---

### Post by bab1 on 2016-02-02
> **incurablegeek said:**
> I quite agree. And that is why I posted the codes, actually many codes, I tried. I posted the screenshots for those who said LibreOffice was not contained in Kubuntu.

The problem at hand now is that I **cannot enter an asterisk * in Konsole**.

I am quite willing to try all suggested code if I can actually enter it in Konsole. I cannot.
Nor will you ever be able to enter one command to remove LibreOffice completely unless you do have a working **[COLOR="#FF0000"][SIZE=3]*[/SIZE][/COLOR]** key.  The reason for that is that LibreOffice is multiple packages.  The glob **[SIZE=3][COLOR="#FF0000"]*[/COLOR][/SIZE]** allows the BASH script to expand that notation to include any package that starts with libreoffice.

Get another keyboard.  If you can't do that then look at the list I gave you and purge each sub package by itself.  You will need more than a couple of hours to completely purge LibreOffice.

---

### Post by incurablegeek on 2016-02-02
> Get another keyboard.

Surely you jest. It is an expensive mechanical keyboard that I need for efficiency in my work. 

I do not use sponge membrane keyboards, not can I assume that another keyboard would make any difference.

[SIZE=3]Not to worry. I will ask my partners in India. Thanks to all.[/SIZE]

---

### Post by bab1 on 2016-02-02
> **incurablegeek said:**
> Surely you jest. It is an expensive mechanical keyboard that I need for efficiency in my work. 

That does not work!

---

### Post by incurablegeek on 2016-02-02
Well, it actually does work in DOS, Windows command line and even in Cisco OS. 

And, yes, I do know Cisco - far better than I know Kubuntu.

But, have no fear, that will change. I am very quick to ascend learning curves. ):P

---

### Post by Geoffrey_Arndt on 2016-02-02
Incurable . . . as info, there are at least 2 versions of Indian English (Hindu) keyboards that replace the * with the ' symbol.    When you talk to Kumar or Srinivas in India, perhaps you could check if either modified your keyboard while you visited???  :oops:

Also, you can use the package manager "_Synaptic_" to "completely remove" any package in Kubuntu, including the PRE-INSTALLED version of LibreOffice (modified for non-GTK distros).

By the Way . . . . do you mean "Cisco IOS" (versus OS?) . . .

---

### Post by vasa1 on 2016-02-02
What is the output of 
**dpkg -l | grep libreoffice**?
**whereis libreoffice**?
**apt-cache policy libreoffice**?

I also looked at a text file you attached in post #4:```
india@india-desktop:/$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 217 not upgraded.

``` **Why 217 not upgraded**? I'd be wary of doing anything with such a system.

---

### Post by bab1 on 2016-02-02
> **Geoffrey_Arndt said:**
> Also, you can use the package manager "_Synaptic_" to "completely remove" any package in Kubuntu, including the PRE-INSTALLED version of LibreOffice (modified for non-GTK distros).

There can be some confusion with using Synaptic.  By default the "meta package" *libreoffice* is not used to install all the LibreOffice parts.  This is why the OP keeps getting the message "LibreOffice" is not installed when using the CLI command "sudo apt-get remove --purge libreoffice".  It's always the little things that get ya.  One would still have to find and select all the parts to remove all of LibreOffice.

You can check this from the CLI with this dpkg command```
dpkg -l libreoffice
```
This should show the metapackage not installed even though LibreOffice is working.

Once again for those that have a working * key the output of this will show the individual packages just a @vasa1 ask for
```
dpkg -l libreoffice*
```

---

### Post by incurablegeek on 2016-02-02
> Kumar or Srinivas in India

Now I am curious. Who are those people and how do you know I have ever been to India?

> By the Way . . . . do you mean "Cisco IOS" (versus OS?)

Oh my goodness, here we go again. ;)

---

### Post by vasa1 on 2016-02-02
> **bab1 said:**
> ... One would still have to find and select all the parts to remove all of LibreOffice.
When I run **apt-cache show libreoffice**, I see this:```
Package: libreoffice
Priority: optional
Section: universe/editors
Installed-Size: 161
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Architecture: amd64
Version: 1:4.2.3~rc3-0ubuntu2
Depends: fonts-sil-gentium-basic, libreoffice-base, libreoffice-calc, libreoffice-core (= 1:4.2.3~rc3-0ubuntu2), libreoffice-draw, libreoffice-impress, libreoffice-math, libreoffice-report-builder-bin, libreoffice-writer, libreoffice-avmedia-backend-gstreamer, fonts-dejavu, libreoffice-java-common (>= 1:4.2.3~rc3~), python3-uno (>= 4.0~)
Recommends: fonts-liberation | ttf-mscorefonts-installer, libpaper-utils, libreoffice-gnome | libreoffice-kde
Suggests: cups-bsd, hunspell-dictionary, hyphen-hyphenation-patterns, iceweasel | firefox | icedove | thunderbird | iceape-browser | mozilla-browser, imagemagick | graphicsmagick-imagemagick-compat, libgl1, libreoffice-grammarcheck, libreoffice-help-4.1, libreoffice-l10n-4.1, libsane, libxrender1, myspell-dictionary, mythes-thesaurus, openclipart-libreoffice, pstoedit, unixodbc, gstreamer1.0-plugins-base, gstreamer1.0-plugins-good, gstreamer1.0-plugins-ugly, gstreamer1.0-plugins-bad, gstreamer1.0-ffmpeg, default-jre | gcj-jre | openjdk-7-jre | openjdk-6-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre, libreoffice-officebean
Filename: pool/universe/libr/libreoffice/libreoffice_4.2.3~rc3-0ubuntu2_amd64.deb
Size: 26774
MD5sum: f7e84577ec95c192133e46c9b33b69b5
SHA1: c8354820a9674b6bae1ac2e4c03c921285d43d37
SHA256: ed367ed42fa51aba0a2b7ed3fbbf5f02f2408698777e6a45d6738707b993fb01
**Description: office productivity suite (metapackage)**
Description-md5: 69d7556a53642b01f6e6383cd4447bc4
Homepage: http://www.libreoffice.org
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```
As Vlad pointed out, "libreoffice" is a metapackage and simply running **sudo apt-get purge libreoffice** wouldn't do much!

OP may try a _simulation_ for starters: **apt-get purge -s libreoffice-base libreoffice-calc libreoffice-core libreoffice-draw libreoffice-impress libreoffice-math libreoffice-report-builder-bin libreoffice-writer** and post the output here within code tags.

---

### Post by vasa1 on 2016-02-02
> **incurablegeek said:**
> Now I am curious. Who are those people and how do you know I have ever been to India?
...
Oh my goodness, here we go again. ;)

Why don't you please focus on the issue at hand?

---

### Post by incurablegeek on 2016-02-02
> Why don't you please focus on the issue at hand?

Nope! Will the poster please answer the question.

You purport to have intimate knowledge of me and I would like to know how!

---

### Post by vasa1 on 2016-02-02
> **incurablegeek said:**
> .., not can I assume that another keyboard would make any difference.
...
Why is that?

I'm going to leave this thread alone. All the best.

---

### Post by Irihapeti on 2016-02-02
Closed for staff review.

---

