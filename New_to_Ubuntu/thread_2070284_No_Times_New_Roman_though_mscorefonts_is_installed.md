---
title: "No Times New Roman though mscorefonts is installed"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by bonedriven on 2012-10-12
I couldn't find MS fonts in Libre office, yet when I tried to install ttfs-mscorefonts in software center I saw it's already been installed.

Now what do I do? Thank you very much!

Unbuntu 12.04
Libre Office 3.5.3.2

---

### Post by newb85 on 2012-10-12
ttf-mscorefonts isn't the fonts themselves.  It's a package that, when configured, will download & install the  fonts.  This should have happened when you installed ttf-mscorefonts, but only if you accepted Microsoft's EULA for the fonts.  You could force it to happen now with a command like

```
sudo dpkg --configure ttf-mscorefonts
```

Note: please check the syntax of that command first.

---

### Post by Frogs Hair on 2012-10-12
The fonts installer package will appear to be installed but if EULA is not checked no fonts will be installed . This would affect all fonts included with the package though.

---

### Post by bonedriven on 2012-10-13
Thank you. I'll check your command when I get to office on Monday.

---

### Post by bonedriven on 2012-10-15
> **newb85 said:**
> ttf-mscorefonts isn't the fonts themselves.  It's a package that, when configured, will download & install the  fonts.  This should have happened when you installed ttf-mscorefonts, but only if you accepted Microsoft's EULA for the fonts.  You could force it to happen now with a command like

```
sudo dpkg --configure ttf-mscorefonts
```

Note: please check the syntax of that command first.

I get this error running the command:

dpkg: error processing ttf-mscorefonts-installer (--configure):
 package ttf-mscorefonts-installer is already installed and configured
Errors were encountered while processing:
 ttf-mscorefonts-installer


I also tried re-installing that ttf-mscorefonts-installer. During the installation, there was an EULA popping up, I checked the box and finished the installation. Nevertheless, I still don't have MS fonts in Libre office!

---

### Post by furtom on 2012-10-15
> **bonedriven said:**
> I get this error running the command:

dpkg: error processing ttf-mscorefonts-installer (--configure):
 package ttf-mscorefonts-installer is already installed and configured
Errors were encountered while processing:
 ttf-mscorefonts-installer


I also tried re-installing that ttf-mscorefonts-installer. During the installation, there was an EULA popping up, I checked the box and finished the installation. Nevertheless, I still don't have MS fonts in Libre office!

Try

```
sudo dpkg-reconfigure ttf-mscorefonts

```
And a reboot for good measure. That might do it. :)

---

### Post by Frogs Hair on 2012-10-15
I used the installer last week on 12.10 and had to reinstall because a theme error didn't allow me to see the EULA dialog properly . I was also using the fonts with all releases going back to 10.10 . The fonts are hosted on Sourceforge. Have you logged out and back in since adding the package ?

---

### Post by Zimmer on 2012-10-15
Try entering in a Terminal..

 sudo fc-cache -f -v

This will rebuild the fonts cache..

---

### Post by bonedriven on 2012-10-16
> **furtom said:**
> Try

```
sudo dpkg-reconfigure ttf-mscorefonts

```
And a reboot for good measure. That might do it. :)

Did this and it brought up a screen and all I can click is ok. So I oked 3 screens then nothing seemed to happen. So I log out/restart several times and still nothing changed.

sudo fc-cache -f -v

It says it's successfully done but nothing changed.

edit: my proxy had a problem. Will get to this later.

---

### Post by bonedriven on 2012-10-16
Just nothing happends with those command.

Here's cleaning cache command result:

/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 9 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/cmap/adobe-gb1: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/adobe-japan2: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap/gs-cjk-resource: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 1 fonts, 20 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/truetype/droid: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 13 fonts, 0 dirs
/usr/share/fonts/truetype/horai-umefont: caching, new cache contents: 18 fonts, 0 dirs
/usr/share/fonts/truetype/kacst: caching, new cache contents: 15 fonts, 0 dirs
/usr/share/fonts/truetype/kacst-one: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/liberation: caching, new cache contents: 16 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype/nanum: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/takao-gothic: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/tlwg: caching, new cache contents: 54 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 17 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-khmeros-core: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-punjabi-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ubuntu-font-family: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts-core: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 5 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 2 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/type1/mathml: caching, new cache contents: 1 fonts, 0 dirs
/usr/X11R6/lib/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/jacques/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/jacques/.fontconfig: cleaning cache directory

I don't even know if I have downloaded the ttf or not.

---

### Post by bonedriven on 2012-10-16
sudo dpkg-reconfigure ttf-mscorefonts-installer

The result of this is a configuring screen, I oked all 3 of them. Then my last "enter" gives me nothing. I'm back to terminal and nothing happens.

---

### Post by thatguruguy on 2012-10-16
Try the following in a terminal, and post the results here.
```
ls /usr/share/fonts/truetype/msttcorefonts
```

---

### Post by bonedriven on 2012-10-16
> **thatguruguy said:**
> Try the following in a terminal, and post the results here.
```
ls /usr/share/fonts/truetype/msttcorefonts
```

Hi, it's blank. Nothing happens. Is my terminal broken?

---

### Post by Frogs Hair on 2012-10-16
You should get an output from the command if the fonts are installed. To check manually use ```
gksudo nautilus
```
File System > usr > share > fonts > truetype.

---

### Post by bonedriven on 2012-10-16
> **Frogs Hair said:**
> You should get an output from the command if the fonts are installed. To check manually use ```
gksudo nautilus
```
File System > usr > share > fonts > truetype.

Looks like msttcorefonts fold is empty. Now back to the begining, how do I install it?

From software centre it shows "installer for microsoft true type fonts" is installed already.

---

### Post by Frogs Hair on 2012-10-16
when I did my re-installation last week I removed the installer and made sure to accept the EULA when adding it again. My problem was related to a theme error and I could not read or check the EULA dialog box. What desktop environment are you using ?

---

### Post by Peter Maunder on 2012-10-16
The mscorefonts are installed on my 12.04 systems in 
/usr/share/fonts/truetype/msttcorefonts/  and that is where you will find the Times Roman. There should be 60+ fonts there but I see you have 0 installed

(/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 0 fonts, 0 dirs).

I found an earlier thread on the subject which gives a good reference. Libreoffice will pick up the fonts in the /usr/share/fonts when you restart Libreoffice.

 				 				**Re: Configuring ttf-mscorefonts-installer problem** 			
 			 			 		   		 		 		To fix the "ttf-mscorefonts-installer" issue, please see this guide:

[http://www.tuxgarage.com/2011/11/ttf...er-ubuntu.html]("http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html")

Thereafter, to fix the issue with the missing GPG key, just run:
 	Code:
 	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783 


I

---

### Post by bonedriven on 2012-10-16
> **Peter Maunder said:**
> The mscorefonts are installed on my 12.04 systems in 
/usr/share/fonts/truetype/msttcorefonts/  and that is where you will find the Times Roman. There should be 60+ fonts there but I see you have 0 installed

(/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 0 fonts, 0 dirs).

I found an earlier thread on the subject which gives a good reference. Libreoffice will pick up the fonts in the /usr/share/fonts when you restart Libreoffice.

 				 				**Re: Configuring ttf-mscorefonts-installer problem** 			
 			 			 		   		 		 		To fix the "ttf-mscorefonts-installer" issue, please see this guide:

[http://www.tuxgarage.com/2011/11/ttf...er-ubuntu.html]("http://www.tuxgarage.com/2011/11/ttf-mscorefonts-installer-ubuntu.html")

Thereafter, to fix the issue with the missing GPG key, just run:
 	Code:
 	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783 


I

I can't get the EULA screen in your link. I can only press ok. Then it ask me to input the msfonts folder if I have downloaded, and said if not I can leave it blank. So I leave it blank and press ok again, then it asked me if I want to choose a mirror site to download, and it said it's also ok if I don't input a mirror site to download and leave it blank and ok. I oked again. Then it's a black screen like I did nothing. Then nothing happens to libre office.

---

### Post by bonedriven on 2012-10-17
"Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection."

I use a proxy to connect to internet. But I have set the proxy for my internet, as well as apt get connection. Now I simply don't understand if this thing is different and need to set a proxy for it specially.

---

### Post by bonedriven on 2012-10-17
Followed this link:[http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package](http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package)

and manually download every exe files. Then I got this reply:

checking home/jacques/andale32.exe
checking /Home/jacques/andale32.exe
checking /home/jacques/andale32.exe
checking /home/jacques/arial32.exe
checking /home/jacques/arialb32.exe
checking /home/jacques/comic32.exe
checking /home/jacques/courie32.exe
checking /home/jacques/georgi32.exe
checking /home/jacques/impact32.exe
checking /home/jacques/times32.exe
checking /home/jacques/trebuc32.exe
checking /home/jacques/verdan32.exe
checking /home/jacques/webdin32.exe

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.


Why installing some fonts is soooooooooo hard???
The whole thing is plain stupid.

---

### Post by JKyleOKC on 2012-10-17
You might try this link: [https://launchpad.net/ubuntu/precise/+package/ttf-mscorefonts-installer](https://launchpad.net/ubuntu/precise/+package/ttf-mscorefonts-installer) and note that in the list of released versions, the topmost one is for 12.10 64-bit, the next is for 12.04 64-bit, and so on. You should be able to download the appropriate package and then install it from the command line using "sudo dpkg -i " followed by the filename, after downloading the package itself from the launchpad link...

As for the whole thing being plain stupid, that's typical Microsoft behavior for you: make them available only in *.exe format so that nothing but Windows can make use of them!

---

