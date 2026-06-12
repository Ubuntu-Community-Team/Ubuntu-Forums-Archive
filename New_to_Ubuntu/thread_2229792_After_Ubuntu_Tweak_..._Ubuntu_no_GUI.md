---
title: "After Ubuntu Tweak ... Ubuntu no GUI"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by czgirb on 2014-06-15
Currently, I'm using **Pangolin** on my **Compaq CQ40-328TU**
After clean-up my system with **Ubuntu Tweak**, my Ubuntu is ended with no GUI
after do some googling, i found this one ... [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) ... and after that my Ubuntu back to normal.

1. How can this happen? How can I stop thing to re-occured when I doing **Ubuntu Tweak**?

2. Or is it **Ubuntu Tweak**'s bug? How can it be fixed? If it's cannot, what a substitute that I should use?

Thank you

---

### Post by MartyBuntu on 2014-06-15
What are you selecting to "clean" with Ubuntu Tweak?

---

### Post by czgirb on 2014-06-15
> **MartyBuntu said:**
> What are you selecting to "clean" with Ubuntu Tweak?

I just click the **Janitor**'s tab (the right one) and **have all option (both LEFT and RIGHT windows' option) checked**
I do this since **Ubuntu Tweak** installed in my system, and have no problem.
But later ... it end me to **NO GUI** environment.

---

### Post by grumblebum2 on 2014-06-15
These are the options I have in Trusty.
[ATTACH=CONFIG]253970[/ATTACH]

What options do you have?

---

### Post by czgirb on 2014-06-16
> **grumblebum2 said:**
> These are the options I have in Trusty.
[ATTACH=CONFIG]253970[/ATTACH]

What options do you have?
Yup! I marked/checked all the available options

---

### Post by grumblebum2 on 2014-06-16
I have no answer why but it looks like it may be from cleaning "old kernel".
Just don't use that option.

Check what kernel your using 
```
uname -a
```
and use synaptic to remove old kernels to see if anything else is being removed.

---

### Post by czgirb on 2014-06-24
> **grumblebum2 said:**
> I have no answer why but it looks like it may be from cleaning "old kernel".
Just don't use that option.

Check what kernel your using 
```
uname -a
```
and use synaptic to remove old kernels to see if anything else is being removed.

OK! I run **ubuntu-tweak**'s **janitor** and unmarked the **old kernel**'s box ... and it's OK
***  how can I manually erase the **old kernel** if it was changed?
> uname -a
what is it? just copy-paste the command in terminal?

---

