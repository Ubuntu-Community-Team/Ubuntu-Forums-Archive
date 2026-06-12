---
title: "rRootage controls"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by rootie on 2008-06-09
hello there, i'm on dvorak, and i'm having trouble playing rRootage (in the repos). the controls seem to be hardcoded, and the placement of the keys are uncomfortable in the layout i use. is there any way i can fix it?

thanks :D

---

### Post by red_Marvin on 2008-06-09
If they're hardcoded it's not much you can do except changing the keymap when playing, either by adding and setting up a keyboard indicator on your panel, or if you prefer the terminal, use setxkbmap.

**Keyboard indicator on panel:**
Right click on your gnome-panel, select *add to panel*.
Somewhere in the list there should be a keyboard generator, though I'm not sure about it's name, since I don't use an English localization personally.
It should have three flags as it's icon though.
Select it and chose *add*.
Right click on the indicator and choose keyboard settings->layouts and you should see a list containing your standard layout (dvorak of some sort).
Choose *add* and the keymap that you want.
Remember to select which layout you want to use by default and if you want separate layouts for each window.

Now each time you want to toggle the layouts, click once on the keyboard indicator on the panel.

**Terminal**
You can use [COLOR="DarkOliveGreen"]*setxkbmap layout variant*[/COLOR] to change to the variant of the layout you want. IE:
US layout: [COLOR="DarkOliveGreen"]*setxkbmap us*[/COLOR]
dvorak layout: [COLOR="DarkOliveGreen"]*setxkbmap dvorak*[/COLOR]
Swedish dvorak layout: [COLOR="DarkOliveGreen"]*setxkbmap se dvorak*[/COLOR]
and so on...

**Automation of the layout switching**
You can automate the keymap switching by creating a bash script:
```
#!/bin/bash
setxkbmap the_keymap_you_want_during_game
the_command_to_run_the_game
setxkbmap the_keymap_you_normally_use
```
Then you need to make it executable with the command [COLOR="DarkOliveGreen"]*chmod +x the_file_here*[/COLOR]

And now you can run the program by running the script (or create a launcher that runs the script if you want a menu entry)
that runs the script (don't forget to use absolute paths or prepend ./ to the script file name when running it from terminal).

---

