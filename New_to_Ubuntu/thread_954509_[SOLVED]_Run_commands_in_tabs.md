---
title: "[SOLVED] Run commands in tabs?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-10-21
Is it possible to runs two commands on different tabs in the terminal?

I want for example to write a script that will display two different log files using the "tail" command, but I want to run them in the same terminal on different tabs.

I have tried the --tab option but it doesn't work.

---

### Post by greg@localhost on 2008-10-21
When you say 'same terminal' - do you mean the same terminal window? Not infront of my machine at the moment but this I'm 99% sure that this is in one of the drop downs in gnome terminal - 'open tab' or something.

You could always install an alternative terminal app such as Terminator - [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

---

### Post by Archmage on 2008-10-21
If you want to use a terminal and not the gnome terinmal, I can recommend the "screen" program. Such a nice tool.

---

### Post by lovinglinux on 2008-10-21
> **greg@localhost said:**
> When you say 'same terminal' - do you mean the same terminal window?

Yes, same terminal window.

> **greg@localhost said:**
> Not infront of my machine at the moment but this I'm 99% sure that this is in one of the drop downs in gnome terminal - 'open tab' or something.

You could always install an alternative terminal app such as Terminator - [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

Thanks, I will try that.

> **Archmage said:**
> If you want to use a terminal and not the gnome terinmal, I can recommend the "screen" program. Such a nice tool.

Thanks. I looked into "man screen", but it seems a little bit complicated to me.

---

### Post by vanadium on 2008-10-21
This will be very much dependent on the graphical terminal command emulator you use. You might find what you want to do in the manual of gnome-terminal: "man gnome-terminal"

---

### Post by lovinglinux on 2008-10-21
> **vanadium said:**
> This will be very much dependent on the graphical terminal command emulator you use. You might find what you want to do in the manual of gnome-terminal: "man gnome-terminal"

I tried "man gnome-terminal" but the far as I can get is this:

```
gnome-terminal --tab --tab --execute sudo iptstate
```

This will open gnome-terminal with two tabs and launch iptstate command in the second tab. But I want to launch something else in the first tab too. How can I do it?

---

### Post by lovinglinux on 2008-10-21
Nevermind. I found in another thread.

All I have to do is:

```
gnome-terminal --tab -e "command" --tab -e "command"
```

I was doing --tab -e command without quotes.

---

### Post by stephanvaningen on 2008-10-21
What about:
 ```
gnome-terminal --tab -e /home/yourusername/scripts/script1.sh --tab -e /home/yourusername/scripts/script2.sh
```
;-)

--execute is tricky in the fact that it takes the remainder of the command line, while -e (or -command) takes only next argument, but the effect is that you would need any command to be in an external script in case the command you want to run also has arguments... I think...

---

### Post by stephanvaningen on 2008-10-21
> **lovinglinux said:**
> Nevermind. I found in another thread.

All I have to do is:

```
gnome-terminal --tab -e "command" --tab -e "command"
```

I was doing --tab -e command without quotes.

Oh sorry, did not read your last post (old page-refresh) :-/

---

### Post by lovinglinux on 2008-10-21
> **stephanvaningen said:**
> What about:
 ```
gnome-terminal --tab -e /home/yourusername/scripts/script1.sh --tab -e /home/yourusername/scripts/script2.sh
```
;-)

--execute is tricky in the fact that it takes the remainder of the command line, while -e (or -command) takes only next argument, but the effect is that you would need any command to be in an external script in case the command you want to run also has arguments... I think...

Yep. I tried "--execute" too. Now I know it takes the remainder of the command.

> **stephanvaningen said:**
> Oh sorry, did not read your last post (old page-refresh) :-/

Thanks. It would have helped a lot if I didn't figured the problem with the quotes.

---

