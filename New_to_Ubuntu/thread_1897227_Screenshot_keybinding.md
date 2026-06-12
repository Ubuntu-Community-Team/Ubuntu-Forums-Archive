---
title: "Screenshot keybinding"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by Worp8d on 2011-12-18
Is is possible to change the screenshot key in lubuntu? I keep dropping the keyboard and filling my drive up with pics so I want to change it from PrintScreen to Alt-PrintScreen. I assume there's a file listing keybindings somewhere but I can't find it.

---

### Post by lechien73 on 2011-12-18
I believe the keybindings for Lubuntu are stored in ~/.config/openbox/lubuntu-rc.xml

You can change the Print Screen key settings there.

---

### Post by Worp8d on 2011-12-20
You are quite right, I can see the keybindings in there, but I can't find the scrrenshot key despite much searching with every string I can think of.

---

### Post by lechien73 on 2011-12-21
Ok, can you search for "Print"? The section you're looking for probably looks like this:

```
<keybind key="Print">
      <action name="Execute">
       <execute>scrot</execute>
      </action>
    </keybind>
 
    <keybind key="A-Print">
      <action name="Execute">
       <execute>scrot -s</execute>
      </action>
    </keybind>
```

"Print" is what happens when the screenshot (PrntScrn or Print Screen) key is pressed. "A-Print" is what happens when Alt+PrntScrn is pressed.

---

### Post by amjjawad on 2011-12-22
> **lechien73 said:**
> Ok, can you search for "Print"? The section you're looking for probably looks like this:

```
<keybind key="Print">
      <action name="Execute">
       <execute>scrot</execute>
      </action>
    </keybind>
 
    <keybind key="A-Print">
      <action name="Execute">
       <execute>scrot -s</execute>
      </action>
    </keybind>
```"Print" is what happens when the screenshot (PrntScrn or Print Screen) key is pressed. "A-Print" is what happens when Alt+PrntScrn is pressed.

You are right:

```
<!-- Keybinding for PrintScreen Key -->
    <keybind key="Print">
      <action name="Execute">
       <execute>scrot</execute>
      </action>
    </keybind>

    <keybind key="A-Print">
      <action name="Execute">
       <execute>scrot -s</execute>
      </action>
    </keybind> 
```

Alt-Print Screen is used "scrot -s". You can change that as per your need.

By the way, just curious, why you want to change that? I didn't understand the reason :)

---

