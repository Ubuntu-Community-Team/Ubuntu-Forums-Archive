---
title: "[SOLVED] Num Lock by default"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Toegang on 2008-06-12
Hi,

Still new . . .
When Xubuntu starts the num lock is off by default. 
How do I get it ON by deafault?

Please let me know.

Toegang

---

### Post by avtolle on 2008-06-12
There is a small app in the repositories, which I think is also available under Xubuntu, named numlock or something close to that. Install it, and after your system fully loads, your num lock key will be on by default.

---

### Post by Titan8990 on 2008-06-12
Most of the time that is an option that is found in the BIOS. In my BIOS i have to hit CTRL+F1 to see the option for it.

---

### Post by hyper_ch on 2008-06-12
```

sudo apt-get install numlockx

```

---

### Post by Toegang on 2008-06-16
@Titan: 
My BIOS already says to activate num-lock . . .

@avtolle & hyper_ch: 
Thanks, just thought it didn't work. The NumLock indicator on the keyboard didn't light up, so I persumed there was something missing in the trick. But later on I descovered the num keypad is working perfectly, it's just the indicator that put the world upside down. (burning = no numlock)

Any idea how to put that one right??

---

### Post by hyper_ch on 2008-06-16
for me it's activated even if it does not light up.

---

### Post by jdarias on 2008-06-21
You just received incomplete instructions. Keep numlockx installed.

You have to edit this file:

```
sudo mousepad /etc/gdm/Init/Default
```

Then you search for a line like this:
```

exit 0
```
In my case, it's at the end of the file.

Now you add this code on top of that line:
```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
```

Must end looking like this:
```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi

exit 0
```

---

### Post by Redsandro on 2009-02-26
It's most stupid that an operating system that decides to overrule the BIOS setting doesn't come with an option to turn it on.

I always thought I just hadn't find the option yet, and it became increasingly annoying.

So thanks for this solution, I accidentally stumbled upon it. :)

---

