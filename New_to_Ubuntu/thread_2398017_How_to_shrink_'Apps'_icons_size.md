---
title: "How to shrink 'Apps' icons size ?"
date: 2018-08-06
forum: New to Ubuntu
---

### Post by Innernet on 2018-08-06
The 'dock' icons were able to be reduced, but cannot find the way for the ones showing when opening  'Apps'  :::

What is the way to do it ?

---

### Post by deadflowr on 2018-08-06
You mean the transparent overview window(ish thing).
I don't think those can be resized. At least not in any normal manner.
I believe they are set.
Perhaps there is an extension that can do this in gnome extensions:
[https://extensions.gnome.org/]("https://extensions.gnome.org/")

It might be possible to resize it by mucking about the gnome shell theme file in /usr/share/gnome-shell.
But the theme file is now a gresource binary file that you'd need to extract, play with and then recompile.
And I'm not sure where you'd need to look with the file to make that change.

---

### Post by Innernet on 2018-08-06
Hi.  Thanks.
Not the ::: , the icons.
Looking for a picture to paste here as reference, found this same request.  Comments on the answer, please ?

----> [https://askubuntu.com/questions/1049325/how-do-i-resize-dash-app-icons-ubuntu-18-04](https://askubuntu.com/questions/1049325/how-do-i-resize-dash-app-icons-ubuntu-18-04)

---

### Post by Frogs Hair on 2018-08-06
There is a 3rd party Gnome Shell that will do this, but it makes the icons very small even on a laptop . 

[https://www.gnome-look.org/p/1174444/](https://www.gnome-look.org/p/1174444/)

---

### Post by deadflowr on 2018-08-06
> **Innernet said:**
> Hi.  Thanks.
Not the ::: , the icons.
Looking for a picture to paste here as reference, found this same request.  Comments on the answer, please ?

----> [https://askubuntu.com/questions/1049325/how-do-i-resize-dash-app-icons-ubuntu-18-04](https://askubuntu.com/questions/1049325/how-do-i-resize-dash-app-icons-ubuntu-18-04)

That's what I said., Er, or meant.
I mean the icons in the transparent window for apps.
ie, the menu overview system.

Edit: Droid shell themes works.
I guess if you look through the droid shell theme css file you might find the appgrid (or something along those lines) section to adjust the icons even more.

Double
> Comments on the answer, please ?
I'll be gone for a while, but I'll come back with a more fluid answer.

---

### Post by deadflowr on 2018-08-06
> Comments on the answer, please ?


Okay, after reading the askubuntu link that would work fine.
Or
You can create a small file for your local user that you can set the small changes like this in.



To do that you create a local  (and hidden) .themes folder, then create a folder in the .themes folder called anything you want.
Then you make a folder called gnome-shell.
And then you create a file called gnome-shell.css.
(So the path would be /home/your-username/.themes/Something/gnome-shell/gnome-shell.css)
Inside this file you put this

```
@import url("/usr/share/gnome-shell/theme/gnome-shell.css");
.icon-grid {
  spacing: 30px;
  -shell-grid-horizontal-item-size: 136px;
  -shell-grid-vertical-item-size: 136px; }
  .icon-grid .overview-icon {
    icon-size: 96px; }
```
Then in the program Tweaks (gnome-tweaks or gnome tweak tool) you can set whatever you named the main folder as you shell theme, and it'll use the setting for icon-grid you set in that folder.
(But also use the main system gnome-shell.css file for everything else.)
This way you can lay around with tweaking it without having to always run as root.

(It'll also allow you to add other theme settings you want to play around with,
but also keep the original system gnome-shell theme file safe and intact)

Does that make sense?


**EDIT:** I forgot to mention you need to enable the user-theme extension.
If you don't have that extension, it can be installed with the gnome-shell-extensions package (which installed a few extra extensions.)
Or search Ubuntu Software for user-themes.

(user-theme is paramount to using the customized shell themes.
I always have user-themes on, and forget it's usually not on or installed by default)

---

