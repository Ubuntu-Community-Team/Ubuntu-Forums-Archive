---
title: "Customizing boot up messages"
date: 2009-07-11
forum: Programming Talk
---

### Post by p0cky84 on 2009-07-11
I don't know where to post this.

But, is there a way to customize the boot up messages?
Such as ```
 
 *  Setting up blah                          [OK]
 *  Setting up cheese noddles                [FAIL]
```And so on..
I would be able to insert something like ```
\033[31m[FAIL]\033[0m
```(Which would output red letters.)
And/Or ```
\033[32mOK\033[0m
``` (outputs green letters)
Seeing how it's a open-source OS, I should be able to do this, but do I have to recompile the kernel?, where is the config files located?.

I'm quite sure this is possible, seeing how they've done it in Archlinux.(?)


Again; I'm sorry if this should be posted somewhere else, and/or if there's any error in what I've just said/typed.



UPDATE/EDIT: I have managed to get red text by editing a file in /etc/init.d/, I am getting closer to my goal.
UPDATE/EDIT(again): I have managed to customize the "* Setting up something" part, tho where to I find the "[OK]" and "[FAIL]"?

---

### Post by p0cky84 on 2009-07-11
bump

---

### Post by lavinog on 2009-07-11
you shouldn't bump a thread that is less than an hour old.

Have you looked at /lib/lsb/init-functions and /etc/lsb-base-logging.sh
Are you wanting to change the text in usplash or console?

---

