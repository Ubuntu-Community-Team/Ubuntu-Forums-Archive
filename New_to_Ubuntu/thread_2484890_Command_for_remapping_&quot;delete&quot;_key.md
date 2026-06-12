---
title: "Command for remapping &quot;delete&quot; key"
date: 2023-03-13
forum: New to Ubuntu
---

### Post by dclntn on 2023-03-13
Good day,
I am new to Ubuntu and wish to remap the left key of my keyboard to use it as del "delete" key (keeping anyhow the right delete key as unchanged)

I found in "Settings > Keyboard > View and customize keyboard > custom shortcuts > Add custom shortcuts, with 3 lines to be filled:
Name:                             I understand this is the new name I want for designation of my new shortcut, ok
Command:                      I understand this is the "delete" command I should enter here to use the shortcut as I want to do, as a "delete" key
Shortcut, add shortcut:   I understand this is the (left) key of my keyboard I want to use as a new "del" key, ok ( I just have to click on the chosen key of my keyboard)

The help file is not clear for me on this item, how to I enter the right "delete" command in the second line ? /  I tried to enter the word "delete", or the word "del" but this do not work

As an other option, if I wish to use the "loudspeaker high" key as an alternative to the del key, what would be the command to use?

Thanks for your help,

---

### Post by MAFoElffen on 2023-03-13
What might be easier for you is xkeycaps: [https://manpages.ubuntu.com/manpages/jammy/man1/xkeycaps.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/xkeycaps.1.html)

Here is a YouTube video on how to use it: [https://www.youtube.com/watch?v=hJ34yW8qJrU](https://www.youtube.com/watch?v=hJ34yW8qJrU)

---

### Post by DuckHook on 2023-03-14
I do believe that xkeycaps and its underlying utility xmodmap no longer work under Wayland. If OP is still using X11, then these two utilities are fine, but Wayland will nerf them.

@dclntn

Please follow the instructions in the link in my sig: Remapping Keys

---

