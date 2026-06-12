---
title: "How can we implements Firewall in .deb based OS?"
date: 2009-11-23
forum: Programming Talk
---

### Post by aditya.gnu on 2009-11-23
Hello Ubuntu Geeks,
I am trying to implement firewall,by default in one of the debian based distribution(name has to be disclosed).
I excactly want to build this facility under a live cd/dvd kind of OS, whenever I boot with a live cd.
First thing is I want to detect the NIC of my PC and then gateway and the DMZ .
How can I do it ..its urgent..Can anyone help me..? or Give me a clue.
Links or URL's are also encouraged.

Thanks n Regards,
Aditya.

---

### Post by cdenley on 2009-11-23
```

ifconfig
route -n

```

---

### Post by aditya.gnu on 2009-11-24
Well Thanks for the response , but can anybody elaborate it in a more specific manner,it'll be a great job,coz I am  a newbie to Linux.

Thanks n Regards,
Aditya.

---

### Post by Zugzwang on 2009-11-24
> **aditya.gnu said:**
> Well Thanks for the response , but can anybody elaborate it in a more specific manner,it'll be a great job,coz I am  a newbie to Linux.


So you asked the question "First thing is I want to detect the NIC of my PC and then gateway and the DMZ. How can I do it?". cdenley provided an answer containing information on how to do this on the terminal. This is the clue that you actually asked for in your first post. What precisely do you need more?

Now with regard to making a firewall out of it - If you are really a beginner with Linux, then depending on what you actually mean by "implementing a firewall", I am afraid to say that this task *might* be way too difficult for you. This is like asking for how to construct a braking system for a car when you just started learning the basics of engineering and taking driving lessons. 

For getting tasks to run at boot time of Ubuntu, you might want to have a look at the "upstart" documentation, which is the "service starting" system used by Ubuntu.

---

### Post by slavik on 2009-11-24
install ubuntu server
sudo apt-get install ufw
???
profit

---

