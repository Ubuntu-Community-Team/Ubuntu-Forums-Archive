---
title: "Deleted the default panel"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Carl50 on 2012-12-09
Sorry to ask such a silly question, but I managed to delete the default panel at the bottom of the screen.  I've figured out how to create a new one, but I'd like it to go back to the original.  Is there a quick "restore defaults" button somewhere?

---

### Post by debodas on 2012-12-09
What desktop are you using? Doesn't sound like unity...

There most likely is a return to default option, but I'd need to know what desktop you're using.

---

### Post by Carl50 on 2012-12-09
I don't actually know what the desktop is, it's the one that came up when I first booted up in lubuntu

---

### Post by debodas on 2012-12-09
Ah ok, if its Lubuntu it will be LXDE.

Open up the terminal (Crl + Alt + t) and type ```
mv ~/.config/lxpanel/Lubuntu/panels/panel ~/
``` into the terminal and hit enter.

Once that has finished running, type ```
lxpanelctl restart
``` into the terminal and hit enter.

This should reset your panels back to default.

---

### Post by Carl50 on 2012-12-09
I copied and pasted that first command into the terminal and it said "No such file or directory"

Am I doing this wrong?

---

### Post by debodas on 2012-12-10
Nope, you were fine, it was my bad. Really should have coffee **before** posting ;)

Try typing just the second line of code into the terminal and pressing enter. Reboot, has this fixed it?

If not don't worry, there is another way, its just a bit more complicated so we'll only use it if the first way doesn't work.

---

### Post by kalehrl on 2012-12-10
You need to be user, not root when executing the above commands.

---

### Post by Carl50 on 2012-12-10
Hmmm, still not working as expected.   I'm pretty sure I'm entering it as a user.  How do you know if you're root?  Doesn't it say so on your terminal command line?

Sorry I'm asking so many questions, I'm a bit timid about entering commands as I'm pretty ignorant of linux.

---

### Post by kalehrl on 2012-12-10
This is being logged in as user.
```
**kalehrl**@eeepc:~$
```
If you type 'sudo su' you will become root:
```
**root**@eeepc:/home/kalehrl#
```

---

