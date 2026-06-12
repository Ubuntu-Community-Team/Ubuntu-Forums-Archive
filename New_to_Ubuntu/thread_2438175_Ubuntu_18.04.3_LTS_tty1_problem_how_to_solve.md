---
title: "Ubuntu 18.04.3 LTS tty1 problem how to solve"
date: 2020-03-06
forum: New to Ubuntu
---

### Post by vaya2 on 2020-03-06
i got this problem since i install Jupiter Note,  something problem with packages so i add** MATPLOTLIB**.
many step i was trying but alway fail.
some recomend i have to do
**[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]sudo apt-get purge python3.6 [/FONT]**[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]then i follow that instruction

since that i lost my unbuntu desktop, how to fix this. but i dont wanna loss my data et all.

i tried used 
**sudo apt-get ubuntu-desktop** but got problem 

its look like that i have to install many things ( firefox,gnome,ibus etc)

anyone could help me?

[/FONT]

---

### Post by deadflowr on 2020-03-07
> i tried used
sudo apt-get ubuntu-desktop but got problem

its look like that i have to install many things ( firefox,gnome,ibus etc)

anyone could help me?
Let it do as it does.

Removing python3.6 removes a ton of stuff required for the desktop.
Not sure who or why anyone would recommend it's removal. 

You can cut down some on what will be installed by adding the --no-install-recommends option to the command like
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

---

### Post by mörgæs on 2020-03-07
Here you have a good example of why not to install 18.04 or other kind of outdated software: It takes a lot of tweaking to be brought to a useable state.

If you do a clean install of 19.10 you will get Python 3.7.5 by default. Plug and play.

---

### Post by DuckHook on 2020-03-07
This is where I must disagree with friend mörgæs:

Aside from the odd non-LTS VM that I keep for curiosity and experimentation, I stick to LTS releases exclusively and find life to be far more enjoyable and less stressful as a result. Yes, the software and apps won't be cutting-edge, but the increased stability and enhanced dependability are far more important to me. It's a given that the standard releases have younger body parts. That's the whole point in being a standard release. But they also have more bugs, are less stable and require their own often arcane tweakings to work around issues and unnecessary frustrations. But instead of going through this pain only every two years, it must be done every six months.

Perhaps it's better to say that the two sorts of releases have their own advantages and drawbacks. LTS are best for people who have no new HW or SW requirements and value stability over the latest and greatest. Standard releases are best for those who have bleeding-edge HW or must use SW that require newer bins and libs. As is true of many things in life, there's no such thing as the "best" in this case because the choice of release is far more dependent on the circumstances of the user than it is on any inherent properties in the releases.

---

### Post by him610 on 2020-03-07
> why not to install 18.04 or other kind of outdated software
I assumed the '18.04' was a typing mistake.

---

### Post by mörgæs on 2020-03-07
Though still supported it's outdated nevertheless, especially if Python is important. 

I suggest that original poster does a clean install of 19.10, and based upon his findings we can see whether or not it was an easier approach than 18.04.

---

