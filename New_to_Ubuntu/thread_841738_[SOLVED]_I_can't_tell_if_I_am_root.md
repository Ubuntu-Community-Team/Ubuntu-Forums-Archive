---
title: "[SOLVED] I can't tell if I am root"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by go_lanche on 2008-06-26
This is pretty embarrassing to have to ask, but I can't tell if I am root. I had no idea what I was doing when I first installed Ubuntu and now I can't remember what I did.
The user switcher only lists me.  I have used   ```
cat /etc/passwd |grep "/home" |cut -d: -f1 
``` and it doesn't list root, but I have to give my own password to do things like sudo and synaptic. Thanks for the help.

---

### Post by PinkFloyd102489 on 2008-06-26
It means root doesnt have a password and it's never listed in the user accounts.

Do:
```
sudo -s
```

Enter your password and you'll be come root.

---

### Post by rburkartjo on 2008-06-26
go open terminal and type sudo -i it will ask for a password try typing in the password you nomally use. see if this works. if not you will have to type in a root password. here is a link for help
[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)
/cheesemaker

---

### Post by brian_p on 2008-06-26
> **go_lanche said:**
> This is pretty embarrassing to have to ask, but I can't tell if I am root.

```
whoami
```

---

### Post by bodhi.zazen on 2008-06-26
> **brian_p said:**
> ```
whoami
```

id

(less typing)

@go_lanche Ubuntu uses sudo and gksu. Use your user password.

[uhelp]community/RootSudo[/uhelp]

@PinkFloyd102489

```
sudo **-i**
```:twisted:

---

### Post by PinkFloyd102489 on 2008-06-26
> **bodhi.zazen said:**
> id

(less typing)

@go_lanche Ubuntu uses sudo and gksu. Use your user password.

[uhelp]community/RootSudo[/uhelp]

@PinkFloyd102489

```
sudo **-i**
```:twisted:


I use sudo -s. It works the same way.

---

### Post by bodhi.zazen on 2008-06-26
> **PinkFloyd102489 said:**
> I use sudo -s. It works the same way.

No it does not. -s uses your user environmental variables, -i uses root.

Try

sudo -s
echo $HOME

sudo -i
echo $HOME

-i is a tad more secure but more important, IMO, we want root to write config files to /root (for example).

---

### Post by brian_p on 2008-06-26
> **bodhi.zazen said:**
> id

(less typing)

Be fair now! You should compare like with like.

```
id -un
```

A draw.

---

### Post by go_lanche on 2008-06-27
Thanks for the help, everything worked out just fine. I tried a couple of the ideas listed here just for curiosity's sake and they were all helpful.

---

