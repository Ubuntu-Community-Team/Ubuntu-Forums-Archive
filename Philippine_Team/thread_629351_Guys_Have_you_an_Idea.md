---
title: "Guys Have you an Idea?"
date: 2007-12-02
forum: Philippine Team
---

### Post by MSC5-28 on 2007-12-02
Help naman panu pagalawin yong mismong wallpaper ng ubuntu masyado cgurung mahirap.... I just want to try... thanks!!!!

---

### Post by pinoyskull on 2007-12-03
what do you mean?

Animated wallpaper or automatic ang pag change ng wallpaper?

---

### Post by kopinux on 2007-12-04
baka naman yung cube yon?

ito check mo din ito
[http://www.robbief.com/content/view/35/36/](http://www.robbief.com/content/view/35/36/)

---

### Post by elite_angel on 2007-12-05
Its unclear question... Hmm? Look at my reply title, its clear. haha!

Well, anyway what do you mean by "gumagalaw ang wallpaper?"

---

### Post by raxso on 2007-12-07
> Guys Have you an Idea? 


Hmmmmnnnn Let me think..... have you.

---

### Post by loell on 2007-12-07
currently, the only desktop environment that implements animated wallpaper is **E17**

there is no common implementation in gnome yet, the only work around is **xwinwrap** if i'm not mistaken.

edit:

here is something to tinker, [http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/]("http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/")

---

### Post by raxso on 2007-12-10
Baka ito gusto mo mangyari...

Screensaver as Desktop Wallpaper 

Ito ay ginagawa sa pamamagitan ng pag disable panandalian ng nautilus desktop at papalitan ng xscreensaver.pero di xa ok kung gumagamit ka ng Compiz Fusion. :) (Beware if you are using Compiz)

Unang command:
# gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false 

pangalawang command:

# /usr/lib/xscreensaver/glmatrix -root


Kung gusto mo ng animation kada login mo,open &#8220;~/.config/autostart/glmatrix.desktop&#8221; sa text editor and paste mo yung command na ito.

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_IN]=Desktop matrix
Exec=/usr/lib/xscreensaver/glmatrix -root
X-GNOME-Autostart-enabled=true

Have fun.... for more tips visit my site [http://raxso-linux.blogspot.com](http://raxso-linux.blogspot.com)

---

### Post by mitchi on 2007-12-11
nice one sir raxso.. galing.. astig..

---

### Post by mitchi on 2007-12-11
> **raxso said:**
> Kung gusto mo ng animation kada login mo,open “~/.config/autostart/glmatrix.desktop” sa text editor and paste mo yung command na ito.

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_IN]=Desktop matrix
Exec=/usr/lib/xscreensaver/glmatrix -root
X-GNOME-Autostart-enabled=true



may alternative na gumana sa akin.

system > preferences > sessions

tapos dun sa command, type nyo to
> /usr/lib/xscreensaver/glmatrix -root

---

### Post by business.geek on 2007-12-11
> **raxso said:**
> Baka ito gusto mo mangyari...

Screensaver as Desktop Wallpaper 

Ito ay ginagawa sa pamamagitan ng pag disable panandalian ng nautilus desktop at papalitan ng xscreensaver.pero di xa ok kung gumagamit ka ng Compiz Fusion. :) (Beware if you are using Compiz)

Unang command:
# gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false 

pangalawang command:

# /usr/lib/xscreensaver/glmatrix -root


Kung gusto mo ng animation kada login mo,open “~/.config/autostart/glmatrix.desktop” sa text editor and paste mo yung command na ito.

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No name
Name[en_IN]=Desktop matrix
Exec=/usr/lib/xscreensaver/glmatrix -root
X-GNOME-Autostart-enabled=true

Have fun.... for more tips visit my site [http://raxso-linux.blogspot.com](http://raxso-linux.blogspot.com)

coolness!:)

---

### Post by ichi_730 on 2007-12-13
waaaaaaaaaaa!! puro codes!!!:shock:

---

