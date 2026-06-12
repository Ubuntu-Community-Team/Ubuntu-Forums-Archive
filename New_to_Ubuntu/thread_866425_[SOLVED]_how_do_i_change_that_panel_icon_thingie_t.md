---
title: "[SOLVED] how do i change that panel icon thingie thats the ubuntu symbol?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-21
so i m customizing my ubuntu desktop

iv alrdy changed the windows and im looking for a good backgroud (but thats not the point)

the theme i downloaded ([http://www.gnome-look.org/content/show.php/Cobra?content=58699]("http://www.gnome-look.org/content/show.php/Cobra?content=58699")) and it comes with instructions that have been helpful except theres a spot where it gets confusing

i removed the things on the panel at the top and added a new menu (a start menu with no text) but the instructions dont explain very well how to change the image from the ubuntu logo to the picture from the theme

help please

btw if u know about any nice backgrouds that would go with the theme please post links

thanks

:guitar:

---

### Post by perlluver on 2008-07-21
That looks like the tango icon theme.  You just change your icons to tango, or the icon theme that came with the theme.

---

### Post by jimi_hendrix on 2008-07-21
i love how responsive this forum is...

how do i do that?

and off topic how do i get one of those signiture thingies

---

### Post by mc4100 on 2008-07-21
You can change this in "gconf-editor", under

Apps -> Panel -> Objects -> Object_1
(Check, as yours might be different, that the "tooltip" has the value "Main Menu", if it doesn't then check the different Objects like 2,3,4 etc, until you find one which has the "Main Menu" tooltip)
Tick use custom icon
Set the "custom icon" value to the path of the icon you want.

---

### Post by jimi_hendrix on 2008-07-21
uhh i dont have an application thing...i changed it to a single main menu to go along with the theme and when i click that i dont see a panel thing

---

### Post by mc4100 on 2008-07-21
> **jimi_hendrix said:**
> uhh i dont have an application thing...i changed it to a single main menu to go along with the theme and when i click that i dont see a panel thing
Sorry, I wasn't clear, you misunderstand: I wasn't talking about a menu entry -- although I think, while not shown by default, gconf-editor *does* have one (Under, Applications -> System Tools)
Anyway... Just press, Alt+F2, and type:
```
gconf-editor
```
Then follow the previous instructions. ;)

---

### Post by jimi_hendrix on 2008-07-21
ty soooooo much

---

### Post by lhb1142 on 2008-07-21
This is my favorite Ubuntu Desktop Background. Of course there are lots more.

[http://technology.desktopnexus.com/wallpaper/16274/](http://technology.desktopnexus.com/wallpaper/16274/)

Just download it, move it to "Pictures" (you may want to create a folder in "Pictures" called, for example, "Ubuntu Backgrounds"), go to System->Preferences->Appearance->Background. Click < + Add > and then browse for your downloaded background file in your "Pictures." When you find it, just "open" it - this adds it to your Backgrounds and sets it as your background- this is straightforward. Other backgrounds can be downloaded and added just as easily. Though I haven't tried it, I believe you could make any suitable .jpg picture your background.

You can do something similar to change your "Login" page if you have one.

I hope this is of some use to you.

---

### Post by perlluver on 2008-07-21
> **jimi_hendrix said:**
> i love how responsive this forum is...

how do i do that?

and off topic how do i get one of those signiture thingies

To get the signature, go to the user CP and, edit your profile, and signature.

---

### Post by jimi_hendrix on 2008-07-21
ok ty and one last thing...whats an emrald theme manager and how do i get there...then shiney thank you's to u all

---

### Post by mc4100 on 2008-07-21
> **jimi_hendrix said:**
> ok ty and one last thing...whats an emrald theme manager and how do i get there...then shiney thank you's to u all
Emerald is a window decorator for Compiz-fusion, which is a window manager that uses OpenGL and Compositing. Basically, it uses your graphics card instead of the CPU which speeds things up, among other things.
Compiz is enabled by default in Ubuntu if your hardware supports it. You can get emerald by typing:
```
sudo apt-get install emerald
```
But check if you have hardware that supports running compiz. Once emerald is installed, you can run it by typing into a terminal:
```
emerald --replace &
```
Also, you'll have its theming app called "Emerald Theme Manager", under System -> Preferences (I think). 
Themes for it can be found in the "Beryl" section of [www.gnome-look.org](www.gnome-look.org)

---

### Post by jimi_hendrix on 2008-07-22
thank you all

---

