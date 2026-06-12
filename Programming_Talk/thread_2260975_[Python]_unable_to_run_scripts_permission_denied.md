---
title: "[Python] unable to run scripts: permission denied"
date: 2015-01-15
forum: Programming Talk
---

### Post by michigogo on 2015-01-15
Hello there guys,
I was trying to run a script using the terminal:
```
michi@E6520:~$ '/home/arthur/Desktop/Python/Pygames/pygames.py' 
bash: /home/michi/Desktop/Python/Pygames/pygames.py: Permission denied

```
What's wrong? I know I'm not in the sudoers file, but I can at least do that, can't I?
Thanks,
Michi

---

### Post by $yl9pAR%t on 2015-01-15
Try this code in terminal:

```
chmod +x [COLOR=#000000][FONT=Ubuntu Mono]/home/michi/Desktop/Python/Pygames/pygames.py[/FONT][/COLOR]
```

---

### Post by michigogo on 2015-01-16
No errors pop up, but i get nothing on my screen:

```
michi@E6520:~$ chmod +x /home/michi/Desktop/Python/Pygames/pygames.py
michi@E6520:~$ 



```

---

### Post by steeldriver on 2015-01-16
All it does is mark the script as executable... having done than, are you now able to run the script?

---

### Post by michigogo on 2015-01-16
Yes it works!
Thanks so much to, you all! :D
Thanks thanks thanks!

---

