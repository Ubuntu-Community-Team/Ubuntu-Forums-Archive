---
title: "A little bash help"
date: 2008-11-07
forum: Programming Talk
---

### Post by onlyproductions on 2008-11-07
hey i need help making this small shell script

basically i have a script but i want it to initiate like a minute after i open it

---

### Post by m_duck on 2008-11-07
Add "sleep 60" (without quotes) to the beginning of the script and it should make it wait 60 seconds before continuing with the rest of the script.

---

### Post by onlyproductions on 2008-11-07
> **m_duck said:**
> Add "sleep 60" (without quotes) to the beginning of the script and it should make it wait 60 seconds before continuing with the rest of the script.

thanks didnt know it was that easy
but what if i wanted it to apply to only a spiecific part of the script

---

### Post by m_duck on 2008-11-07
I'm unsure in that case as I'm not overly clued up on bash scripts. I hope someone else can give you an answer :)

---

### Post by Sorivenul on 2008-11-08
An example for you:
```

# First part of script
xterm &
xterm -e vim &

# Second part of script
sleep 60 && firefox &
```

---

