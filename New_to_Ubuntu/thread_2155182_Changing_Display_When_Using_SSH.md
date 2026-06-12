---
title: "Changing Display When Using SSH"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by Lieske on 2013-06-17
I'm connected to another computer via ssh currently. I need to set the windows to pop up on my current, local machine and not the computer that I'm connected to. How can I do this?

---

### Post by Cheesemill on 2013-06-17
Use the -X switch when connecting to the remote machine...
```
ssh -X user@host
```

---

### Post by Lieske on 2013-06-17
I tried using -X but whenever I try to display an image I get this error:

```
 display: unable to open X server ` @ display.c/DisplayImageCommand/420.
```

---

### Post by HermanAB on 2013-06-17
You have to run Xorg on the local machine, before you you run ssh.

---

### Post by Lieske on 2013-06-17
Do you have any resources on how to install / run Xorg? I am having dificulty finding a guide.

---

