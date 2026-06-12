---
title: "Special characters in login form NOT accepted"
date: 2020-11-17
forum: New to Ubuntu
---

### Post by gino2490 on 2020-11-17
On Ubuntu 20.04.1 lts Italian updated till today November 17 2020 in login form when I type ctrl+shift+u the system clear all characters I have written before. I can't login if my password has a special character. I have inserted and used special character in password until 20.04. Is there any other way to type special character not ctrl+shift+u?

---

### Post by Impavidus on 2020-11-18
You may be able to type special characters if they are directly supported by your keyboard, or using dead keys or the compose key.

A password with special characters isn't more secure than a password with the digits forming the Unicode code point for that character in its place. Id est, the password```
passw&#13487;rd
```isn't more secure than```
passw34afrd
```and the latter is faster to type as it doesn't need the ctrl-shift-u. (It's just a random character; I've no idea what it means.)

And neither of these examples is secure, especially since I published them here. As input of special characters may be difficult in some cases, it's best to stick to ascii for passwords. In particular for login passwords, as you have to type them before user specific input settings have been loaded. You need a few more characters for the same security, but without the special input methods it's faster to type.

---

### Post by gino2490 on 2020-11-21
Thanks a lot, my opinion  about special characters is a little different but what I want to highlight is that accounts manager accepts ctrl+shift+u in password field BUT login form doesn't. It looks like a bug. My administrator's password had password with special characters and the solution for log in is been...  reinstall! I didn't know ctrl+alt+f3 for login via terminal, maybe it works.

---

### Post by Impavidus on 2020-11-21
You're right, somewhat. It isn't very nice of the accounts manager to accept passwords that cannot be typed at the login screen, so maybe it should only accept ascii characters. Except that, if you happen to use a non-latin keyboard, it should really accept those non-latin characters.

It's a result of the modular nature of Linux. The accounts manager doesn't handle keyboard input itself; it has a separate tool for that. Whether that's a separate process or a library function doesn't matter, the important bit is that's it's opaque to the accounts manager. It doesn't really know how you type the password, using ctrl+shift+u, compose, dead keys or direct input. So it has to check whether that password can be typed using the keyboard settings used by the login screen. But then, there's more than one tool that can run the login screen, which may or may not support various forms of keyboard layout switching. And all of those tools can be freely mixed.

BTW, was it not possible to reset your password using recovery mode? Or you could try with a chroot from your live disk.

---

### Post by gino2490 on 2020-11-22
Thanks again, next time I will try with recovery mode or to login with terminal, ctrl+alt+f3 in login form.

---

