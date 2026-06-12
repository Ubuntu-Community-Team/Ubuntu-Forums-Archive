---
title: "Pidgin HELP"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by rfsquared on 2008-05-03
So I tried to post this in the Beginner Team sticky but something went wrong I think...anyway...

So yeah...I'm such a noob it's not even funny. I downloaded Ubuntu about 3 days ago and so far everything's been going really well.

However...the one thing I CANNOT get for some reason is IM. I downloaded the source for Pidgin and read the directions and still can't understand what it wants me to do.

But then today I figured out that I think Pidgin is installed on my computer. It opened once when I was in terminal and, desperate for any help, just typed "pidgin" into the prompt. The software popped up, I put in my AIM info and as soon as my buddy list loaded, the program shut down. It now appears in my Internet folder of Applications, but when you click on it the bar at the bottom pops up "Starting Pidgin" but then it closes.

So what do I need to do to get Pidgin to work?

---

### Post by Cresho on 2008-05-03
ill keep watch of this.

open terminal and type pidgin, hit enter and post what it outputs here.

---

### Post by tamoneya on 2008-05-03
type the following into terminal and then test it again by going into applications -> internet -> pidgin
```
sudo apt-get remove --purge pidgin
sudo apt-get update
sudo apt-get install pidgin
```
Answer yes to all the prompts in terminal

---

### Post by rfsquared on 2008-05-03
nevermind...it just started working correctly when i rebooted...

And it doesn't SAY anything when you type "pidgin," it just starts the program if it's not running and then gives you another prompt

---

