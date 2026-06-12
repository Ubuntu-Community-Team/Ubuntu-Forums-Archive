---
title: "Computer icon on Unity Panel"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pkg9991 on 2011-09-30
Is a there a way to get My Computer icon on the left hand side unity panel on 11.10
I read some help pages in which they said goto terminal and type
$ gconf-editor
and under apps>nautilus>desktop tick on computer_icon_visible
but whole desktop branch is missing under nautilus in my case.. so i'm not even able to display my computer icon on desktop.
I was then thinking of dragging it to the panel ;)
Somebody help!

---

### Post by pkg9991 on 2011-09-30
bump! no replies?

---

### Post by thatguruguy on 2011-09-30
What is this "My Computer" icon of which you speak?

---

### Post by mc4man on 2011-09-30
The new set of default unity launchers will include a gnome-control-center, though you wouldn't see that in an updated install

If you actually mean Computer then you need to either open dconf-editor > org > gnome > nautilus > desktop & disable, then enable "computer-icon-visible" to allow on Desktop
or for launcher
create a .desktop in ~/.local/share/applications with command of  nautilus computer:/// & icon of computer

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=nautilus computer:///
Name=Computer
Icon=computer
```

Note - there was a time previously where having a 'Computer' bookmark in nautilus could cause issue so YMMV with either of the above

---

### Post by pkg9991 on 2011-09-30
I want to put its shortcut on the left Unity panel

---

### Post by pkg9991 on 2011-09-30
@[mc4man]("http://ubuntuforums.org/member.php?u=320715") - Thanks man you rock!

Those who still did not know how to do.. here it is step by step
1) Press Ctrl+Alt+T
2) Type gedit
3) Copy Paste this code :
```
[Desktop Entry] 
Version=1.0 
Type=Application 
Terminal=false 
Exec=nautilus computer:/// 
Name=Computer 
Icon=computer


```4) Save the file on Desktop with the name Computer.desktop
5) Right click on the newly created icon, goto permissions and click "Allow executing file as program"
6) Drag and drop onto the unity panel.. DONE!

---

### Post by mc4man on 2011-09-30
A quick test suggests that this may not be a good idea for adding to the launcher - it may take over from the nautilus-home icon
as said YMMV

I'd look at using a quicklist entry instead if really needing this & it does take over

---

### Post by pkg9991 on 2011-09-30
actually i'm not getting you.. i'm not so technical please be light on the language :)
what's the exact issue you're talking about ie. taking over nautilus-home icon.. what does it mean?
what's the quicklist entry? 
and my home folder is working fine till now.. no issues yet..

---

### Post by pkg9991 on 2011-09-30
yeah! got it what you meant.. it totally takes over the home folder of nautilus :D :D
but still i'm loving it.. it's more clean to have it in unity panel then to first navigate to home then to computer

---

### Post by jbicha on 2011-09-30
By  the way, if you have your Desktop focused, you can just click Go>Computer as part of the Ubuntu/Nautilus desktop menu thing.

---

### Post by pkg9991 on 2011-09-30
@[jbicha]("http://ubuntuforums.org/member.php?u=898421") Right but it's not possible in ubuntu 2D

---

