---
title: "Question regarding updates"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Indy452 on 2008-06-17
I totally removed evolution email client from my ubuntu because I use a different one but I have noticed that when I recieve updates I am getting certain updates for evolution. Should I be recieving evolution updates when I don't have it? 

I have been installing them anyway thinking that there must be certain parts of evolution that cannot be totally removed but I thought I would ask and find out for certain.

Thanks, Neal

---

### Post by friendofpugs on 2008-06-17
I've wondered the same thing. It's a pain to go through and uncheck what you don't want updated. Even though I don't use Evolution at all, I go ahead and install the updates, but this seems backwards to me. I know that Linux is extremely customizable, to the point of hilarity, so I'd guess that you could completely uninstall Evolution and not affect other programs, unless other programs rely on libraries or something in Evolution, but that seems screwy too. I'm curious too.

---

### Post by unutbu on 2008-06-17
Run the command below to show the status of all packages that fit the pattern evolution*:
```
COLUMNS=150 dpkg --list evolution*
```

You probably want to remove evolution-data-server and evolution-data-server-common:
```

sudo apt-get remove --purge evolution-data-server
sudo apt-get remove --purge evolution-data-server-common
```

---

### Post by Indy452 on 2008-06-17
Cool. Thanks, I removed the data server stuff.  Lets hope that helps.

Neal

---

### Post by iansane on 2008-06-18
> **unutbu said:**
> Run the command below to show the status of all packages that fit the pattern evolution*:
```
COLUMNS=150 dpkg --list evolution*
```

You probably want to remove evolution-data-server and evolution-data-server-common:
```

sudo apt-get remove --purge evolution-data-server
sudo apt-get remove --purge evolution-data-server-common
```

Not really a related question but I tried the command just to see what it does and then changed it to COLUMNS=200 and it showed more info in the column so I see that it is a width measurement.

Can you tell me what unit of measurement that is, how it relates to my screen size and resolution, and can I use that with most other commands that list info in columns?

Thanks

---

### Post by cariboo on 2008-06-18
At one point a screen that could display 80 columns X 24 rows was pretty high tech. 

When a terminal opens on your desktop it opens in 80 X 24.

---

### Post by Victormd on 2008-06-18
> **iansane said:**
> Not really a related question but I tried the command just to see what it does and then changed it to COLUMNS=200 and it showed more info in the column so I see that it is a width measurement.

Can you tell me what unit of measurement that is, how it relates to my screen size and resolution, and can I use that with most other commands that list info in columns?

Thanks

This is a character count, i.e., display 150 characters (including spaces).

If you maximize your terminal window, you'll see how this relates to your particular resolution based on your font size. I'm not aware of a direct relation between character and screen resolution. Different font sizes yield different relations. I guess we could "stretch it" and try to relate to the default 96dpi but I don't really know how... :D
+ I'm too sleepy and just talking gibberish at this point... hehehe

---

### Post by iansane on 2008-06-18
80 x 24 what? pixels, inches, centimeters? LOL Sorry I'm clueless when it comes to resolution and display properties. All I know is 1280 x 1024 looks good to me.

---

### Post by iansane on 2008-06-18
Ah, Thanks Victormd. That makes since. I guess if I'd looked at it long enough and thought about it, I would have figured it out sooner or later.

---

### Post by Victormd on 2008-06-18
No problem... :)

---

### Post by kansasnoob on 2008-06-18
The updates update everything in your selected repositories.

You need not worry. Just make sure you still have the default settings in Software Sources (updates tab), which is only Important Security Updates & Recommended Updates.

Leave the rest of the stuff for the gurus, and bless them because they make Ubuntu work better for the rest of us!

---

