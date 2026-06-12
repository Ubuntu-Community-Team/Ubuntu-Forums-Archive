---
title: "sudo? huh sudo to you too."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by carrarin on 2008-08-26
I was just wondering how this command works.

---

### Post by mikewhatever on 2008-08-26
man sudo in terminal give a good description.

---

### Post by halitech on 2008-08-26
sudo basically tells the operating system that you want to run the command as root

ie. sudo gedit /etc/fstab

that command tells the system that you want to open gedit, have it load the file fstab which is located in the folder /etc and you want to do it as root so you can edit it and save the file.

---

### Post by Crafty Kisses on 2008-08-26
Look at this > [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by kaibob on 2008-08-26
> **Codename said:**
> Look at this > [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

This is another good read on sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by -Zeus- on 2008-08-26
> **halitech said:**
> sudo basically tells the operating system that you want to run the command as root

ie. sudo mkdir gedit /etc/fstab

that command tells the system that you want to open gedit, have it load the file fstab which is located in the folder /etc and you want to do it as root so you can edit it and save the file.
This is also useful; [http://xkcd.com/149/](http://xkcd.com/149/)

halitech: what does sudo mkdir gedit /etc/fstab do? :lolflag:

---

### Post by aysiu on 2008-08-26
> **carrarin said:**
> I was just wondering how this command works.
Think about it this way.

Do you have a bank card or ATM card with a pin code or password?

You use it to pull money from the bank machine, right?

You can't just be walking along and say "I'd like some cash now" and have it magically appear. You have to got the bank machine and insert your card. After you insert your card, you have to enter a code to authenticate. Then you can pull cash out.

Same deal with *sudo*. Think of your Home directory as what you put on your person and every other file (the system files) as money in your bank account. *sudo* is like a bank machine or ATM. It allows you to have commands affect system files after you authenticate with a password.

There's also a comic strip on the web that gives you another explanation for this. Google *sudo make me a sandwich*

---

### Post by halitech on 2008-08-26
> **-Zeus- said:**
> This is also useful; [http://xkcd.com/149/](http://xkcd.com/149/)

halitech: what does sudo mkdir gedit /etc/fstab do? :lolflag:

absolutely no idea, I read it in a thread somewhere and thought I'd be smart and post it here :lolflag:

---

### Post by mikewhatever on 2008-08-26
I think it should be <sudo gedit /etc/fstab> without mkdir. That will open fstab for editing with gedit.

---

### Post by aysiu on 2008-08-26
It really should be ```
gksudo gedit /etc/fstab
```

---

### Post by jerome1232 on 2008-08-26
and just to nit and pick since this is kubuntu it would be
```
kdesu kate /etc/fstab
```

---

### Post by halitech on 2008-08-26
d'oh, I never even noticed the mkdir was in there and I read the original post and the one that Zues posted. I've corrected my original post. I started down one path and ended on another, my bad :(

---

### Post by aysiu on 2008-08-26
> **jerome1232 said:**
> and just to nit and pick since this is kubuntu it would be
```
kdesu kate /etc/fstab
```
How right you are. My oversight.

---

