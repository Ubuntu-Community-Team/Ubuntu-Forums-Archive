---
title: "Pop-ups and OpenVPN"
date: 2022-02-20
forum: New to Ubuntu
---

### Post by eltirobert on 2022-02-20
I recently installed Ubuntu 22 and found that when I typed commands in terminal, sometimes other windows (such as software updates) would pop up. How do I fix this problem?

Second, I tried to install OpenVPN access server; it didn't work and read "Error: unable to locate package openvpn-as". Why is this?

---

### Post by pantazi on 2022-02-21
Ubuntu 22.04 isn't released until April 21st 2022. How come you've got it?

---

### Post by SeijiSensei on 2022-02-21
The pre-release version of 22.04 has been available for weeks now. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

On the first question, if you enter a command at the terminal to run a graphical program, then that program will appear in its own window. That's how things are supposed to work. Then you need to the mouse into the program's window to do anything there just like you would if you launched it from the menu.

You can launch a program from the terminal and have it run in the background so the terminal prompt will be available again. Try, for instance,

```
firefox
```

and

```
firefox &
```

The ampersand "&" puts the application into the background.

What purpose do you intend to use OpenVPN for? If there's not a compatible version yet available for 22.04, you just need to wait awhile or revert to 20.04.  In general, don't install software from other sites; rely on the package manager that came with your distribution.

What if you type
```
sudo apt update
sudo apt install openvpn

```

---

### Post by ActionParsnip on 2022-02-21
You don't need to download anything from the OpenVPN website. OpenVPN is in the repositories. You can install it with the commands given by SeijiSensei. This isn't Windows which has users scurrying all over the internet to install basic functionality. It's all in one place and easy to use.

---

### Post by pantazi on 2022-02-21
> **SeijiSensei said:**
> The pre-release version of 22.04 has been available for weeks now. [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)



Ok thanks.

---

### Post by eltirobert on 2022-02-22
Ok, makes sense.

---

