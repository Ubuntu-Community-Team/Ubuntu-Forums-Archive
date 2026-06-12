---
title: "windows works but my ubuntu doesnt :("
date: 2008-08-31
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-31
i am staying in my sisters dorm and theres no wireless, so i plud into the wall and it can connect (never gets the network ip or something) even if i use the plug that works perfectly when she plugs it into her laptop! (i checked theres no security on the wired connections) whats up???

---

### Post by original_jamingrit on 2008-08-31
That might mean you need to disable ipv6.  check this howto for more info: [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)
**IMPORTANT**: if you're unfamiliar with the 'vi' text editor, replace 'vi' with 'gedit' in the given instructions, and proceed normally; like this:


Go to "Applications"->"Accesories"->"Terminal", a terminal window should appear.  Enter the following: 

```
sudo gedit /etc/modprobe.d/aliases
```

Find the line: ```
alias net-pf-10 ipv6
```

change to

```
alias net-pf-10 off
```

If the above change is not working you need to change the following one

```
alias net-pf-10 off ipv6
```

Save the file and reboot

Post again if this works.

---

### Post by zamadatix on 2008-08-31
the auto thing said ip4 so i dont think its that

---

### Post by original_jamingrit on 2008-08-31
It might be a MAC address thing, then.  Did your sister have to register her MAC address when she moved in?  One way to test is to see if an Ubuntu LiveCD on her computer will connect.

If an Ubuntu LiveCD on her computer does connect, it might mean that her network card's MAC address is permitted, while yours is not.  Which is good, since it's easy to clone her MAC address onto your machine.

---

### Post by zamadatix on 2008-08-31
nope no security and i know that my laptop works because i was able to do it at my house.

---

### Post by original_jamingrit on 2008-08-31
I'm sorry, I have to admit I'm a little stumped.  I'll check back on this trhead later

---

