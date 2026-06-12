---
title: "Adding a line to etc/modprobe.d/options"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by J.sanchez on 2008-06-17
I've been trying to add a line to etc/modprobe.d/options per the instructions [here]("https://help.ubuntu.com/community/MacBook_Santa_Rosa"), but I can't.

I'm opening the file in MousePad and trying to save it, but I can't.  

I've tried changing properties on the folders and the files, but I am clearly missing something, as aparently I can'.

---

### Post by sdennie on 2008-06-17
Are you sure you are putting sudo in front of the edit command?  Those instructions for editing /etc/modprobe.d/options looks correct to me.

---

### Post by J.sanchez on 2008-06-17
I type this in terminal
[INDENT] sudo edit /etc/modprobe.d/options options snd_hda_intel model=mbp3  
[/INDENT]

and get this
[INDENT]
Warning: unknown mime-type for "/etc/modprobe.d/options" -- using "application/*"
Warning: unknown mime-type for "options" -- using "application/*"
Warning: unknown mime-type for "snd_hda_intel" -- using "application/*"
Warning: unknown mime-type for "model=mbp3" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"[/INDENT]

I know I'm doing something wrong, but I don't know what.

A link to a good resource would be enough.

---

### Post by bufsabre666 on 2008-06-17
this might sound stupid but are you including the / before etc?

your command should look like
```
sudo gedit /etc/modprobe.d/options
```

---

### Post by bufsabre666 on 2008-06-17
> **J.sanchez said:**
> I type this in terminal
[INDENT] sudo edit /etc/modprobe.d/options options snd_hda_intel model=mbp3  
[/INDENT]

and get this
[INDENT]
Warning: unknown mime-type for "/etc/modprobe.d/options" -- using "application/*"
Warning: unknown mime-type for "options" -- using "application/*"
Warning: unknown mime-type for "snd_hda_intel" -- using "application/*"
Warning: unknown mime-type for "model=mbp3" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"
Error: no "edit" mailcap rules found for type "application/*"[/INDENT]

I know I'm doing something wrong, but I don't know what.

A link to a good resource would be enough.

no open /etc/modprobe.d/options
```
sudo gedit /etc/modprobe.d/options
```

then add the line

options snd_hda_intel model=mbp3

to the end of the file

save and close

---

### Post by J.sanchez on 2008-06-17
> **bufsabre666 said:**
> this might sound stupid but . . . 

Ah, but you see, when it comes to this, stupid is my middle name.

Thanks, issue solved.

---

### Post by Miljet on 2008-06-17
Not knowing something doesn't make one stupid; being unwilling to learn is stupid. We were all beginners at one time. That's what these good folks on this forum are for - to help us over the rough spots.

---

