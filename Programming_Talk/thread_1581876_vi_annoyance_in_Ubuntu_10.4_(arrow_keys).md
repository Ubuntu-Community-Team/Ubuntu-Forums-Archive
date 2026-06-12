---
title: "vi annoyance in Ubuntu 10.4 (arrow keys)"
date: 2010-09-25
forum: Programming Talk
---

### Post by bertszoghy on 2010-09-25
Hello,

I have been scripting on SuSE and on Dapper for about 5 years. I just started with Ubuntu 10.4 both at work and at home this week.

vi is giving me a bit of trouble

When I open a file, arrow down to a line I want to edit, hit "i" to insert, add something, avi .bashnd hit the arrow key down to hit the next line, it adds a character instead of what I am expecting.

Is there a way to fix this behavior?

I have the same problem at work and at home, different keyboards, so I figure I have a flavor of vim I don't like.

Thanks in advance,
Bertrand

---

### Post by Bachstelze on 2010-09-25
That's normal vi behaviour. If you want the arrow keys to move in the file, use vim.

---

### Post by bertszoghy on 2010-09-25
Fine by me!

What package do I need to apt-get remove and apt get install, please?

B

---

### Post by Bachstelze on 2010-09-25
```
sudo apt-get install vim
```

---

### Post by bertszoghy on 2010-09-25
Yes indeed!

I had to add the line :

syntax off

in file .vimrc

and now the joy has returned.

Thank you!

---

