---
title: "help with iso"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by sweeneytodd on 2008-04-23
i have gmount, i select an image, created a folder in docs as mount point, but i'm doing something wrong aren't i, cause it won't mount, if i mount to cdrom where is it, confused

---

### Post by jakev383 on 2008-04-23
> **sweeneytodd said:**
> i have gmount, i select an image, created a folder in docs as mount point, but i'm doing something wrong aren't i, cause it won't mount, if i mount to cdrom where is it, confused

What are you trying to mount? If you're trying to mount an .iso file, I only know how to do it from the command line:
```

mkdir tmpiso
sudo mount -o loop your_file.iso tmpiso

```
That's assuming you're in the same dir as the ISO image and want to mount it in a folder called "tmpiso".  When you're all done with it:
```

sudo umount tmpiso

```

---

### Post by sweeneytodd on 2008-04-23
o.k. i may be stupid but i'm in the terminal and need to go into a folder, i think this might be out of my league at the moment, i typed "dir" and surprisingly was a command, now would "goto" b right

---

### Post by aeiah on 2008-04-23
to 'change directory' do 

```
cd
```

the terminal stars off in your home folder. if your iso is in a folder called 'banana' you'd do ```
cd banana
```

if your iso is say, in another partition called 'frog' you may want to select the absolute path
```
cd /media/frog/
```

---

### Post by sweeneytodd on 2008-04-23
you legends, thank you so much for your time, i learnt some code which obviously was my first, i can now create "the machine" thanking you both again, and again, hope i can help someone else one day

---

### Post by MrWES on 2008-04-23
I used two nautilus scripts to mount and umount an iso; works great.

Here's the thread:

[http://ubuntuforums.org/showthread.php?t=87369]("http://ubuntuforums.org/showthread.php?t=87369")

---

