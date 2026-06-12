---
title: "How to remove fonts-ubuntu non-free package?"
date: 2020-11-14
forum: New to Ubuntu
---

### Post by rajan222 on 2020-11-14
I wanted to uninstall `fonts-ubuntu` package.

I used  
```sudo apt remove fonts-ubuntu```,

also tried `$HOME/.local/share/fonts/` but this does not exists.
It doesnot have `fonts-ubuntu` package.

`vrms` although detects it as proprietery software. so i want to uninstall it, Help!!

---

### Post by Impavidus on 2020-11-14
The name of the package is fonts-ubuntu, so the command as you used it (without the quotation marks) should work. I don't know about vrms. The package exists for Ubuntu 18.04, 20.04 and 20.10. It seems unavailable for 16.04, of the still supported releases.

Note that there's nothing suspicious about these fonts being non-free. They were developed (or at least funded) by Canonical, the creator of Ubuntu, so they are fully compatible with Ubuntu's licensing.

---

### Post by CatKiller on 2020-11-14
[Here's](https://ubuntu.com/legal/font-licence/faq) some information on the licensing of the Ubuntu fonts, if you're interested.

---

### Post by rajan222 on 2020-11-14
Thank you , i've uninstalled. but got gui problem and slow booting.

---

### Post by Impavidus on 2020-11-15
Ubuntu font is the default font for many GUI components on Ubuntu, so if you remove it, you may have to reconfigure some things to use a different font (and it must be one that supports all the characters you need).

---

