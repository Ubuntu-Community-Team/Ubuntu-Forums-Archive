---
title: "Using SSH to set up my VPS, how do I close the terminal without ending the process?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by noobydev on 2008-07-15
I don't know if this will make any sense to anyone but here goes..

I've managed to get my webapp working on my new VPS (Ubuntu Hardy) and I've really enjoyed working on my laptop in an Ubuntu VM.

My final command in the terminal over SSH to get my (pylons) webapp working is ```
paster serve production.ini
```

How can I close the terminal (and the VM) without my site breaking?

---

### Post by Dr Small on 2008-07-15
Either:
```
paster serve production.ini**&**
```

Or, open screen, and then run the command:
```
$ screen
$ paster serve production.ini
```

Dr Small

---

### Post by noobydev on 2008-07-15
The 1st solution didn't work for me but the 2nd one did.

Thanks for the fast reply! :)

---

### Post by bodhi.zazen on 2008-07-15
You can also :

```
nohup paster serve production.ini&
```
```
(paster serve production.ini&)
```

nohup is probably better of the two.

---

