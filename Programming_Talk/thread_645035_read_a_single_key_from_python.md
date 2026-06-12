---
title: "read a single key from python"
date: 2007-12-19
forum: Programming Talk
---

### Post by pcit on 2007-12-19
Hi, 
I am writing an remote control program for the iRobot create in Python.
I can now send a different commands to the robot and the robot will perform  the given tasks. 

However, I would like to improve my program a little bit by reading "single key" from the keyboard. Right now, I am using the raw_input to read the command from the user, but every time I need to hit return to send the command. 

I wonder if there is a way for the user just hit a single key (ie: "f"), and python can detect the 'f' and perform certain functions without any additional enter/return key pressed.

Thanks,

Patrick

---

### Post by LaRoza on 2007-12-19
> **pcit said:**
> 

I wonder if there is a way for the user just hit a single key (ie: "f"), and python can detect the 'f' and perform certain functions without any additional enter/return key pressed.


You can use NCurses for this: [http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific)

[http://www.amk.ca/python/howto/curses/](http://www.amk.ca/python/howto/curses/)

---

### Post by ghostdog74 on 2007-12-19
see [here ]("http://pyfaq.infogami.com/how-do-i-get-a-single-keypress-at-a-time")

---

### Post by pcit on 2007-12-20
Thank you for both of you!
I forgot to mention that my application will be running under Mac, but the solution you provided work well!:lolflag:

I haven't tried to apply the curse yet, but I will look into the curse module in a few days, it seems to be a good module to know.

Thanks again!

---

