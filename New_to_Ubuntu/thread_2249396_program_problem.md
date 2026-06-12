---
title: "program problem"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by barefootdon on 2014-10-21
I was trying to install skype to ubuntu 14.04. Now it shows I have an internal program problem. I cannot access the ubuntu software center or the updates. The program seems fine except for that. It asks to right click for package manager but I don't know where to go for that. It also says I can find the problem by going to the terminal and apt-get but I'm not sure what else to do.

---

### Post by ian-weisser on 2014-10-21
Hi!
Welcome to the forums.

Can you pleasetell us *exactly* when the error message is?
The exact wording can be a vital clue.

Can you please lead us through all the steps you did to install Skype? Did you use Software Center? The Skype website? A Terminal? More than one of those?
I know it's tedious to list all the steps, but there are a lot of possible ways to install Skype, and a lot of possible mistakes.

---

### Post by sandyd on 2014-10-21
Moved to *New to Ubuntu*

---

### Post by grahammechanical on 2014-10-21
So, you get a indicator notification in the top panel that is a red circle with a white horizontal bar across the middle. Clicking on it not only gives you that message but a few other options. Have you tried them? Or you could open a terminal and run these two commands

```
sudo apt-get update
sudo apt-get upgrade
```

Watch for error messages and post them in your thread. An error message may suggest running a certain command. Do what it says. But running those two commands may clear the red indicator from the top panel and things may be back to normal.

Regards.

---

