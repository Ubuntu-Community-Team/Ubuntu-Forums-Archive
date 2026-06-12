---
title: "how to create useful &amp;&amp; powerful user interface to bash program"
date: 2013-03-02
forum: Programming Talk
---

### Post by behnamvanda on 2013-03-02
Hi all
sorry for spam !
i wanna create user interface to my programs (coded with bash )
any body have intrest to design programs plz contact me with private message 
this is good project to developing back track 
i worked with this languages (c,c++,bash)
we can to form a cohesive team in developing linux :D
tnx for help :)

---

### Post by nwalkey on 2013-03-03
Bash is a scripting language is it not? From my knowledge I don't really see how you would create a user interface for it. Do you want an interface to create bash scripts? I can't see the use of that myself.

---

### Post by behnamvanda on 2013-03-03
yeah is it true bash is scripting language but i wanna creat user interface with [zenity]("http://library.gnome.org/users/zenity/stable/") and other gui maker tools but >> not have not enough option four this programs .

---

### Post by Tony Flury on 2013-03-05
> **behnamvanda said:**
> yeah is it true bash is scripting language but i wanna creat user interface with [zenity]("http://library.gnome.org/users/zenity/stable/") and other gui maker tools but >> not have not enough option four this programs .

There is a rule that says - pick the right tools for the job. 

So if you are trying to create an application which needs a rich feature-full GUI - use a programming language that can support that set of features - i.e. one that has libraries which support GTK or Tinker etc (such as python or C or C++ or Java).

If you have a bash script which needs some GUI features (progress bars, simple dialogs) - use zenity - if it needs full GUI features such as menu's, toolbars, multiple elements on a single window, multiple windows, drag and drop etc etc - re-write it in a langauge (as above) which has support for those features, as the chances are your bash script is probably so complex it probably should be written in a language which is better suited to complex applications.

Consider this - after all of this time Bash doesn't support full-featured GUIs - I would wager that it is because there is no real need for it do so.

If you already know bash and can get your head around all the escape chearacters and specials to access variables etc, then higher level scripting languages like python could well be fairly easy for you.

---

### Post by cortman on 2013-03-05
Zenity is limited. If you want a GUI use Python (PyGTK or PyQT) or some similar, better suited language.
In addition, please write clearly and without using txtspeak. It's hard to take a post seriously when it's poorly written.

---

### Post by Pinoy Tux on 2013-03-14
Depending on your requirements, you could give YAD (Yet Another Dialog) a shot.  It's "[zenity on steroids]("http://www.webupd8.org/2010/12/yad-zenity-on-steroids-display.html")."   I use it to create a graphical front-end for my timer scripts.  Here's an example that uses tabs and forms:

[IMG]https://dl.dropbox.com/u/5521153/screenshots/ubuntu/2013-03-14-yad-gui-frontend-shell-script-backend.png[/IMG]

Y-PPA Manager also use it.

---

