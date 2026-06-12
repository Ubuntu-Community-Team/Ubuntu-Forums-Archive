---
title: "How to shows picture files thumbnails ?"
date: 2019-11-05
forum: New to Ubuntu
---

### Post by mandani48 on 2019-11-05
Hello All,

Newbie in Linux, I've just installed Ubuntu 18.04.3 LTS on two PC.
Every thing seams to run correctly, thanks.

But there's something that I didn't succeed to set, it's the thumbnails view of pictures.
As a matter of fact, beside the picture files, wether in the stock files manager or Dolphin, there's just a dark grey square with "JPG" or "PNG" in it.[ATTACH=CONFIG]284333[/ATTACH][ATTACH=CONFIG]284332[/ATTACH]
Thus, one has to open it to see the content.

Please can any one tell-me how to set my Ubuntu installation so it shows thumbnails ?


Thanks a lot before hand !
Regards,
        mandani48

---

### Post by deadflowr on 2019-11-05
I forget where it sets in dolphin, but in Ubuntu's file manager just click on that four dot square like button in the top bar next to the magnify glass icon.

---

### Post by Dennis N on 2019-11-05
Using Teamviewer? Nautilus (a.k.a. Files) default is to display thumbnails on local filesystems only. Change Nautilus setting for this using dconf-editor.

---

### Post by SeijiSensei on 2019-11-05
If the pictures are stored elsewhere on the network, and you're using Dolphin, you may need to increase the size limit in Control > Configure Dolphin > General > Previews.  And make sure the appropriate file types are checked on that screen as well.

---

### Post by mandani48 on 2019-11-06
deadflowr,

> ... in Ubuntu's file manager just click on that four dot square like button in the top bar next to the magnify glass icon. <
That's fine !
Now it's OK, thumbnails shows in Ubuntu stock files manager.
Thank you very much, it's very kind of you deadflowr !

---

### Post by mandani48 on 2019-11-06
Dennis,

> Using Teamviewer? <
Well, I just used TeamViewer to access the PC I've installed Linux on it, to make the screen-shots.

> Nautilus (a.k.a. Files) default is to display thumbnails on local filesystems only. <
The pictures files are stored locally on this PC.
When one is in the front of the PC, he see exactly the same dark grey squares with "JPG" or "PNG" in it.
Thanks any way.

---

### Post by mandani48 on 2019-11-06
[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")SeijiSensei,

> If the pictures are stored elsewhere on the network, and you're using Dolphin, you may need to increase the size limit in Control > Configure Dolphin > General > Previews. And make sure the appropriate file types are checked on that screen as well. <
Thanks, but the trouble is that this previews is empty.
There's no files type to check or un check.
The only control is the file size limit.
By default it was 0Mb.
No matter how much I increase it, there's no files type to check and the thumbnails doesn't shows neither.

Any idea what to do so there's files type to check in Dolphin ?

---

### Post by SeijiSensei on 2019-11-06
On my system, the Previews dialog looks like this: [https://politicsbythenumbers.org/images/previews-dialog-dolphin.png](https://politicsbythenumbers.org/images/previews-dialog-dolphin.png)

Pretty sure it's looked like this for quite some time now, including 18.04.

You also have to click on the Preview item at the top of Dolphin's main screen to see any of them.

---

### Post by mandani48 on 2019-11-06
SeijiSensei,

Thanks for these clarifications.

> On my system, the Previews dialog looks like this: [https://politicsbythenumbers.org/ima...og-dolphin.png]("https://politicsbythenumbers.org/images/previews-dialog-dolphin.png") <
Well that's how it appearse on mine:
[ATTACH=CONFIG]284340[/ATTACH]

> Pretty sure it's looked like this for quite some time now, including 18.04. <
The fact is that it appears that way on the two PC I've installed.
As I didn't know much about Linux, I let all the standard options.

> You also have to click on the Preview item at the top of Dolphin's main screen to see any of them. <
You mean this box checked (sorry, it's in french):
[ATTACH=CONFIG]284341[/ATTACH]
By the way, I don't knows if these settings are of any utility about that:
[ATTACH=CONFIG]284342[/ATTACH][ATTACH=CONFIG]284343[/ATTACH][ATTACH=CONFIG]284344[/ATTACH]


Thanks again for your help.

---

### Post by SeijiSensei on 2019-11-06
It sounds like you didn't install Kubuntu, the version of Ubuntu that uses KDE, but maybe added Dolphin to an existing Ubuntu installation?  If so, it's likely that Dolphin is missing a lot of items that would be there in a full KDE installation.

If you want a KDE desktop, you should install Kubuntu: [http://cdimage.ubuntu.com/kubuntu/bionic/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/bionic/daily-live/current/)

If you boot this image and select Try Ubuntu, you can see what it will look like without making any alterations to your system.

The Preview button appears in the top row of Dolphin: [https://www.politicsbythenumbers.org/images/dolphin-top-menu.png](https://www.politicsbythenumbers.org/images/dolphin-top-menu.png)

---

### Post by Dennis N on 2019-11-06
> Please can any one tell-me how to set my Ubuntu installation so it shows thumbnails ?
_Tip:_
To best view thumbnails in directories with a lot of images, I suggest you try a program made for that: **gthumb** for gtk-based Ubuntu, and **gwenview** for qt-based Lubuntu or Kubuntu.

---

### Post by mandani48 on 2019-11-11
Hello SeijiSensei,

Thank you very much for your answer.
Sorry to replay that late, I was away for a few days.

> It sounds like you didn't install Kubuntu, the version of Ubuntu that uses KDE, but maybe added Dolphin to an existing Ubuntu installation? <
Yes, that's exactly what's happen.
I downloaded and installed Ubuntu 18.04.3 LTS.
Then, has I didn't find my mark with the stock files manager*, I've been looking for an other files manager.
Dolfin was in the list of optional software to install.
So I installed it, without knowing some other elements (KDE) should precede it.
I was happy to see the left side panel showing directories and sub-directories in Dolfin.

* I missed left panel showing directories and sub-directories, for one thing side; and the thumbnails didn't shows, for the second.
  As deadflowr helped, now the thumbnails shows in stock files manager, so it's ok for the second point.
  It remains the first.

> If so, it's likely that Dolphin is missing a lot of items that would be there in a full KDE installation.
> If you want a KDE desktop, you should install Kubuntu: [http://cdimage.ubuntu.com/kubuntu/bi...-live/current/](http://cdimage.ubuntu.com/kubuntu/bi...-live/current/)
> If you boot this image and select Try Ubuntu, you can see what it will look like without making any alterations to your system.
> The Preview button appears in the top row of Dolphin: [https://www.politicsbythenumbers.org...n-top-menu.png](https://www.politicsbythenumbers.org...n-top-menu.png) <
OK, I understand.
The fact is that I don't know much about Linux, and I learn slowly.
Thus, I would like to keep my Linux installation as basic as possible, without adding unnecessary layers.

So, if there's a way to shows a left panel with directories and sub-directories to the stock files manager, or if there's an other files manager that have left panel and shows image files' thumbnails, I'll not need Dolfin and KDE.

Thanks again, any way.

---

### Post by mandani48 on 2019-11-11
Hello Dennis N,

>> Please can any one tell-me how to set my Ubuntu installation so it shows thumbnails ? <<
> Tip:
> To best view thumbnails in directories with a lot of images, I suggest you try a program made for that: gthumb for gtk-based Ubuntu, and gwenview for qt-based Lubuntu or Kubuntu. <
Thanks for that tip.
As I understand, I've got GTK+ based Ubuntu Linux, thus I need gThumb.
        gThumb - an image viewer and browser for GNOME
        [http://manpages.ubuntu.com/manpages/bionic/en/man1/gthumb.1.html](http://manpages.ubuntu.com/manpages/bionic/en/man1/gthumb.1.html)

I'll try it on Wednesday.
Thanks again, any way.

---

### Post by Dennis N on 2019-11-11
> As I understand, I've got GTK+ based Ubuntu Linux, thus I need gThumb...
Correct. If you search for **gthumb** in Ubuntu Software, and then go to it's page there, you can see two screenshots of how it looks and install it.

---

### Post by mandani48 on 2019-11-21
Thanks a lot Dennis, it's exactly what I needed, that's fine now.
(Sorry for delay, I've been busy with other concern.)

---

