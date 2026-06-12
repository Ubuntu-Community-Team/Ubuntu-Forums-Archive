---
title: "How to modify login screen?"
date: 2018-12-02
forum: New to Ubuntu
---

### Post by meslas on 2018-12-02
How can I modify the login screen? I am using Lubuntu 18.10 :o

---

### Post by Autodave on 2018-12-02
Can you be a little more specific as to what you are hoping to modify?

---

### Post by Dennis N on 2018-12-02
Lubuntu 18.10 login screen has themes. You can install these from Ubuntu repository. Search for "sddm". Attached is screenshot of **sddm-theme-maui** that I installed on mine. Requires some extra work afterwards to get it to display. Ask if you decide you want to install.

---

### Post by Dennis N on 2018-12-02
Here's an entirely different screen style (attached) with **sddm-theme-elarun**. Looks like it would be fairly easy to change just the background on any of these if you wanted to do that.

---

### Post by meslas on 2018-12-02
> **Dennis N said:**
> Lubuntu 18.10 login screen has themes. You can  install these from Ubuntu repository. Search for "sddm". Attached is  screenshot of **sddm-theme-maui** that I installed on mine.  Requires some extra work afterwards to get it to display. Ask if you  decide you want to install.

Yes, I would like this theme. I downloaded **sddm-theme-maui **through apt-get and how do I get it to display now?

---

### Post by Dennis N on 2018-12-03
> **meslas said:**
> Yes, I would like this theme. I downloaded **sddm-theme-maui **through apt-get and how do I get it to display now?

Hello meslas,

After installing theme from repository, you need to edit the sddm configuration file located at:
**/etc/sddm.conf**

**Add** the following lines:

```
[Theme]
ThemeDir=/usr/share/sddm/themes
Current=maui

```
Save the edited file. Log out and back in and it should be working. To use a different theme, just edit again and change Current= to the another theme.

_User Picture in some themes:_

In the maui theme, you can have a picture with your login box. The image file must be named in a certain way:** .face.icon** and located in your home folder. Important: Notice the period at beginning of the file name, which makes it a hidden file. If left out, it won't be used. 

After some experimenting, it seems the picture used in maui theme is a square shape, 256x256 pixels from what I see. If not, the theme will resize it. If its not square, it will be trimmed on the longer dimension. I used a .png image. Maybe it could be .jpg as well.

I got all the information from studying the documentation links here:

[https://jlk.fjfi.cvut.cz/arch/manpages/listing/extra/sddm/](https://jlk.fjfi.cvut.cz/arch/manpages/listing/extra/sddm/)

Hope you like your new log in screen.

---

### Post by meslas on 2018-12-03
> **Dennis N said:**
> 
Hope you like your new log in screen.

Thank you very much! Everything works perfectly!

---

### Post by zeiken on 2019-01-05
Cannot save, permission denied. Also I have 2 sddm.conf files..I give up, I'll keep the gray icon for login window sigh

---

### Post by zeiken on 2019-01-05
*EDIT* After a whole week of trying to find a fix, I finally found it.  The fix was quite easy, instead of saving an image as .face, save the  image as .face.icon  in your /home/(username) folder. Not sure if image  should be a .PNG file or not, but my image I saved as a png with no  extensions. Might want to save the image with equal dimensions, though  I'm not sure if it makes a difference. Didn't even need to use a  different lock/start screen manager or different theme. Lubuntu 18.10  out of the box.   --- This is for those wanting to just change User icon in lock/start screen

---

### Post by Dennis N on 2019-01-05
> **zeiken said:**
> Cannot save, permission denied. Also I have 2 sddm.conf files.. FFS I give up, I'll keep the gray icon for login window sigh

The file /etc/sddm.conf is owned by root, so this file can only be edited by opening it with administrative permissions. To edit this file in the terminal with the nano text editor and with administrative permissions, type:

```
sudo nano /etc/sddm.conf
```

When finished adding the extra lines, CTRL-O will save the edited file, and CTRL-X will exit the editor. You may want to practice using the nano editor with a practice file first where you can do no harm. You don't use the preface sudo if the file you are editing is in your home folder.

Changing the user image is explained in post #6 above.

---

### Post by zeiken on 2019-01-06
> **Dennis N said:**
> The file /etc/sddm.conf is owned by root, so this file can only be edited by opening it with administrative permissions. To edit this file in the terminal with the nano text editor and with administrative permissions, type:

```
sudo nano /etc/sddm.conf
```

When finished adding the extra lines, CTRL-O will save the edited file, and CTRL-X will exit the editor. You may want to practice using the nano editor with a practice file first where you can do no harm. You don't use the preface sudo if the file you are editing is in your home folder.

Changing the user image is explained in post #6 above.

Thanks man, that worked, got the maui theme installed without issues, question though.. Is there a way I can keep this theme but change the background image? (for the login screen) and maybe change the way the clock/time is displayed (non military)? Probably pushing my luck at this point, but I'd like to have it look how I want :)

---

### Post by Dennis N on 2019-01-06
>  Is there a way I can keep this theme but change the background image? (for the login screen) and maybe change the way the clock/time is displayed (non military)?

Well, there are images packaged in the theme. Looks to me like you could substitute. We know the themes are stored in /usr/share/sddm/themes. For example, maui has a theme folder there.

```
dmn@Roxanne:/usr/share/sddm/themes/maui$ ls -l
total 388
-rw-r--r-- 1 root root    185 Jul 27 06:15 angle-down.png
-rw-r--r-- 1 root root    159 Jul 27 06:15 angle-left.png
-rw-r--r-- 1 root root    165 Jul 27 06:15 angle-right.png
-rw-r--r-- 1 root root 216158 Jul 27 06:15 background.png
-rw-r--r-- 1 root root  22165 Jul 18 03:31 LICENSE
-rw-r--r-- 1 root root   9404 Jul 18 03:31 Main.qml
-rw-r--r-- 1 root root 108867 Jul 18 03:31 maui.jpg
-rw-r--r-- 1 root root    352 Jul 18 03:31 metadata.desktop
-rw-r--r-- 1 root root    562 Jul 18 03:31 README
-rw-r--r-- 1 root root    496 Jul 27 06:15 reboot.png
-rw-r--r-- 1 root root    513 Jul 27 06:15 shutdown.png
-rw-r--r-- 1 root root     47 Jul 18 03:31 theme.conf

```
Looks to me like you possibly could switch **background.png** to another image (but use same name) of the same size. Try that and see what happens. 
And **Main.qml** looks like it defines other aspects of the login screen. Maybe the clock format you ask about is defined in there. 

Have fun experimenting. I suggest backing up this folder before making changes so you can restore it if things go south.

---

