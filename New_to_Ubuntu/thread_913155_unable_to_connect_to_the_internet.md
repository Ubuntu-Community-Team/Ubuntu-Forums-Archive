---
title: "unable to connect to the internet"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by edward73 on 2008-09-07
I've tried everything I can find and I still can't connect to the internet using my wired ethernet westell dsl modem. My laptop wireless connected thru it with no problem.
What am I not doing right? Help!

---

### Post by kjohansen on 2008-09-07
It probably means that the driver for your wired connection didnt get installed or isnt compatible. Post the output of

```

lspci

```

---

### Post by sanemanmad on 2008-09-07
Hi edward73~

Please post more information.

Is this a wireless router/modem combo? Are you connecting via ethernet? If so please drop to a terminal

[COLOR="Red"]Applications > Accessories > Terminal [/COLOR]

and type

*ifconfig eth0* post these results.

---

### Post by edward73 on 2008-09-07
How do I do that - I'm completely confused.

---

### Post by eggdeng on 2008-09-07
Go to Applications -> Accessories -> Terminal. Copy and paste
```
lspci
``` into the terminal window & hit Intro. Select the output and paste it into your reply. 
Repeat for
```
ifconfig
```
Welcome to Linux. :cool:

---

