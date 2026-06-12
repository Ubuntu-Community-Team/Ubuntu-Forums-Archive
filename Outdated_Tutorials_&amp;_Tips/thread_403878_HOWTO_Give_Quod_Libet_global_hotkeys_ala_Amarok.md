---
title: "HOWTO: Give Quod Libet global hotkeys ala Amarok"
date: 2007-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Xyhthyx on 2007-04-07
Hop into the terminal or application launcher and type:

```
gconf-editor
```

Travel down from the tree to:

```
apps->metacity->keybinding_commands
```

Here you will find command_1 through command_12. Edit the following keys by double clicking to the following:

command_1  =  quodlibet --previous
command_2  =  quodlibet --play
command_3  =  quodlibet --play-pause
command_4  =  quodlibet --pause
command_5  =  quodlibet --next

Now go to:

```
apps->metacity->global_keybindings
```

Here you will find (in addition to other keys) the keys run_command_1 through run_command_12. Edit the following keys to include the following:

run_command_1  =  <mod4>z
run_command_2  =  <mod4>x
run_command_3  =  <mod4>c
run_command_4  =  <mod4>v
run_command_5  =  <mod4>b

**Done!**

Now you can control Quod Libet with the following global hotkeys:

<Windows> + Z  =  Previous Track
<Windows> + X  =  Play
<Windows> + C  =  Play/Pause
<Windows> + V  =  Stop
<Windows> + B  =  Next Track

---

### Post by Echow on 2007-06-01
Neat thanks heaps.
Ed

---

### Post by hyperair on 2007-06-09
If you use Beryl you'll have to put those commands into Beryl instead. Same goes for Compiz.

---

### Post by ird on 2009-06-05
Sorry to bring back an old thread, but I have a question.

What if I wanted to use Shift-Ctrl instead of the win key? (Or alt, etc for that matter)

---

