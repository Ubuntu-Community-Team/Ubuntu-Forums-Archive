---
title: "EPD Enthought installation - how to?"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by wendy.willow on 2012-10-02
I'm running Ubuntu 12.04. I'm trying to install the EPD Enthought as I need it for my python course (it's recommended).

I did the following:


[LIST=1]
[*]go to the epd website and download the 32-bit .sh; epd_free-7.3-2-rh5-x86.sh
[*]install it by going to the download directory and giving command: bash epd_free-7.3-2-rh5-x86.sh
[*]agree to all the conditions
[*]choose the directory where you want to have it installed.
[*]Now the part where I'm left dry. It says:
[/LIST]
  As the last step, you should edit your .bashrc or prepend     the EPD_free install path:
      /home/*/epd_free-7.3-2-rh5-x86/bin  Thank you for installing EPD_free!   I'm suppose to export a path or something like that but I'm too afraid to do it and can't find the proper support online.
  I needn't say that I can't find Enthought by searching it through dash.
  



Help would be much appreciated.

---

### Post by sandyd on 2012-10-02
> **wendy.willow said:**
> I'm trying to install the EPD Enthought as I need it for my python course (it's recommended).

I did the following:


[LIST=1]
[*]go to the epd website and download the 32-bit .sh; epd_free-7.3-2-rh5-x86.sh
[*]install it by going to the download directory and giving command: bash epd_free-7.3-2-rh5-x86.sh
[*]agree to all the conditions
[*]choose the directory where you want to have it installed.
[*]Now the part where I'm left dry. It says:
[/LIST]
  As the last step, you should edit your .bashrc or prepend     the EPD_free install path:
      /home/*/epd_free-7.3-2-rh5-x86/bin  Thank you for installing EPD_free!   I'm suppose to export a path or something like that but I'm too afraid to do it and can't find the proper support online.
  I needn't say that I can't find Enthought by searching it through dash.
  



Help would be much appreciated.
You can temperirorily set it with (replacing *username* with your username)
```

PATH=$PATH:/home/_username_/epd_free-7.3-2-rh5-x86/bin

```

---

### Post by wendy.willow on 2012-10-02
> **sandyd said:**
> You can temperirorily set it with (replacing *username* with your username)
```

PATH=$PATH:/home/_username_/epd_free-7.3-2-rh5-x86/bin

```

Even if I do this, I still don't know how to run it.

Typing 'epd', 'Enthought', 'enthought' gives nothing.  Searching in dash - again, nothing.

Also, I would rather set it permanently, which file do I need to append it to?

EDIT: I'm running Ubuntu 12.04

---

### Post by sandyd on 2012-10-02
add it to .bashrc
```

nano ~/.bashrc

```

---

### Post by wendy.willow on 2012-10-02
> **sandyd said:**
> add it to .bashrc
```

nano ~/.bashrc

```


It worked, it seems that Idle is the python editor in this package.

Thank you very much for your help.

---

