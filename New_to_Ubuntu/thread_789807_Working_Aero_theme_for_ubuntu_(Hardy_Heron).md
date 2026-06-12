---
title: "Working Aero theme for ubuntu (Hardy Heron)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-10
I need a good theme....like an aero theme or something.  I've seen a few (all from gnome-look), but none of the aero ones I tried seemed to work. I have used some themes, but others don't seem to want to cooperate. Is there something I need to install first?  What are those GTK 1 and GTK 2 things?  

Also, is there a dock for ubuntu?  I am used to using docks (I used objectdock on XP), si it'd be nice to have one for Ubuntu.

---

### Post by Joeb454 on 2008-05-10
There's plenty on gnome-look (I see you've already looked). Though I know a lot of users here aren't Aero's biggest fan's ;)

And you may want to look for Avant Window Navigator (AWN). It's a quite well featured dock that many people use (I've used it in the past :))

---

### Post by Rukaru on 2008-05-10
> **Joeb454 said:**
> There's plenty on gnome-look (I see you've already looked). Though I know a lot of users here aren't Aero's biggest fan's ;)

And you may want to look for Avant Window Navigator (AWN). It's a quite well featured dock that many people use (I've used it in the past :))

Well like I said...I've seen the aero themes on gnome look....i'm just asking about like the different typed of themes (GTK 1, GTK 2, etc)  and if I need to do or install something extra for theme to work.  And why do a lot of people here not like the aero interface?  it's just graphics...it's not like it turns ubuntu into vista. I don't really need aero...it's just that I've tried other high rated themes and they haven't worked.

---

### Post by gkrules on 2008-05-10
the gtk 2 ones all u hav to do is drag and drop them into the appearance program
then jus click it and click customize to change the other stuff


sometimes u hav to extract the files u download but most of the time u dont


have u seen linsta?

---

### Post by inportb on 2008-05-10
> **Rukaru said:**
> Also, is there a dock for ubuntu?  I am used to using docks (I used objectdock on XP), si it'd be nice to have one for Ubuntu.

If you have compositing support, AWN is a nice dock.

---

### Post by Joeb454 on 2008-05-10
> **Rukaru said:**
> Well like I said...I've seen the aero themes on gnome look....i'm just asking about like the different typed of themes (GTK 1, GTK 2, etc)  and if I need to do or install something extra for theme to work.  And why do a lot of people here not like the aero interface?  it's just graphics...it's not like it turns ubuntu into vista. I don't really need aero...it's just that I've tried other high rated themes and they haven't worked.

I didn't intend to make it sound like I thought Aero themes turned Ubuntu into Vista.

I just meant that some don't like it because of some of these reasons:
1) It *reminds* them of Vista
2) They just plain don't like it :p
3) They may want a more lightweight theme, etc.

Sorry, should've been a little clearer :)

---

### Post by adult swim on 2008-05-10
> **Rukaru said:**
> I need a good theme....like an aero theme or something.  I've seen a few (all from gnome-look), but none of the aero ones I tried seemed to work. I have used some themes, but others don't seem to want to cooperate. Is there something I need to install first?  What are those GTK 1 and GTK 2 things?  

Also, is there a dock for ubuntu?  I am used to using docks (I used objectdock on XP), si it'd be nice to have one for Ubuntu.

you might want to use emerald theme manager.  it works pretty good if you have compiz enabled.  you can get it by running ```
sudo apt-get install emerald
``` from a terminal.  then you can go to gnome-look and on the left pane select compiz and then you can browse the compatible themes.  to get the theme to load, you need to open emerald, system/preferences/emerald theme manager, and then you need to import the theme you downloaded.  you can do that by selecting import, and then navigating to where you saved the theme from gnome-look.  select the theme file and it should show up in emerald.  click on the theme and if it doesnt use change your theme automatically, hit alt-f2 and type in ```
emerald --replace
```

---

### Post by warbread on 2008-05-10
> **Rukaru said:**
> I need a good theme....like an aero theme or something.  I've seen a few (all from gnome-look), but none of the aero ones I tried seemed to work. I have used some themes, but others don't seem to want to cooperate. Is there something I need to install first?  What are those GTK 1 and GTK 2 things?  


To put it simply, a GTK theme will change almost everything that a windows decorator (Metacity, Emerald, Kwin, etc.) wouldn't change.  A windows decorator will change the status bar at the top of your windows and the close, maximize and minimize buttons and this is probably what you're looking for in a Vista theme.  If you are using Compiz, you might want to look into getting Emerald installed as that will give you lots of Vista-ish themes.  There are a few for Metacity as well.

GTK will change the color of your toolbars, scrollbars, status bars, drop down menus, etc.  GTK 2 themes are what you want.  Play around with different combinations.  Download GTK 2, Metacity and Emerald themes and mix and match until you're happy. You've got nothing to lose but time and hard drive space!

---

### Post by Rukaru on 2008-05-10
> **inportb said:**
> If you have compositing support, AWN is a nice dock.

I read about the compositing support stuff...but I'm still a little confused.  Do most mid-range 2006 desktops come with it?

---

### Post by warbread on 2008-05-10
> **Joeb454 said:**
> I didn't intend to make it sound like I thought Aero themes turned Ubuntu into Vista.

I just meant that some don't like it because of some of these reasons:
1) It *reminds* them of Vista
2) They just plain don't like it :p
3) They may want a more lightweight theme, etc.

Sorry, should've been a little clearer :)

For me, I hate where Vista has the close and max/min buttons.  There's a large gap on their sides and it weirds me out.  It's odd, but that's the main reason I have to change to the classic windows style anytime I use a Vista machine.

---

### Post by warbread on 2008-05-10
> **Rukaru said:**
> I read about the compositing support stuff...but I'm still a little confused.  Do most mid-range 2006 desktops come with it?
Compositing is a way the windows manager renders stuff on the desktop.  If you have Compiz enabled (System -> Preferences -> Appearance -> Desktop Effects tab - any of the options other than 'disabled' will work), then you have compositing enabled.

---

### Post by cchester on 2008-05-10
I just setup my wife's Ubuntu 8.04 machine to look like the Aero theme with different things.

Here is the list under Appearance Preferences:

1. Background - Anything you like.

2. Fonts from top to bottom Sans 10, Sans 10, Sans 10, Sans Bold 10, and Monospace 10.

3. Interface - Show icons in menus is checked.

4. Visual Effects - None since she is using a laptop.

5. Theme - Click customize

6. Controls - Aero-Clone

7. Colors  - Didn't change

8. Window Border - LiNsta3

9. Icons - nuoveXT-aero

10. Pointer aero-drop

Like I said I took bits and pieces from different things. I borrowed some from this great post too.

[http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html]("http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html")

If you can't drag and drop things into Appearance Preference and get them to install then you will most likely have to extract them and install them manually.

I added a picture of what it looks like. Hope it helps. The only thing is no dock.

---

### Post by Rukaru on 2008-05-10
> **warbread said:**
> To put it simply, a GTK theme will change almost everything that a windows decorator (Metacity, Emerald, Kwin, etc.) wouldn't change.  A windows decorator will change the status bar at the top of your windows and the close, maximize and minimize buttons and this is probably what you're looking for in a Vista theme.  If you are using Compiz, you might want to look into getting Emerald installed as that will give you lots of Vista-ish themes.  There are a few for Metacity as well.

GTK will change the color of your toolbars, scrollbars, status bars, drop down menus, etc.  GTK 2 themes are what you want.  Play around with different combinations.  Download GTK 2, Metacity and Emerald themes and mix and match until you're happy. You've got nothing to lose but time and hard drive space!

Ok yeah....emerald and mettacity....how do you get those?  Let's start with emerald.

---

### Post by warbread on 2008-05-10
You have metacity.  It's the default for Gnome and it uses less resources than Emerald.  Despite loving eye candy and Compiz in specific, I don't use Emerald for just this reason, even on my high end systems.  It messes with the GIMP.

Emerald is easy.

```
:-$ sudo apt-get install emerald
```

Then you need to get the themes.  For some reason, they're not in the repos anymore (at least I think so - has this changed for Hardy?)  You can download them from the last link at the bottom of [this page.]("http://ubuntuforums.org/showthread.php?t=727193")  Double click on it to install.

Then, press ALT + F2 and type in:

```
emerald --replace
```

You now have a slew of Emerald themes, at least one of which looks like Vista, I'm sure.  Gnome-look.org should have other Emerald themes to install.

---

### Post by fela on 2009-02-18
> **inportb said:**
> If you have compositing support, AWN is a nice dock.

You don't need a good graphics card for compositing (you don't even need compiz). If your graphics card can't run compiz (ie very old), you can make metacity (the default, ugly window manager) run in compositing mode by: running gconf-editor, then, within gconf editor go to apps > metacity > general and tick compositing_manager. Now you can run AWN with metacity.;)

---

### Post by handy on 2009-02-18
I use an Aero theme which I modified to suit my eyes as they like the dark I'm also using the Artwiz-boxed theme which only effects my title bars & the menu.

All of this is happening in Arch/Openbox/xfce4-panel .

---

