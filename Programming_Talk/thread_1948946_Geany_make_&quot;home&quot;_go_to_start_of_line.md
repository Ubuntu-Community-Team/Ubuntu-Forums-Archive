---
title: "Geany: make &quot;home&quot; go to start of line"
date: 2012-03-29
forum: Programming Talk
---

### Post by Max Williams on 2012-03-29
Hi all.  I've recently switched from gedit to geany for my standard text editor in ubuntu and generally i'm pretty happy.  However there's one thing that's really bugging me:  when i press "home" it doesn't take me to the start of the line - it takes me to before the first non-whitespace char on that line, ie *after* the indentation.  

I've got so many years of muscle memory of "hit home and then delete/press space" to fix indentation and it's too late for me to change now :)  Any idea how i can tell geany that home means "go to the start of the line"?

In the Geany preferences, under keybindings, it has "Go to start of line: Home" already, which is irritating.  I discovered that alt&home goes to the *actual* start of the line, but i don't want to have to hit alt&home every time.  If i could swap the functionality of home and alt&home that would do me i think.  Can i do this in the config somehow?

I also noticed the same behaviour in notepad++ on my windows machine.  Is this a common behaviour?

thanks, max

---

### Post by Max Williams on 2012-03-29
Found the answer - thought i'd leave it up here in case anyone else googles it.  In the main geany config file, which for me is `~/.config/geany/geany.conf`, there's a line

pref_editor_smart_home_key=true

I set this to "false" and that sorted it.  I also noticed that when you exit geany it rewrites this file, overwriting changes done externally, so you need to close geany before making any changes to the config file.

---

### Post by r-senior on 2012-03-29
You don't need to edit the config file to make that change. It's on Edit > Preferences > Editor > Features > "Smart" Home Key.

---

### Post by Max Williams on 2012-04-02
> **r-senior said:**
> You don't need to edit the config file to make that change. It's on Edit > Preferences > Editor > Features > "Smart" Home Key.

So it is :) thanks.

---

