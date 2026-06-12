---
title: "How can I do this? Making a conky script to check pingtime"
date: 2009-09-17
forum: Programming Talk
---

### Post by rob86 on 2009-09-17
I'm trying to make some kind of a ping checker to use with Conky. I want to automate a ping, extract the avg time, and display it on the desktop.

I'm stuck at the extracting the information part. I can get it working in the terminal, by doing something like this:

ping -c 3 [www.SomeWebsite.com](www.SomeWebsite.com) | grep rtt | gawk -F/ {'print $6}'

This gets the average ring reply time using the terminal. I don't know how to make conky execute that. I tried using {exec } etc but it doesn't really execute the full command and gives me the entire output.

Does anyone know how to do this? I think it's relatively simple, if you know what you're doing, and I don't :)

---

### Post by pattinsonrobert on 2009-09-17
Hi Rob86.

I am also have the same problem If you find the answer then post it here.It's pleasure to be a part of your forum. I love to try also what you are discussing here. Thanks!

---

