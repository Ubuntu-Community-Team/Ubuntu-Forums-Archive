---
title: "Pastie"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by goonybird on 2012-11-24
Hello

I have installed Pastie and it shows up in the Dash but when I click the icon nothing happens. It was a bit difficult to install and there seem to be many ways to do it. Most references I found were for Ubuntu versions 10 and 11. Does anyone know if Pastie will run on Precise Pangolin?

Unity desktop

Thanks

---

### Post by stinkeye on 2012-11-24
You may have to add it to the systray-whitelist.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12362081&postcount=4")
Same method, different clipboard manager.

---

### Post by goonybird on 2012-11-24
Hello stinkeye, thanks for your reply.

Installed Unsettings. Interesting utility. Added Pastie to whitelist but to no avail.

Thanks

---

### Post by Frogs Hair on 2012-11-24
I did not have to add a white list entry when using Pastie with Unity 12.04/12.10. All that was required was starting Pastie from dash and then setting it start automatically from preferences. Try starting from the terminal by typing the name in lower case. I installed using a .deb package because the PPA was not updated at that time.

---

### Post by goonybird on 2012-11-25
Thanks frogshair. 

I installed from deb package too for same reasons. Clicking Pastie in dash does nothing.
Running from terminal [hadn't tried that, thanks] gives me two error messages:

[LIST]
[*]ValueError: need more than 1 value to unpack
[*]ImportError: No module named gnomevfs
[/LIST]
Does that second one mean it only works on Gnome? I'm using Unity.

---

### Post by stinkeye on 2012-11-25
Don't know why the error with pastie.
Try glipper as your clipboard manager as it still seems to be actively developed.

---

### Post by goonybird on 2012-11-25
Thanks.

Pardon my ignorance here - isn't glipper for Gnome? I'm using Unity. How much do these desktops overlap with regard to apps?

---

### Post by stinkeye on 2012-11-25
I use glipper with unity.
Both gnome and unity use a gnome3 desktop enviroment.

The gnome session uses **gnome-shell** for interaction with the GNOME3 desktop and
is intended to replace functions handled by the GNOME Panel and by the
window manager in previous versions of GNOME. Mutter is the window manger for gnome-shell.

The Ubuntu session interacts with the GNOME3 desktop using unity which is just a plugin for the window manager, Compiz.

So they both use the gnome3 desktop enviroment but with different window managers.

---

### Post by goonybird on 2012-11-29
Thanks for that explanation. I understand things a bit more clearly now.

I have installed glipper, seems to do the job. Thank you.

And thanks for your help and suggestions. Much appreciated.

---

