---
title: "Uninstalling KDE"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by abennett on 2008-09-17
I am running Ubuntu 8.04 and I installed the KDE 4.0 environment. Now it boots up saying Kubuntu and a lot of my GNOME features do not work. I went to add remove programs and removed KDE 4.0 environment but I cant get my regular Ubuntu log in screen or anything to work. Please help. Thanks

---

### Post by alienexplorers on 2008-09-17
Please read this page:
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by abennett on 2008-09-17
Ran the command and it comes back and says couldn't find package manager

---

### Post by alienexplorers on 2008-09-17
Do you have synaptic, aptitude, or apt-get currently open, if so, then close them and try the command again.

---

### Post by abennett on 2008-09-17
Im super new to linux but the only thing I have open is a terminal, this website and thats it. If you could give me a way to check to see if the other things are open please let me know..

---

### Post by alienexplorers on 2008-09-17
If synaptic was running you should see it in the task bar.  As for the other two, you would need to have more than one terminal running.

---

### Post by abennett on 2008-09-17
Well.........Im wondering if anybody else can chime in here to help me with my issue

---

### Post by scip on 2008-09-17
> **alienexplorers said:**
> Please read this page:
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

Is there any other way to remove kde than by running this command? I don't need to reinstall ubuntu-desktop, as I already have it installed. I used Synaptic and marked kubuntu-desktop for complete removal, yet I still have kde and kde4 available as a session type in my login window and can still load kde4...and it didn't seem to reclaim much disk space so I think there's more to it than simply marking kubuntu-desktop for complete removal (which said 45k would be freed-not much space I would say).

---

### Post by doorknob60 on 2008-09-17
Do the command again and copy and paste he exact output so we really know whats wrong with it.

---

### Post by abennett on 2008-09-17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package manager
abennett@DellD600:~$

---

### Post by Tatty on 2008-09-17
Could you copy and paste that again, but this time include the command you are typing in what you copy from the terminal.

---

### Post by scip on 2008-09-19
A Linux-savvy coworker of mine suggested that I run:

```
apt-get remove kde-base
```

to get rid of kde. I have both kde (as in v3) and kde4 installed.

Does anyone know if that command will work without blowing up my gnome environment?

---

