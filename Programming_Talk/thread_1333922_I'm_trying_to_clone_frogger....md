---
title: "I'm trying to clone frogger..."
date: 2009-11-21
forum: Programming Talk
---

### Post by Yes on 2009-11-21
I'm cloning Frogger, with ncurses.  How would I have everything like the traffic move at a constant rate, while still being able to move the frog all the time.  I run everything from one loop, so should I just get the time when the loop starts, and then have another loop at the end that iterates until the current time minus the start time is half a second or something?  

The problem then is that the user would have to time their keystrokes rather perfectly or they would be missed.  How is that normally done?

Thanks very much.

---

### Post by 0cton on 2009-11-22
try making a thread that listens to user input.

---

### Post by Yes on 2009-11-22
Is there any website that's particularly good at explaining those?

Should I use a thread for user input, or for the traffic?

---

