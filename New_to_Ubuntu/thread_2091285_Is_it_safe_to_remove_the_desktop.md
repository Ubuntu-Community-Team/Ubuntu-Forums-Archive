---
title: "Is it safe to remove the desktop?"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by Justin C on 2012-12-04
I don't use my desktop for files, I don't use a desktop wallpaper, it's useless to me but still needs to load everytime i boot up... so is there a way for me to remove the desktop? 

Thanks

---

### Post by papibe on 2012-12-04
Hi Justin C.

I'm not sure what you want to do.

Do you want to remove all graphic interface and work in text mode?
Do you want to get a simpler interface in order to boot faster?
Do you want to remove your wallpaper picture?

Regards.

---

### Post by Nightcreeper on 2012-12-04
Part of the "Desktop" that you use, if I understand what you are saying, is the menu, the clock, the notification area, etc. Without the desktop, you could I guess expand the menu bar at the bottom all the way to the top, but, then where would your apps open? That is the purpose of the desktop, a place for the running apps to be shown, the backgrounds and everything else is just a way of letting it do something when not covered by a program.

On the other hand, if you are referring to the GUI itself, then yes, you could uninstall the GUI and access most things via command line, though, without the GUI, I would suppose multitasking would be much harder if not impossible.

---

### Post by oldos2er on 2012-12-04
> **Nightcreeper said:**
> On the other hand, if you are referring to the GUI itself, then yes, you could uninstall the GUI and access most things via command line, though, without the GUI, I would suppose multitasking would be much harder if not impossible.

?? The presence or absence of any GUI has zero effect on Linux's ability to multitask.

I agree the OP should clarify what exactly they mean by "removing the desktop."

---

### Post by squakie on 2012-12-04
And.....without the desktop there wouldn't BE a task bar to expand!

---

### Post by squakie on 2012-12-04
> **oldos2er said:**
> ?? The presence or absence of any GUI has zero effect on Linux's ability to multitask.

I agree the OP should clarify what exactly they mean by "removing the desktop."

+1.  Back in the "old" days we ran Unix without a GUI - no problem running multiple "batch" jobs, interactive jobs (started from the command line but not forked), time-sharing for all the programmers, etc..

I also agree that I think the OP really wants something other than removing the desktop.  Perhaps they don't understand that one of the desktop managers is what gives them the GUI interface, so they need to re-word and expand on what they want.

---

### Post by Krytarik on 2012-12-05
> **Justin C said:**
> I don't use my desktop for files, I don't use a desktop wallpaper, it's useless to me but still needs to load everytime i boot up... so is there a way for me to remove the desktop?
That varies slightly depending on what version of Xfce you are using:

"Settings Manager -> System (header, since Xfce 4.10) -> Session and Startup -> Session (tab)":

[LIST=1]
[*]"xfdesktop" -> "Quit Program"
[*]"Thunar"    -> "Quit Program"
[*]"Save Session"
[/LIST]
To reset to default, ie. re-enable the desktop feature:

[LIST]
[*]"Clear saved sessions" (only since Xfce 4.10 / Xubuntu 12.10)
[*]alternatively, delete the content of "~/.cache/sessions" (hidden, in your home directory)
[/LIST]
Regards.

---

### Post by Krytarik on 2013-02-26
> **Krytarik said:**
> That varies slightly depending on what version of Xfce you are using:

"Settings Manager -> System (header, since Xfce 4.10) -> Session and Startup -> Session (tab)":

[LIST=1]
[*]"xfdesktop" -> "Quit Program" 
[*]"Thunar"    -> "Quit Program" 
[*]"Save Session" 
[/LIST]
To reset to default, ie. re-enable the desktop feature:

[LIST]
[*]"Clear saved sessions" (only since Xfce 4.10 / Xubuntu 12.10) 
[*]alternatively, delete the content of "~/.cache/sessions" (hidden, in your home directory) 
[/LIST]
Regards.
Just found a better way than that - similar to what I describe in this post, but just change "xfdesktop" to an empty string, i.e. "", obviously:

[http://ubuntuforums.org/showthread.php?p=12532124#post12532124](http://ubuntuforums.org/showthread.php?p=12532124#post12532124)
> **Krytarik said:**
> [QUOTE=cortman;12530750]There may be some useful information [here]("http://askubuntu.com/questions/53996/running-xubuntu-without-panels").In addition to the accepted answer there, if you are using the "Xubuntu" session, as opposed to the "Xfce" one, you need to modify "/etc/xdg/**xdg-xubuntu**/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml". You can either just change the entry "xfce4-panel" to an empty string, i.e. "", or change it to "cairo-dock" straight away, this way you don't even need an entry in startup applications for it.

If you are following that outcommenting route, however, you'd need to outcomment (with "<!-- ... -->") the panel's section in *both* "/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml" *and* "/etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml", otherwise it would just fall back to the latter.

Obviously, I'd choose the first way, much less hassle and the additional option to run the dock of your choice directly through it.[/QUOTE]

ADD.: Also, disabling the Thunar daemon isn't really necessary when only wanting to disable the desktop, and in fact rather undesirable when using it otherwise - just assumed the same behavior as Nautilus when it comes to drawing the desktop.

---

