---
title: "Unity 14.04 + Gnome shell: login set to automatic but still requesting password"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by swarup on 2014-04-29
I have installed Ubuntu 14.04 unity, and then added the Gnome shell [using "sudo apt-get install gnome-session-flashback"]. In "User Accounts", I had from the beginning set up automatic login so as not to have to type in my password every time I boot. And when initially I had only unity installed, it was booting directly to the desktop without showing any login page or asking password.

But now that I've added the Gnome shell, even though login is set to automatic it still gives me the login page and associated requirement that I type my password-- presumably to give me the option of which shell I want at that login. But is there some way to avoid having this login page come every time I boot? Say, have it set up so it will boot automatically to the shell I used the previous time as a default. And then if a particular session I want to change it, I can push some key to make the login screen appear at boot. Otherwise it is just a pain to have to deal with the login screen every boot-- if it can be avoided somehow that would be very nice.

---

### Post by Habitual on 2014-04-29
I don't know about what Ubuntu may offer, but if slim is in your software center, you could have a look at that.

[http://askubuntu.com/questions/143844/how-do-i-install-slim-login-manager](http://askubuntu.com/questions/143844/how-do-i-install-slim-login-manager)

and in slim.conf:
default_user        yourID
...
auto_login          yes

---

### Post by swarup on 2014-04-29
Thanks very much-- I'll have a look into slim. I want to learn a bit about it, and then I'll try installing it and see how it works.

---

### Post by Habitual on 2014-04-30
You are very welcome.

---

