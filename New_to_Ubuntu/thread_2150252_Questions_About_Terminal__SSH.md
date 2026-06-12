---
title: "Questions About Terminal / SSH"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by Lieske on 2013-05-31
If a connect to another computer via ssh on terminal, am I effectively using that os in terminal?


Right now I'm connected to a user account on a Scientific Ubuntu computer through ssh. I'm attempting to install OpenCV. Is that something I can do? By accessing terminal, do I have access to all the functions available on that computer, like installing new software?

---

### Post by r-senior on 2013-05-31
Yes. It is as though you had opened a terminal session while sitting at the other computer. Note that if you run any commands that attempt to display a new window, that window would by default appear on the remote machine, not the one you connected from.

---

### Post by Cheesemill on 2013-05-31
Also bear in mind that your user account on the remote machine might not have the privileges that you need to install software, you should check with the server admin to make sure.

---

### Post by Lieske on 2013-05-31
Thank you for your quick response! I was having trouble understanding exactly what was going on when I ssh. I'm having some unexpected errors installing the software so I thought I was trying to do more than I could over ssh.

---

### Post by Lars Noodén on 2013-05-31
You can do anything (that you have privileges to do) on the remote machine using ssh that you can locally.  Depending on what you are working on and how you work, you might be interested in using tmux (or screen) to keep your remote session between logins.  

At the most primitive you can start a new session on the remote machine after logging in with ssh, 

```

tmux

```

then after working a bit, you can detach ctrl-b,d and then log out.  Later you can log in again with ssh and reattach to that active session.

```

tmux a

```

That will bring up your old session exactly as you left it.  It's useful when you have to interrupt your work, but has thousands of other uses.

---

