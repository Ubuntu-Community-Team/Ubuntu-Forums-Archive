---
title: "Is there a version of Remote Assistance for Hardy Heron?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-07-10
I am setting up Hardy Heron for my parents but I live several hundred miles away normally.  
Is there a version or Remote Assistance or PC Anywhere that I can setup on their machine now so that I can help them out later from home if there is a problem?

---

### Post by sydbat on 2008-07-10
I think it's built in. System > Preferences > Remote Desktop. Just enable it with a password, etc. Then you can troubleshoot from a distance.

---

### Post by Dr Small on 2008-07-10
> **sydbat said:**
> I think it's built in. System > Preferences > Remote Desktop. Just enable it with a password, etc. Then you can troubleshoot from a distance.
This is true, albeit if the connection is poor, the remote assistance will be rather sluggish.

---

### Post by jualin on 2008-07-10
> **Dr Small said:**
> This is true, albeit if the connection is poor, the remote assistance will be rather sluggish.

Yeah, the connection is very slow while using the default Remote Desktop that Ubuntu offers. Something that you can do is use RealVNC, or TightVNC, but you just have to deal with port forwarding if you use a router. Hope this helps!

---

### Post by curiousnoob on 2008-07-10
> **jualin said:**
> Yeah, the connection is very slow while using the default Remote Desktop that Ubuntu offers. Something that you can do is use RealVNC, or TightVNC, but you just have to deal with port forwarding if you use a router. Hope this helps!

Besides the speed is there any advantage of using RealVNC or TightVNC?  Also, when you say "sluggish" do you mean there is a couple second delay when moving the mouse and typing or the system as a whole?

---

### Post by dutchman72 on 2008-07-10
*VNC is a near native response, the sluggishness referred to above is in the reaction times you'll see on your end of the connection. Not on the actual machine.

I've used both remote desktop and vnc programs to and from both windows and linux boxes, adn I must say that vnc does tend to be more real-time, though there are times when RDP is the better option.

The other option is a vpn connection then use remote desktop. You'll have a secured link to begin with then a one-to-one access as if your inside their network, and in that instance RDP works very well. I use this setup from my desktop to home during the work day. And it allows a secured command shell access outside of the graphical. If thats all you'd need to resolve the trouble.

---

### Post by tjwoosta on 2008-07-10
it might be a very good idea to test all of this out from an outside connection before returning home ( you dont want to be several hundred miles away and find out you cant connect)

---

