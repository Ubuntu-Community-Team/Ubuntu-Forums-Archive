---
title: "display once off message to all users on login"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by dioltas on 2008-08-12
Hey, I was just wondering if anyone could tell me how to broadcast a message to all users on my system on their next login. I've been googling it but can't find a solution.

eg after successful login message like: "Software X has now been installed"
or whatever.

I know I can use the wall command to send a message to all logged in users, but I would like the message to just come up on the user's next login, and not to be displayed on any subsequent logins.

Im using debian on the computer I want to do this, ubuntu on my normal comp, don't think that matters though... 

Thanks

---

### Post by bodhi.zazen on 2008-08-12
Put this in ~/.bashrc 

```
if [ -f "$HOME"/.msg ]; then source "$HOME"/msg; rm -f "$HOME"/.msg; fi
```

And in .msg use :

```
echo "Hi $USER, since your last login program X has been installed"
```

---

