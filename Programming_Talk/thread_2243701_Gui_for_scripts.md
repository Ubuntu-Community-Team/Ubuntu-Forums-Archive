---
title: "Gui for scripts"
date: 2014-09-10
forum: Programming Talk
---

### Post by jimmyh1972 on 2014-09-10
Hi
I need a gui to run some bash functions - I build something in Java to run the bash but there is a lot of permission problems, also runinng bash asking for root pass is impossible.
so what I need now is some box/window with about 5 buttons.
I tried also Zenity, Kdialod, Yad (I know them very good) but I didnt manage to add or edit the number of buttons
does anyone know how to build a simple gui with any of them (Zenity, Kdialod, Yad) so I'll be able to run my bash functions?

---

### Post by Habitual on 2014-09-10
> **jimmyh1972 said:**
> I'll be able to run my bash functions? Can you clarify these functions please?

```
#!/bin/bash
com=$(yad --title="My Script Runner" --height=200 --width=450 --list --separator=" & "  --checklist --column="1/0" --column=Command  \ 
--column=Script "" "Script1"  "gnome-terminal -e 'bash -c "/path/to/script1.sh"'" "" "Script2" "gnome-terminal -e 'bash -c "/path/to/script2.sh"'"  \
"" "Script3" "gnome-terminal -e 'bash -c "/path/to/script3.sh"'" ""  "Script4" "gnome-terminal -e 'bash -c "/path/to/script4.sh"'" "" "Script5" \ 
"gnome-terminal -e 'bash -c "/path/to/script5.sh"'" )
eval "$com"


``` Whatever you click gets run.

Refernce: [http://ubuntuforums.org/showthread.php?t=891851&p=5602475#post5602475](http://ubuntuforums.org/showthread.php?t=891851&p=5602475#post5602475)

Hope that gets you started.

---

### Post by Vaphell on 2014-09-11
still promoting that fugly, barely working eval hack? ;-)

---

### Post by Habitual on 2014-09-11
> **Vaphell said:**
> still promoting that fugly, barely working eval hack? ;-)

So, no Christmas card from you this year? :p
5m after I posted it, I said "Vaphell should answer this thread post, not me."

It was fun back in the day. I hardly have time for 'shiny' things made with yad.
I didn't author it, so I felt no need to improve upon it and not that I could.

Give us something better and I'll start using that instead. (half my scripts have your name in them already).

---

### Post by Pinoy Tux on 2014-09-14
> **jimmyh1972 said:**
> I tried also ... Yad ... but I didnt manage to add or edit the number of buttons
```
man yad
```
is your friend.  Use the **--form** option.  For example,

```
yad --title="My Script GUI" --form --columns=2 --no-buttons           \
    --field="Firefox":FBTN          "/usr/bin/firefox"                \
    --field="System Monitor":FBTN   "/usr/bin/gnome-system-monitor"   \
    --field="LibreOffice":FBTN      "/usr/bin/libreoffice"            \
    --field="Calculator":FBTN       "/usr/bin/gnome-calculator"       \
    --field="My Script":FBTN        "/path/to/my-script.sh"
```
will produce

[IMG]https://dl.dropboxusercontent.com/u/5521153/screenshots/ubuntu/2014-09-14-yad-buttons.png[/IMG]

Scalable? Yes.  Just add **--field***s* where applicable.  HTH.

---

### Post by Habitual on 2014-09-18
> **Pinoy Tux said:**
> 

[IMG]https://dl.dropboxusercontent.com/u/5521153/screenshots/ubuntu/2014-09-14-yad-buttons.png[/IMG]

and no "fugly, barely working eval hack?"
Good stuff. I'm sticking this on my [DorkBlog]("http://bournetoraiseshell.com/article.php?story=20110719205526639"), with credit.
Good bye eval. I never liked you!

---

