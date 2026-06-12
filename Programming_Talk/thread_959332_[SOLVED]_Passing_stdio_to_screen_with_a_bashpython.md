---
title: "[SOLVED] Passing stdio to screen with a bash/python script"
date: 2008-10-26
forum: Programming Talk
---

### Post by durand on 2008-10-26
I'm trying to wrap shellfm (a console last.fm player) around a python or bash script so that I can start it from cairo-dock by just typing in an artist. I'd then like to control it somehow so I thought of using screen and then just run screen -r when I want to do something. That method works fine except that I would prefer to just run a single command rather than having to connect to the screen session, then typing something.

I tried something like **screen -S shellfm -X "l"** to send l to shellfm but it just says unknown command in screen. I think its trying to execute it rather than send it to standard input. So, any suggestions? If it is possible to do it without screen, that would also be cool!

Thanks

---

### Post by geirha on 2008-10-26
```
screen -S shellfm shellfm
```

The -S option expects the next argument to be a title for the screen.

---

### Post by durand on 2008-10-27
Yes, shellfm is the title. I don't want to execute shell-fm again, I just need to input something into the already running shell-fm.

---

### Post by geirha on 2008-10-27
I think your approaching this the wrong way. From a little googling it seems shell-fm has its own interface for remote controlling. Try starting it with "shell-fm -i localhost" then try giving it commands with for example telnet. ```
echo pause |telnet localhost 54311
```

---

### Post by durand on 2008-10-27
Oh, I didn't know that! Thank you so much!

---

### Post by geirha on 2008-10-27
BTW, for a list of accepted commands, see the man-page of shell-fm-config ```
man shell-fm-config
```

---

### Post by durand on 2008-10-27
Hmm, that doesn't work. Where are you getting all this from anyway? I couldn't find any information with google.

EDIT: Its in ****man shell-fm

---

### Post by geirha on 2008-10-27
I looked at the shell-fm package from the Hardy repositories. It has two man-pages (shell-fm(1) and shell-fm-config(5)). The latest source for shell-fm has both the man-pages in one (shell-fm(1)) though.

---

### Post by durand on 2008-10-27
Oh ok...Thanks again :)

---

