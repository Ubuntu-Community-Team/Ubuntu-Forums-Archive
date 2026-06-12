---
title: "Open wtih/in terminal command"
date: 2010-03-03
forum: Programming Talk
---

### Post by brandon88tube on 2010-03-03
I'm trying to make a command to open programs in a terminal window. A good example would be my mplayer. I have the nogui version so when I play something that has no video without using a terminal, I have no control and it just plays in the background until I kill it or it finishes. All I want to do is have a right click command or something to open the program in a terminal window so I can have control.

---

### Post by geirha on 2010-03-04
Here's how you can open a new gnome-terminal running mplayer with two video files. The terminal will close when the command finishes, that's why I added the read at the end. It'll wait for a line of input before closing.
```

gnome-terminal -x bash -c 'mplayer "$@"; read' _ /path/to/video1 /path/to/video2 #...

```

---

### Post by brandon88tube on 2010-03-04
Sorry, you kind of lost me towards the end of the code. I don't understand what you mean by it will close. Also, is this going to open up the file I right-clicked on or do I have to manually type in the file name? I've been using linux for a couple years and still lack a lot of the actual command line knowledge.(*Just learned the other day that I could finally do away with multiple terminal windows by using the "&" after the command. I feel like a moron.)

---

