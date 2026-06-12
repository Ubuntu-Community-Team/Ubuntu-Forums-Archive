---
title: "My system Monitor is displaying steep jagged power uses ?!?!?!"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-05-22
My system monitor looks really wierd and it's been doing this for about the last 15 minutes. All I have is Firefox running. There's a link to a screenshot down below. Also look at my temperature reading!

[http://img259.imageshack.us/my.php?image=screenshot2oc0.png](http://img259.imageshack.us/my.php?image=screenshot2oc0.png)

---

### Post by sdennie on 2008-05-22
I'm not sure what you mean.  The screenshot you posted looks perfectly normal to me.

---

### Post by Watchtow3r on 2008-05-22
Sorry, I should have specified it. I mean look at the system monitor gauge in the top of the screen next to the Firefox logo, not the window, and also the temperature gauge in the upper right hand corner. The gauge is spiked with periods of large cpu usage quickly followed by periods of no cpu usage. I just happened to have the system monitor window open also.

---

### Post by sdennie on 2008-05-22
You should be able to figure out what is using the CPU by starting a terminal and typing top.  Wait for a while and you'll undoubtedly see what keeps spiking the CPU.  As for the temperature, I'm not sure.  Many motherboards/graphics cards report incorrect temperatures.  Based on the system monitor graph, I don't think anything is using enough CPU to cause any of the system components to reach 89C.

---

### Post by Watchtow3r on 2008-05-22
well I have the comp on a laptop cooling pad and its down to 71C. 89 was kinda the peak temp it was reading. How do I read the "top" data? I think it may be Firefox thats doing it. Is there any bug that sometimes causes Firefox to use a bunch of memory/CPU power on laptops?

---

### Post by sdennie on 2008-05-22
I'm not sure what component your temperature sensor is monitoring but, 89C is high for any component and 71 is high unless your system is under heavy load (which, it doesn't appear to be).  I give this advice often but, I would try to get some canned air and clean out every vent on your machine if temperature is an issue (I once had a laptop that had a CPU temp of nearly 100C while under heavy load and, on cleaning the vents, dropped to around 60C under heavy load).  

As for the possible firefox problem, I would check: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851).  There is a known Firefox bug that might be causing it but, I thought it was fixed a week or two ago (I don't use firefox so I'm not sure).

---

### Post by Watchtow3r on 2008-05-22
thanks I'll try both of those. BTW I don't mean to advertise here but this laptop cooling pad is working wonders! This one is made by Antec. Since I borrowed it from a friend at the beginning of this post (about 30 minutes ago), and it has got my laptop down to 55 C already. Highly recommended.

---

### Post by sdennie on 2008-05-22
Laptop coolers can sometimes be useful if you are constantly taxing the machine (like gaming all the time) but, just keeping the vents clear of dust is sufficient in most cases as long as your fans are working properly.  The rate at which your laptop vents become semi-blocked is directly related to the rate at which you clean your house.  In my case, I have to clean them about once a month to keep my machines running cool.  If you border on cleanliness, you'd probably have to do this far less frequently.

---

