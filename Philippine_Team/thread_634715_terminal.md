---
title: "terminal"
date: 2007-12-08
forum: Philippine Team
---

### Post by phoenix072006 on 2007-12-08
how to use terminal in installing the flash player in internet... i already     
downloaded the program...:(

---

### Post by loell on 2007-12-08
you don't need to go to the **terminal/Console** to install flash player , you can go to **Applications** Menu --> **Add/Remove** 

in the **search** text box or text entry , **Type in the word flash**

In the list item will appear **Macromedia Flash Plugin ** . check it then click **Apply changes button**

or


if you would really like it to install from the terminal


just type in


```
sudo apt-get install flashplugin-nonfree 
```

---

### Post by xtrm_redbull on 2007-12-08
Installing flash plugin from add/remove or synaptic is currently not working, due to md5sum mismatch as I found out during a fresh install of xubuntu, I hope its temporary.

---

### Post by raxso on 2007-12-08
> **phoenix072006 said:**
> how to use terminal in installing the flash player in internet... i already     
downloaded the program...:(

sudo dpkg -i flash------.deb

go to the directory where you downloaded your program and issue the command.

---

### Post by .::welemski::. on 2008-02-02
Mga peps ang plugins nag firefox/mozilla kahit anong plugins ay may extension na:

**.xpt** and** .so**

If only if ang installer ay hindi nagwowork you can just copy the **.xpt** and **.so** files in their respective plugin folder.

Halibawa :

If you're using Firefox ang plugin folder nito ay nasa :
[B]
"/user/lib/firefox/plugins"[/B]

If you're using Mozilla ang plugin folder nito ay nasa :

**"/usr/lib/mozilla/plugins"**

So just put the xpt and so files in there and your good to go!

How to tell if it's working?

Just open your web browser ( gecko based ) and type the following :

"**about:plugins**" and press enter ofcourse

And scroll down untill makita nyo hinahanap nyo:

Example : "Flas","WMV","DIVX" so on and so forth ...

---

