---
title: "openSSH problems"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by MrKitty871 on 2011-12-22
hey, i'm completely new so bare with me
i just recently installed Ubuntu server on my old laptop and ive installed openSSH on it already and i have the part working where you type the 192.168.ect and connect on putty or any other openssh thing. ive got that part down. but i want to get it to where i can connect from anywhere in the world essentially. any suggestions? :)

---

### Post by Lars Noodén on 2011-12-22
Having a server on an old laptop is kind of clever since the batter acts a built-in UPS. 

To connect from the outside world you have to have the right port (22)  forwarded on your router or switch.  What model do you have?

---

### Post by MrKitty871 on 2011-12-22
model? and i have 22 port forwarded already

---

### Post by CharlesA on 2011-12-22
Model of router.

If you already have that port forwarded and cannot connect from outside, it could be that your ISP blocks port 22.

You can use something like canyouseeme.org to check to see if it's accessible from the internet.

---

### Post by mindb0ggler on 2011-12-22
You will need to use port forwarding on port 22 from your router to your server. After you have done that, just connect using your external ip address. If you don't understand port forwarding, I would recommend reading this: [http://portforward.com/help/portforwarding.htm](http://portforward.com/help/portforwarding.htm)

---

### Post by MrKitty871 on 2011-12-22
it says success so the port is forwarded, but am i supposed to use my ip address to connect? and if i have a dns am i supposed to use that?

---

### Post by CharlesA on 2011-12-22
> **MrKitty871 said:**
> it says success so the port is forwarded, but am i supposed to use my ip address to connect? and if i have a dns am i supposed to use that?
If you are using a dynamic IP (most are), you can look into a dynamic dns server such as noip or dyndns.

---

### Post by MrKitty871 on 2011-12-22
i already have one, im saying is that what i need to connect to the server or what?

---

### Post by CharlesA on 2011-12-22
> **MrKitty871 said:**
> i already have one, im saying is that what i need to connect to the server or what?
What do you mean? You'd just have to connect to the domain name you have pointing to your ip address.

For example, you can connect using user@example.org or user@123.123.123.132

---

### Post by MrKitty871 on 2011-12-22
thank you, thats what i needed to know. but one final question. how to i figure out my ip address on the server itself?

---

### Post by CharlesA on 2011-12-22
You'd use your public ip address to connect from outside the local network and the priviate ip address (192.168.x.y/10.x.y.z) to connect from internally.

You just use dns to not have to remember your ip. :)

---

### Post by MrKitty871 on 2011-12-22
so when you download openssh all this should be done for me already and all i need to do is connect? besides the dns of course

---

### Post by CharlesA on 2011-12-22
> **MrKitty871 said:**
> so when you download openssh all this should be done for me already and all i need to do is connect? besides the dns of course
Yes. Just make sure it is secured if it can be accessed from the internet.

---

### Post by MrKitty871 on 2011-12-22
nvm, i got it working. thank you everyone for all your help

---

