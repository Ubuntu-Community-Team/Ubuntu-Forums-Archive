---
title: "How To Combine Commands in Linux"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by vokevybez on 2012-07-05
How do i combine commands like for example if i wanted to combine ```
cd /home
``` and ```
cd /media
``` consecutively. Is there a specific symbol  or something of the sort?

---

### Post by sandyd on 2012-07-05
> **vokevybez said:**
> How do i combine commands like for example if i wanted to combine ```
cd /home
``` and ```
cd /media
``` consecutively. Is there a specific symbol  or something of the sort?

There is a syntax to
a) Run commands one after the other (only if the command before it is successful)
b) Run commands all at once.

a) uses "&&"

For example,
```

cd /root && touch test && touch test2
```
That would run one command after the other

b) uses "&"

For example
```

cd /root & touch test & touch test2
```
That would run all of them at once, and would probably not be advisable.

---

### Post by vokevybez on 2012-07-05
Thanks a lot this will help with my bash tutorial :p

---

### Post by Pinoy Tux on 2012-07-06
c) Run the commands sequentially, regardless if the previous command in the chain was successful or not: use the semicolon.

```
cd /home ; ls -l ; cd /root ; ls -l
```

---

### Post by andrew.46 on 2012-07-06
Most of the information has been presented here for you but the gruesome details can be seen in the bash man pages under 'Lists'.

---

### Post by vokevybez on 2012-07-06
> **andrew.46 said:**
> Most of the information has been presented here for you but the gruesome details can be seen in the bash man pages under 'Lists'.
thank you for your input the information covered is very comprehensive

---

### Post by SeijiSensei on 2012-07-06
> **andrew.46 said:**
> Most of the information has been presented here for you but the gruesome details can be seen in the bash man pages under 'Lists'.

Real men read the man pages because they like learning about all those gruesome details!  I'll admit the bash man page is a bit overwhelming though.  The "grep" man page isn't far behind.

---

### Post by andrew.46 on 2012-07-07
Another well written man page is the 'find' page, pity they are all not as well done :).

---

