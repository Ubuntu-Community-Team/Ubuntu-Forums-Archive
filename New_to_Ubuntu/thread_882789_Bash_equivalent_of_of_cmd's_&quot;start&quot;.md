---
title: "Bash equivalent of of cmd's &quot;start&quot;"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by CrookedKarma on 2008-08-07
Is there an equivalent in bash of the "start" command in windows cmd (i.e. a command that will start a program in a new terminal window)?

---

### Post by meindian523 on 2008-08-07
You can send a task to the background by ```
<command> &
```,command is usually the name of the app you want to run.

---

### Post by CrookedKarma on 2008-08-07
What is the number that is printed when you use "&" at the end?
(upon last attempt:
"[2] 10976"
However, that doesn't open it in a new window.
Basically, I have a script which needs to call three other scripts, which will all be in while(true) loops, and I want them to be running in seperate windows.

---

### Post by Aetherius on 2008-08-07
```
gnome-terminal -x <command to run in new terminal>
```

that'll do it if you're using gnome-terminal :)

oh btw if in doubt MAN

```
man gnome-terminal
```

regards,

Aeth

---

### Post by jerome1232 on 2008-08-07
Well this depends on what terminal emulator you are using, for my example I'm using gnome-terminal, others may differ.

check out the man page of your favorite terminal to see the options

```
gnome-terminal -x <script>
```

edit: beaten to it lol oh well I'll leave my double post

---

### Post by meindian523 on 2008-08-07
> **CrookedKarma said:**
> What is the number that is printed when you use "&" at the end?
(upon last attempt:
"[2] 10976"
However, that doesn't open it in a new window.
Basically, I have a script which needs to call three other scripts, which will all be in while(true) loops, and I want them to be running in seperate windows.
I believe that's the PID.

---

### Post by NoFearDJB on 2008-08-07
> **meindian523 said:**
> I believe that's the PID.

ya, that's the PID (process ID, afaik)

---

### Post by CrookedKarma on 2008-08-07
Thanks Guys! That's perfect!
It's gonna be running on Konsole, but it's essentially the same.

---

### Post by bodhi.zazen on 2008-08-07
If you run a command in the back ground, and close the terminal, the command will stop.

The solution is to use an application called screen or nohup

nohup command &

Also see man bash re job control

[http://gd.tuwien.ac.at/linuxcommand.org/lts0080.html](http://gd.tuwien.ac.at/linuxcommand.org/lts0080.html)

---

### Post by tnt2br on 2009-09-30
Thanks [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

  Your post help me.:P

---

### Post by bodhi.zazen on 2009-10-01
You are most welcome.

---

