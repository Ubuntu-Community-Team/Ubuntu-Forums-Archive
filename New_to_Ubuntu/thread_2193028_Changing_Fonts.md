---
title: "Changing Fonts"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by nwpll on 2013-12-10
Hi

I have been using Libre Office Version: 4.1.2.3 for while and using fonts that i don't like. There is no Times new roman or Arial etc like on this forum. How do i change the fonts to the selection that is on this forum. 

Thanks for reading this post.

Peterfc

---

### Post by Frogs Hair on 2013-12-10
Hello and Welcome

The MS Core fonts are available in the software center. That will install _some_ of the proprietary Microsoft fonts you are looking for, but Arial is not included.

---

### Post by sandyd on 2013-12-11
> **nwpll said:**
> Hi

I have been using Libre Office Version: 4.1.2.3 for while and using fonts that i don't like. There is no Times new roman or Arial etc like on this forum. How do i change the fonts to the selection that is on this forum. 

Thanks for reading this post.

Peterfc
If you want, you can use your existing windows fonts in Ubuntu.
Go to your windows drive -> C:\Windows\Fonts , and copy the folder.
Then, go back to Ubuntu, and open your home folder. In one of the drop down menus, (it is different for each Ubuntu release, so you may have to look around), select the option for 'show hidden files'
Create a new folder (if it doesnt exist), and name it .fonts (make sure there is a period in front)
Open the .fonts folder, create a folder inside named 'windowsfonts' and place the contents of the Font folder from Windows into 'windowsfonts'
Open a terminal, and run the below
```

sudo fc-cache -f -v

```
If you open libreoffice now, it should show the fonts you imported from windows in the font selector.

---

### Post by coffeecat on 2013-12-11
@nwpll, if you want to install the MS core fonts from the Software Centre, I'd recommend installing the ubuntu-restricted-extras package. As well as the MS core fonts, that will give you various media codecs, flash and so on. It's on my list of routine stuff to install after I do a fresh installation of each release of Ubuntu. There will be a EULA to agree to otherwise the actual fonts won't be installed, so check on what Software Centre is doing before you close it.

> **Frogs Hair said:**
> but Arial is not included.

I think Arial is included. Was it perhaps Tahoma that you were thinking of? There is one MS font that is not included, but Arial is on my system and I haven't installed any fonts apart from the MS core fonts package.

---

### Post by col48 on 2013-12-11
If a font can be found in any Ubuntu repository then the simplest thing to do is to install it from there just as you would with software.
As the previous poster has said, fonts are transferable from Windows (this may be universally true but I am not certain of this) but this only applies if you have a Windows system to hand!  You should be careful you are not breaching your license by making a copy from this source, but a prosecution is unlikely!

Otherwise....
Many fonts are available on the web for free.  For instance on [http://www.azfonts.net]("http://www.azfonts.net") or [http://www.yolinux.com/TUTORIALS/LinuxListOfFonts.html]("http://www.yolinux.com/TUTORIALS/LinuxListOfFonts.html") - there are many other websites.  The latter gives a tutorial but the *really* 'absolute beginner' may not find it easy to interpret into their system.

[B]What follows is true of my Precise (12.04) system, but the principles will be universal (I hope!).
[/B]
The basics of what is needed are (1) to download the font and (2) to get the computer to recognise it.

(1) Download the font
Fonts available to all users are stored in /usr/share/fonts and can be anywhere in a hierarchy of subfolders.  Mine appear to be organised (mostly by Ubuntu in that I have not downloaded many myself) by type of font and in some cases usage (eg there is a subfolder /truetype/openoffice).  All these folders will be owned by root, so changes to them have to be done using sudo. On a multi-user system, those for a single user will be in a similar fonts folder under that user's home folder.

So download the font to your usual safe downloads folder, extract it or unzip it or whatever if necessary to get the font file (a truetype font will be a .ttf file, for instance). I suggest you create a subfolder in some appropriate place in the fonts folder hierarchy which will tell you this is one you did yourself for future reference.  Now copy the font to the desired folder in the fonts hierarchy.

(2) Computer recognition
Getting the computer to recognise the font will make it available to any software which doesn't operate in its own private world.  So openoffice and libreoffice applications do not need any further action to make immediate use of them.  The action for this is a Terminal command, to be run as root:

```
sudo fc-cache  -f  -v
```

Somewhere I've read that having several tens of thousands of fonts can slow down some operations - I presume because consulting a large index of fonts takes longer than consulting a small one - but unless you download a large library of fonts in order to get the two or three specialist ones you want this is not likely to be a problem.

---

