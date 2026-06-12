---
title: "Auto Updating Picture/File"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Noxn on 2008-10-11
Uhm... I don't know how to explain this, but i will try:
Is there any method of having a file (like a picture), that updates itself from a website every now and then? 

Or something like that.

Is this possible? and if it is, How?

---

### Post by diablo75 on 2008-10-11
I don't know how to do this exactly, but you could probably have a cron job run wget on whatever it is you're trying to sync up...

---

### Post by dhtseany on 2008-10-11
Yes, I would say there are many different methods of accomplishing what you want. If you want an image to update that is on a webpage you can use PHP to spit out a JPG, GIF, or PNG and to call data from another source and update if it changes. If you want this on your local machine then thats a bit out of my league. I'm sure you could do something like this using Ruby or something else along those lines. If I'm close to what you're looking for then you might want to ask the guys in the Programming Forums.

Peace
Sean

---

### Post by Noxn on 2008-10-11
I know i could do something like this in shell script, but i wanted to know if that could happen fully automatic.

Example: Look at the intrepid ibex counter, it changes everyday, and i want that as a picture on my desktop (as pictures are getting themselves as icons) , but i want that it updates itself like every day.

---

