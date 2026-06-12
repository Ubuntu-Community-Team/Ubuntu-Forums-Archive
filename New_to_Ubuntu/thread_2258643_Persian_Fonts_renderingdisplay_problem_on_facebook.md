---
title: "Persian Fonts rendering/display problem on facebook"
date: 2014-12-29
forum: New to Ubuntu
---

### Post by jack_daniels3 on 2014-12-29
Hi, I was using ubuntu other day and i came across this weird problem related to display/rendering of persian fonts on facebook and other similar websites, i did install most of the popular persian fonts in order to make it go away but it was not the case.


Then, i read somewhere that Tahoma fonts was the main culprit for this issue so, i went on with copying my whole windows 8.1 fonts directory to /usr/share/fonts *i was asked to use .fonts folder but i couldn't find that folder* but that didn't fix the problem as it turned out the fonts access was limited to root only meaning i would have only accessed fonts there if i were to use any application in my case chrome/firefox as root.


so, when i tried it, it fixed the problem, but then because i wanted to use it normally, i had to change permissions of those fonts, which made firefox nuts, as it was unable to render simple english fonts correctly, but on chrome it was like as i was using it on windows, where i didn't have single problems with fonts rendering whatsoever.

Can't ubuntu do something about this so that new user wont have to face this problem?

---

### Post by Holger_Gehrke on 2014-12-29
Actually, it can't be simpler: open file manager, double click the font, fontviewer opens with a button "install font", klick the button -> DONE

---

### Post by jack_daniels3 on 2014-12-29
> **Holger_Gehrke said:**
> Actually, it can't be simpler: open file manager, double click the font, fontviewer opens with a button "install font", klick the button -> DONE
I have tried doing that, but i couldn't get it to work. The change in permissions of fonts directory plus lack of MS core fonts which i had to copy to usr/share/fonts directory made it work. Still, its not as perfect as it used to be in windows, where the fonts are somewhat more elegant/refined/crisp than being blurred/discontinuous/broken.

---

### Post by Ko_Char on 2014-12-29
actually, the font folder is in ~/.local/share/fonts
If you install a font (ttf for example) with double click, it will create the fonts folder automatically. 
If you don't, you need to create a new folder from right-click menu and rename it to "fonts" in ~/.local/share/ directory.
You don't need to change permission.

---

### Post by jack_daniels3 on 2014-12-29
> **Ko_Char said:**
> actually, the font folder is in ~/.local/share/fonts
If you install a font (ttf for example) with double click, it will create the fonts folder automatically. 
If you don't, you need to create a new folder from right-click menu and rename it to "fonts" in ~/.local/share/ directory.
You don't need to change permission.
Ok, May be you are right, but if thats the case, then i don't know why any of my web browser didn't display/access those fonts? I had to copy Tahoma fonts along with other Microsoft core fonts from Windows 8.1 to that directory and even then those were not working, after that i did little digging and found out that neither chrome nor firefox were using those fonts because of restricted permission as all of those fonts in that directory were limited to root user, so, that's why i changed the permission which solved the issue in Chrome, but totally messed up firefox, Anyway, those fonts are working on chrome but i still don't get this thing: why are my fonts not smooth or elegant in display as they are while using windows? They seem little blurred, i mean not as crispy as they are while i browse internet on windows.

What i would like is: Use ubuntu with windows fonts? Can i do that? To uninstall all the fonts in the ubuntu and then use windows one? Because i think that will solve the remaining problems.

---

### Post by jack_daniels3 on 2014-12-29
This is what helped me and why i changed permission level: [http://ubuntuforums.org/showthread.php?t=2216759&page=2](http://ubuntuforums.org/showthread.php?t=2216759&page=2)

---

### Post by bapoumba on 2014-12-29
If you want to install Windows fonts (and other License-restricted packages used to play video for ex, flash and such), install ubuntu-restricted-extras. More here :
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
[https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts](https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts)

---

### Post by jack_daniels3 on 2014-12-29
> **bapoumba said:**
> If you want to install Windows fonts (and other License-restricted packages used to play video for ex, flash and such), install ubuntu-restricted-extras. More here :
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
[https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts](https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts)
That i did by simply copying fonts from fonts folder located in MS windows, my problem was that none of my application had access to those fonts by default, which led to permission change. Isn't there anything which can be done to address this issue in upcoming releases?

---

### Post by bapoumba on 2014-12-29
Not everyone has a Windows partition to copy fonts from. The ubuntu-restricted-extras package has been providing them for a few years now, the issue has already been fixed several releases back :)
(and there already was another way before that).

---

### Post by jack_daniels3 on 2014-12-29
> **bapoumba said:**
> Not everyone has a Windows partition to copy fonts from. The ubuntu-restricted-extras package has been providing them for a few years now, the issue has already been fixed several releases back :)
(and there already was another way before that).
If that's the case then i am not sure why i was facing this issue on 14.04 LTS? I mean those fonts were pretty unreadable/broken/disconnected while i was using facebook or wikipedia in persian language; now that was solved by fixing permissions. 

Apart from firefox issue where all of them fail to render by default after i have fixed those permissions, those fonts on chrome appear bold/thick/non-clear *which gives the blurry impression* while i browse facebook/wikipedia which was not the case on MS Windows.

---

### Post by Ko_Char on 2014-12-29
> **jack_daniels3 said:**
> That i did by simply copying fonts from fonts folder located in MS windows, my problem was that none of my application had access to those fonts by default, which led to permission change. Isn't there anything which can be done to address this issue in upcoming releases?

It depends on how you copy the font. If you copy it in normal nautilus window, it will be non-root, accessible by applications without permission change. If you copy it in root (sudo nautilus or something like that), it will be root, not accessible by normal applications. It is not a bug

---

### Post by ajgreeny on 2014-12-29
All the fonts you will use in Ubuntu are stored in one of two places.

1. /usr/share/fonts
or for that user alone

2. /home/*user*/.fonts

I recommend you install them in the #1 location as if you install them to your /home directory they will not be accessible from another user account on the computer, including all the root utilities and applications.

First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```
I am using "myfonts" as an example; you can call it anything you like.

Next open a terminal in the folder where you have your needed ttf fonts and use command```
sudo cp ./*.ttf /usr/share/fonts/truetype/myfonts
```
This will copy the ttf fonts to that system folder. You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.

Now that we have the fonts in the proper folder we need to install them properly in Ubuntu by opening a terminal in the new  /usr/share/fonts/truetype/myfonts folder and using command ```
sudo fc-cache -f -v
``` which will install the fonts so that both your applications like LibreOffice, and any other users including the system utilities can use them.

---

### Post by Holger_Gehrke on 2014-12-29
> **jack_daniels3 said:**
> 
Apart from firefox issue where all of them fail to render by default after i have fixed those permissions, those fonts on chrome appear bold/thick/non-clear *which gives the blurry impression* while i browse facebook/wikipedia which was not the case on MS Windows.


<sarcasm>Hm, fonts published by a company that holds patents on font rendering enhancement algorithms don't look good without the use of those selfsame algorithms. Who could have imagined. </sarcasm>

Find some fonts that look OK in Linux and then set up a user style sheet for your browser to use those instead of Tahoma.

---

