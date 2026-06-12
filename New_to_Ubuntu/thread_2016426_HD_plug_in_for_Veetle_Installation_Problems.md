---
title: "HD plug in for Veetle Installation Problems"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by askkif on 2012-07-04
after i tried to install HD plug in for veetle, i restarted the computer and tried to log in to my session and  i got this message:
Could not update ICEauthority file /home/ouarzazatemaroc/.ICEauthority
i tried these commands as mentioned in some Threads
sudo chown you:you ~/.Iceauthority
chmod 0600 ~/.Iceauthority
sudo chmod 755 /etc/gconf/gconf.xml*

i tried any solved posts, nothing worked for me.
please me brothers.
tnx

---

### Post by QIII on 2012-07-04
Did you replace the word "you" with your user name?

---

### Post by askkif on 2012-07-04
no i didnt.
i just taped the way it was said, bro.

---

### Post by askkif on 2012-07-04
i tried this
sudo chown you:ouarzazatemaroc ~/.ICEauthority
invalid user
sudo chown ouarzazatemaroc:you ~/.ICEauthority
invalid group

lord have mercy
its not solved

---

### Post by QIII on 2012-07-04
Replace "you" in both cases:

```
ouarzazatemaroc:ouarzazatemaroc
```

---

### Post by askkif on 2012-07-04
i tried it as well its not solved
whts the problem now???
try to install veetle HD plug in by terminal and see what happen.
any helppppp

---

### Post by habib0016 on 2012-07-04
these problems is also for me. If you get answer of your question please inform me.

---

### Post by askkif on 2012-07-04
i will man.
why is it hard anyways?

---

### Post by robtygart on 2012-07-04
> **askkif said:**
> i will man.
why is it hard anyways?

By chance you could you please show me exactly how you type that into the terminal?

Just to be clear 

you:you = your login name to your operating system and second your computer name.

example Rob:laptop

---

### Post by askkif on 2012-07-04
ouarzazatemaroc:ouarzazatemaroc
theres no space between : and the username

---

### Post by askkif on 2012-07-04
can you please explain more?
the login name is Ourzazate Maroc

---

### Post by robtygart on 2012-07-04
> **askkif said:**
> can you please explain more?
the login name is Ourzazate Maroc

I did some searching. Have you read this? [http://askubuntu.com/questions/10543/what-does-this-startup-dialog-message-mean-could-not-update-iceauthority-file]("http://askubuntu.com/questions/10543/what-does-this-startup-dialog-message-mean-could-not-update-iceauthority-file")

---

### Post by askkif on 2012-07-05
:lolflag:):P yayyyyyyy thank you so much my problem is solved thank youuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu

---

