---
title: "Java question (CLI)"
date: 2012-06-07
forum: Programming Talk
---

### Post by Drenriza on 2012-06-07
Hey guys.

I have started to use Java for administrative purposes on Linux systems. Where i have made some monitoring tools to live tests in different scenarios.

My question is. Is it possible to split up a CLI screen, to two screens in the same window. And take two different outputs from the program and paste one output in the left side of the screen and the other output in the right side of screen?

Dunno if this is at all possible so thats why i'am asking :)

Kind regards.

---

### Post by na5h on 2012-06-07
Are we talking about terminal emulators or about an actual CLI (as in "without any GUI such as Gnome or KDE").

If you are asking about a terminal emulator, then yes...it just depends on which terminal emulator you are using. I think there is one called "Terminator" that allows screen-splitting.

---

### Post by trent.josephsen on 2012-06-07
Could you be looking for a visual diff tool like vimdiff or meld?

---

### Post by Toz on 2012-06-07
The program **screen** can do that. Look for it in the software center. It will take a bit of configuring to get the dual screen effect you are looking for (but shouldn't be too hard). An added bonus of screen is that you can detach and re-attach the sessions without interrupting the processes that are happening in each window.

---

### Post by Drenriza on 2012-06-07
> **Toz said:**
> The program **screen** can do that. Look for it in the software center. It will take a bit of configuring to get the dual screen effect you are looking for (but shouldn't be too hard). An added bonus of screen is that you can detach and re-attach the sessions without interrupting the processes that are happening in each window.

Uhmm i will try and look into that. I use screen from time to time for long program runs where i need to disconnect the laptop, but wasn't aware it could do screen splitting. But not sure i can get the result i want. 

Also thanks for the other suggestions, i will look into it more.

---

### Post by Toz on 2012-06-07
The following code in your ~/.screenrc file will create two horizontal screen panels:
```

screen -t window0 bash
screen -t window1 bash
select window0
split
focus down
select window1
focus up

```

---

