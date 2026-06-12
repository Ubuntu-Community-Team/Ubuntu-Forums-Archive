---
title: "[lubuntu] how to change clock format (12/24) on login screen"
date: 2020-06-24
forum: New to Ubuntu
---

### Post by davepool on 2020-06-24
I've decided that Lubuntu 20.04 is one of the best OS options for an old Acer Aspire One 722 and everything about the installation and use has gone fine. 

But even though I'm able to access time and date for the clock in the panel...darn if I can figure out how/where to do the same for the clock on the login screen! As a result, I have the 12-hour display I want on the desktop, but I'm still seeing the 24-hour at login. Obviously, a solution is to just get past login quickly....but if there's a setting I've overlooked, I'd sure like to learn where it is.

---

### Post by guiverc on 2020-06-24
The settings you change once logged in will be for your Lubuntu/LXQt deskop. They do not impact the greeter or display manager which is `sddm` for Lubuntu.

The manual page for making changes to the greeter can be found at

 [URL="https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html"]https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html
[/URL]
but it notes "*There is no graphical application to do this currently.*"  (*one is being developed upstream*).

There are a number (of non-Lubuntu) wiki pages on `sddm` configuration, but I've not used any sorry (*selecting which desktop I'll use and the password entry field is all I've ever needed*).

---

### Post by davepool on 2020-06-24
Thanks for the reply, @guiverc. I checked that page and all I saw were instructions for changing autologin and theme. I guess I'll just sit tight and wait. At least now (via your reply) I know I didn't overlook something that was right there in front of me!

---

### Post by Holger_Gehrke on 2020-06-25
In the 'theme.conf' for the theme you're using -- you should have a directory for the theme in '/usr/share/sddm/themes/' -- there should be a section for localization with a line 'HourFormat=...' which takes a [qml time format string]("https://doc.qt.io/qt-5/qml-qtqml-date.html"). 

Holger

---

### Post by davepool on 2020-06-26
> **Holger_Gehrke said:**
> In the 'theme.conf' for the theme you're using -- you should have a directory for the theme in '/usr/share/sddm/themes/' -- there should be a section for localization with a line 'HourFormat=...' which takes a [qml time format string]("https://doc.qt.io/qt-5/qml-qtqml-date.html"). 

Holger

If I've understood you correctly (and it's entirely possible I haven't), when I use a text editor to open /usr/share/sddm/themes/lubuntu (because I'm pretty sure that's the default theme and the only other choice under "themes" is ubuntu-theme) when I then open up theme.conf as you suggested, the only thing there is:

[General]
background=wall.png

Just out of curiosity, I backed up to /usr/share/sddm/themes/ubuntu-theme, opened up the theme.conf there and it has the very same thing:

[General]
background=wall.png

---

### Post by GhX6GZMB on 2020-06-26
> **davepool said:**
> If I've understood you correctly (and it's entirely possible I haven't), when I use a text editor to open /usr/share/sddm/themes/lubuntu (because I'm pretty sure that's the default theme and the only other choice under "themes" is ubuntu-theme) when I then open up theme.conf as you suggested, the only thing there is:

[General]
background=wall.png

Just out of curiosity, I backed up to /usr/share/sddm/themes/ubuntu-theme, opened up the theme.conf there and it has the very same thing:

[General]
background=wall.png

Yes, you're in the wrong place. SDDM normally reads /etc/default/locale to define the clock format (as does the rest of Lubuntu). However, there is only a limited number of combinations existing. In Terminal, execute:

```
locale -a
```

This will show you the existing permutations.

Don't fiddle around with /etc/default/locale, though, you'll get out of sync with LXQt.

Instead, use the application menu, Preferences -> LXQt Settings -> Locale to select time etc., but keep in mind that only the existing permutations will work.

Personally, I use en_DK, which is brilliant: English language, but continental Europe formats. en_DK is a placeholder, en_EU would be more correct.

---

### Post by Holger_Gehrke on 2020-06-26
@ml9104: the clock in the default theme for the greeter uses a fixed format of "hh:mm" (no ap or AP afterwards, so that's a 24-hours display), not a locale dependent form. It does use Qt.DefaultLocaleLongDate for the date-display.

@davepool: Sorry, the theme I was looking at for reference defines it own clock object which will honour the setting I described. The lubuntu-theme uses the stock SddmComponents clock which does not.

I see three ways to change the clock in sddm to a 12 hour am/pm:

[LIST=1]
[*]change to a theme which has that option (I know for sure that the "Sugar"-theme does) 
[*]rewrite the theme and define your own clock 
[*]change the format string for the clock in /usr/lib/x86_64-linux-gnu/qt5/qml/SddmComponents/Clock.qml. There's a line in there that says 'text : Qt.formatTime(container.dateTime, "hh:mm")'. Change the format-string at the end from "hh:mm" to "h:mm ap" (or AP if you want AM/PM in capital letters; use "hh" instead of "h" if you want a leading "0" on the hours before 10; obviously this change will get overwritten if the package "sddm" gets updated necessitating a repeat of that patch). If you go this way, be sure to check that it works using 'sddm-greeter --theme /usr/share/sddm/themes/lubuntu' before logging out, otherwise an error will lock you out of the graphical environment (no big problem, you can still log in on a virtual console and revert the change, but better safe than sorry). 
[/LIST]
 
Holger

---

### Post by GhX6GZMB on 2020-06-26
Holger, thanks for the clarification. I won't pursue this any further, to me it's somewhat too much effort for a screen that is seen for a few seconds.

Cheers,  :)

---

### Post by davepool on 2020-06-26
> **ml9104 said:**
> Yes, you're in the wrong place. SDDM normally reads /etc/default/locale to define the clock format (as does the rest of Lubuntu). However, there is only a limited number of combinations existing. In Terminal, execute:

```
locale -a
```

This will show you the existing permutations.

Don't fiddle around with /etc/default/locale, though, you'll get out of sync with LXQt.

Instead, use the application menu, Preferences -> LXQt Settings -> Locale to select time etc., but keep in mind that only the existing permutations will work.

Personally, I use en_DK, which is brilliant: English language, but continental Europe formats. en_DK is a placeholder, en_EU would be more correct.

Ummm, okay. I'm looking at Preferences > LXQt Settings > Locale right now. ALL of the Detailed Settings are "selectable" by geographic location only. Consequently, for me, the current locale "United States - American English (en_US)" is the logical choice for the Time category. But, if it truly *was* tuned in to the U.S. standard, it would already be showing time in a 12-hour format. There's really no point in me changing this locale to somewhere else since most (everywhere else?) of the rest of the world uses 24-hour display.

Just to re-establish what I laid out in the original post: the clock in my panel (which *is* settable) is showing me time in the desired 12-hour format.  It's the clock that's displayed in the Lubuntu login screen that shows as 24-hour and, apparently, can't be changed.  Or at least the solution remains as yet unreported here.

---

