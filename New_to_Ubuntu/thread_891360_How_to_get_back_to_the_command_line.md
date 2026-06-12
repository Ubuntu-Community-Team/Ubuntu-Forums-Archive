---
title: "How to get back to the command line"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-08-16
Sometimes when I open up gedit or other the command line screws up.
How to I get back to "matthew@computer:~$"?
I've tried ctrl-q but that doesn't work.

Please Help
Thanks

---

### Post by drs305 on 2008-08-16
Try CTRL-C

---

### Post by nicedude on 2008-08-16
Applications -> Accessories -> Terminal

---

### Post by Rolcol on 2008-08-16
To send the process to the background, freeze it by pressing CTRL + Z.  To send it to the background enter ```
bg
```

---

### Post by Nepherte on 2008-08-16
If you run a command with '&' at the end, you can simply continue working in the same terminal without the application messing it up:
```
gedit &
```

---

### Post by t0p on 2008-08-16
> **drs305 said:**
> Try CTRL-C

Does Ctrl-C bring back the terminal.  I know it's used to end processes in the terminal...

---

### Post by drs305 on 2008-08-16
> **t0p said:**
> Does Ctrl-C bring back the terminal.  I know it's used to end processes in the terminal...

I think what the OP wanted was how to get back to the prompt when a terminal command gets messed up or hung up. CTRL-C merely stops the process in terminal and then returns to the prompt. For instance, if you run "sudo find /" it will start listing all your files. When you realize this is going to take a while, you hit CTRL-C to stop the process and return to the command line. Sometimes  I'll be in terminal and start getting strange characters because I've hit the wrong key. Backspace won't clear them, but CTRL-C gets me back to the prompt.

Nepherte made a good point about the " &" at the end of the command. If you simply run "gedit", that terminal window is 'locked' as long as the app is running. If you hit CTRL-C, the terminal returns to the prompt but the application opened via terminal closes. 

To avoid this, run the command as "gedit &", which will allow you to continue to work in that terminal if you use CTRL-C. You can then also close the terminal window it without also shutting down the applicable program you started from that terminal.

---

