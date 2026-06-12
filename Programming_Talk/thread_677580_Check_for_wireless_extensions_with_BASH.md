---
title: "Check for wireless extensions with BASH?"
date: 2008-01-24
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-01-24
I am writing a script that auto-configures a wpa_supplicant setup for the open_alg MSCHAPV2 wireless security that's set up at the school I go to/live at.

It would be really helpful to be able to detect which interfaces have wireless extensions. I know typing:

```
iwconfig
```

brings up the list of interfaces and which ones have wireless extensions.Is their a way to integrate this into a BASH script that would give me the name of which interface has the wireless extension?

Thanks!

---

### Post by Cappy on 2008-01-25
```
iwconfig 2> /dev/null | grep -o '^[^ ]*'
```
will do this, I think.

The non-wireless interfaces are output on sterror and must be redirected to /dev/null.

---

### Post by oodlesOfmoodles on 2008-01-25
Hey thanks!

Can you possible explain what the command does? That would be great!

Thanks again!

---

### Post by Cappy on 2008-01-25
```
2> /dev/null
```
redirects the errors such as
```
lo        no wireless extensions.

wifi0     no wireless extensions.

eth0      no wireless extensions.
```
to /dev/null (throws it away).

grep -o gives only the parts that match (not the whole line).

```
^[^ ]*
```
^ means at the beginning of the line (I accidently left this out but it should be there just in case)
[^ ] means any character but a space
* = any number of times

Put together it means take the non-error output and extract the first word from any line where the first character is not a space.

---

### Post by oodlesOfmoodles on 2008-01-25
Thank you so much for your help. Its working perfectly!
Also, thanks for taking the time to respond and explain it.

Thanks!

---

