---
title: "Ffox always in foreground!"
date: 2016-06-12
forum: New to Ubuntu
---

### Post by Citta on 2016-06-12
Hi, 

I adjusted Ff to do this-unfortunately I forgot how I did it, intending to undoe that. Because, e. g. starting the terminal, I have to minimize Ff, then I can use the terminal. 
Thanks for your hints!

---

### Post by yetimon_64 on 2016-06-12
> **Citta said:**
> Hi, 

I adjusted Ff to do this-unfortunately I forgot how I did it, intending to undoe that. Because, e. g. starting the terminal, I have to minimize Ff, then I can use the terminal. 
Thanks for your hints!

Did you use the program devilspie or gdevilspie to set that by any chance ? That is what I use here for such tweaks.

---

### Post by Frogs Hair on 2016-06-12
Being that there are different was to go about having a window always on top more information might help . Did you use a terminal command, startup applications command, or some other method like the Compiz Configuration Settings Manager (CCSM) ?

---

### Post by Citta on 2016-06-14
No, it was so simple, without using a software. As a newbie I would not know how to do it, how to name it, how to search for it. Btw: What would be the best way to solve such questions, finding software, without knowing a name and without annoying forums? Just downloaded the Ubuntu Manual, 150 pages are awaiting for me. It was just by chance and I used it, because at that session it came in handy. Today, after starting Ubuntu again, everything seems to be back to normalcy. Should have trying that before posting here, my bad, sorry. Pity I do not know how I did it....but I will check Compiz for that purpose.

---

### Post by ckotichas on 2016-06-14
To do this, I use:
```
firefox &
```
Then I hit <ENTER> to see the shell prompt.

---

### Post by Citta on 2016-06-15
> **ckotichas said:**
> To do this, I use:
```
firefox &
```
Then I hit <ENTER> to see the shell prompt.
Understood rightly: Launch terminal, typing above mentioned code, enter? Ff now in foreground...how to undoe this? Will a reboot do it, or can you undoe it via terminal, too?

---

### Post by ckotichas on 2016-06-15
Hit <ENTER> in the terminal window. That will make the shell prompt appear. Then you can use Firefox and the terminal at the same time.

---

### Post by ckotichas on 2016-06-21
Citta, don't forget to mark this thread as "SOLVED" if your issue was resolved.

---

### Post by Impavidus on 2016-06-22
> **ckotichas said:**
> To do this, I use:
```
firefox &
```
Then I hit <ENTER> to see the shell prompt.

That is about running Firefox as a foreground or background process in the terminal. Put an & after the command and it runs in the background, and then you can use the terminal for something else, and Firefox no longer accepts input from the terminal (which it didn't do anyway). But running Firefox as a foreground or background program in the terminal is a completely different matter from making the window stay on top, which you seem to do when writing about minimising your window to get to a freshly opened terminal under your Firefox window. I don't know how to do or undo that automatically, but on Xubuntu I can open a menu when clicking on the icon on the window's title bar and in that menu I can toggle an option "Always on top". I rarely use that, as most of the time I keep my terminals and Firefox window on separate workspaces.

---

### Post by ckotichas on 2016-07-19
> **Impavidus said:**
> That is about running Firefox as a foreground or background process in the terminal. Put an & after the command and it runs in the background, and then you can use the terminal for something else, and Firefox no longer accepts input from the terminal (which it didn't do anyway). But running Firefox as a foreground or background program in the terminal is a completely different matter from making the window stay on top, which you seem to do when writing about minimising your window to get to a freshly opened terminal under your Firefox window. I don't know how to do or undo that automatically, but on Xubuntu I can open a menu when clicking on the icon on the window's title bar and in that menu I can toggle an option "Always on top". I rarely use that, as most of the time I keep my terminals and Firefox window on separate workspaces. Sorry for the necro, but I just wanted to address this.  You are correct, the issue of keeping the Firefox window on top is handled by the window manager. As such, the method varies depending on the window manager being used. Whether that answers the OP's question, I don't know because I have no idea what they are trying to say.

---

