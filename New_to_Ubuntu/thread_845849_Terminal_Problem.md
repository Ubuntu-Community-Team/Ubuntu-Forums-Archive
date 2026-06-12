---
title: "Terminal Problem"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-01
I have a terminal screenlet, and after just letting it sit there (i have it locked on desktop), it starts giving me errors such as:

```

error 3 request 158 minor 6 serial 633070
error 9 request 155 minor 4 serial 633071
error 4 request 54 minor 0 serial 633188

```

I don't really mind the errors, because they don't seem to be affecting my system any. The problem is that I can't put any commands in my terminal now. The only way for me to do commands is if i type in manually what comes defaulted in the terminal, which is:

```

ado@ado-desktop:~$ 

```

Is there anyway to fix this?

---

### Post by bab1 on 2008-07-01
what app are you running?

---

### Post by adobrakic on 2008-07-01
for the embedded terminal?

---

### Post by bab1 on 2008-07-01
No, in the terminal.  What are you monitoring?  Is this a command line terminal?

---

### Post by adobrakic on 2008-07-01
Oh, I'm not monitoring anything. The error just came up randomly. It's not really the error that's bothering me, it's the fact that 

```

ado@ado-desktop:~$

```

doesn't show up agian after the error shows. because since it doesn't show, I have to restart the terminal to have it show again so i can actally use the terminal.

---

### Post by bab1 on 2008-07-01
Ahhh, well something is running and not allowing you to have the prompt back.  The prompt is:ado@ado-desktop:~$  When you see it the command line (tty) is available.  You can open a second terminal and use the command "top" to see what the current top commands are.  You can use the command "ps -ef" or "ps aux" to see everything tyhat is running.

---

### Post by adobrakic on 2008-07-01
okay, i know exactly what you mean. :D When this happens again, i'll do what you said. 
Thanks for the help, i appreciate it.

---

### Post by bab1 on 2008-07-01
your welcome

---

