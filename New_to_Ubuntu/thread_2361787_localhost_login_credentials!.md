---
title: "localhost login credentials!"
date: 2017-05-20
forum: New to Ubuntu
---

### Post by theseancronin on 2017-05-20
I've just started practicing Spring boot but having trouble running localhost in the browser, as it's asking me for a user name and password, but can't for the life of me remember what they are. Well I think I have the password right but not the username. Does anyone know of how I might be able to dig these up? Is there a configuration file somewhere or command that will at least get me the username?

Thanks,

Sean.

---

### Post by JKyleOKC on 2017-05-20
Get to a terminal window, type in "echo $HOME" and press Enter. That will show the path to your home directory (if you duplicate the capitalization exactly; the terminal is case-sensitive). The final word on the line will be your username -- the home directory is always created using the user's username as its filename.

EDIT: "echo $USER" will give you just the username; better way!

---

### Post by theseancronin on 2017-05-21
> **JKyleOKC said:**
> Get to a terminal window, type in "echo $HOME" and press Enter. That will show the path to your home directory (if you duplicate the capitalization exactly; the terminal is case-sensitive). The final word on the line will be your username -- the home directory is always created using the user's username as its filename.

EDIT: "echo $USER" will give you just the username; better way!

Thanks for the reply. After doing that I still couldn't access as it still refused any password I through at it, so upon further researching, I found I had been using spring security which comes with
its own default user name and password. I just removed this dependency and it now works fine. Thanks again!

---

