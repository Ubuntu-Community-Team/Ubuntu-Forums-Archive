---
title: "locking up"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-06-24
is there a ctrl-alt-del equivalent for Ubuntu?, because it seems to have been locking up a lot recently

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> is there a ctrl-alt-del equivalent for Ubuntu?, because it seems to have been locking up a lot recently

As in Ctrl+Alt+Del key combination to open your System Monitor in windoze?

Try to bind your key to open up gnome-system-monitor instead of displaying the Shutdown/Restart option.

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

```

```
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

---

### Post by pikabuntu on 2008-06-24
> **iaculallad said:**
> As in Ctrl+Alt+Del key combination to open your System Monitor in windoze?

Try to bind your key to open up gnome-system-monitor instead of displaying the Shutdown/Restart option.

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

```

```
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

could i make this a different key combo so i could keep the shutdown stuff with control alt delete, like  control alt end?
how could i do that?

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> could i make this a different key combo so i could keep the shutdown stuff with control alt delete, like  control alt end?
how could i do that?

Yes, change the Ctrl+Alt+Del combination.

---

### Post by Methuselah on 2008-06-24
Just curious, what kind of graphics card do you have?

BTW, many times you can get away with killing X only.
CTRL+ALT_BACKSPACE is the three finger salute for that.

Also, CTRL+ALT+F2 should take you to a command prompt (like DOS).
[Once in the command prompt ALT+F7 will take you back to your desktop with all programs in tact. Try it!]

In the Dos-like command prompt you can login by typing your username then <ENTER> key then your password <ENTER> key. 
Note that the password will not be echoed back so don't be surprised.

Then you can type 

```

sudo  reboot

```

and your machine will restart.

---

### Post by Dutch70 on 2008-06-24
You can also hold down "alt & print screen" buttons and slowly type R-S-E-I-U-B, be sure to pause for a couple seconds between each letter to give your pc time to do its thing. I cant remember what each letter does, but it is protecting your pc. and is preferred to a hard shutdown.

Dutch

---

### Post by pikabuntu on 2008-06-24
> **Methuselah said:**
> Just curious, what kind of graphics card do you have?

BTW, many times you can get away with killing X only.
CTRL+ALT_BACKSPACE is the three finger salute for that.

Also, CTRL+ALT+F2 should take you to a command prompt (like DOS).
[Once in the command prompt ALT+F7 will take you back to your desktop with all programs in tact. Try it!]

In the Dos-like command prompt you can login by typing your username then <ENTER> key then your password <ENTER> key. 
Note that the password will not be echoed back so don't be surprised.

Then you can type 

```

sudo  reboot

```

and your machine will restart.


how do i find out the graphics card?

---

### Post by Dutch70 on 2008-06-24
type lspci in terminal.

also check this thread for your first question, just to add to what Methuselah has taught us both.

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

Dutch

---

### Post by iaculallad on 2008-06-24
```
lspci | grep VGA
```

to be exact.

---

### Post by Methuselah on 2008-06-24
Type 

```
lspci
```

in a terminal and inspect the output for lines related to display or VGA.

If you want, you can pipe the output to grep to find the lines for you

```
lspci | grep -i vga 
```

Says to return only lines that have the word 'vga' in it.
The '-i' just means that the match should be case insensitive.

[I see many people responded already with the same approach :D]

---

