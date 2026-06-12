---
title: "[Shell] head command help."
date: 2010-07-05
forum: Programming Talk
---

### Post by xOrphenochx on 2010-07-05
Hello,

Bit stuck here, I have a script I'm trying to write, but I can't find the cleanest way to keep this not hardcoded.

I have this command, which I need to keep the "" off because its part of a larger command related to dialog. What I need is for head to do 1-x for how many times there are lines in a file. I already have used wc -l for this, but I cannot think of a way to get head to do what I want.

```
$(cat /tmp/temp.alldsks | head -1 | tail -1) "" off
```

Right now the whole command looks like this, to create a selection list.

```
		dialog --checklist "Choose Disks:" 15 40 5 \
		$(cat /tmp/temp.alldsks | head -1 | tail -1) "" off \
		$(cat /tmp/temp.alldsks | head -2 | tail -1) "" off \
		$(cat /tmp/temp.alldsks | head -3 | tail -1) "" off \
		$(cat /tmp/temp.alldsks | head -4 | tail -1) "" off  2> /tmp/temp.dsks
```

---

### Post by d3v1150m471c on 2010-07-05
no one can get head to do what they want...it's why we have buddhism...

what is it exactly the script is for and what you need it to do? there may be another way around this altogether.

---

