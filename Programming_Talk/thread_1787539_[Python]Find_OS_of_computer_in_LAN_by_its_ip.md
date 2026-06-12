---
title: "[Python]Find OS of computer in LAN by its ip"
date: 2011-06-21
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
hey all....i wanted to know how to obtain the OS details of a computer connected with ur computer in a LAN by a python script???

---

### Post by Beacon11 on 2011-06-21
I'd just shell out to nmap -O <ip>

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
> **Beacon11 said:**
> I'd just shell out to nmap -O <ip>
No i want python code for this by modules like socket etc..

---

### Post by Beacon11 on 2011-06-21
Ah, you got me then. nmap is the only tool I've used for that. My apologies.

---

### Post by Tony Flury on 2011-06-21
the only way you might be able to work it out is to look at which ports are open and try to make an educated guess - for instances if all the Windows Network shared ports are open - it might be a Windows O/S. nmap -A (as an option) claims to do that - by guessing - i imagine based on the ports (and responses to specific messages).

Any system which is secured in any reasonable way wont directly advertise the O/S - since that will give an attacker a number of clues.

I would also have to ask why do you want to know this ? If you own the box - you would know the O/S on it - if you don't - why does it matter what it has ?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
> **Tony Flury said:**
> the only way you might be able to work it out is to look at which ports are open and try to make an educated guess - for instances if all the Windows Network shared ports are open - it might be a Windows O/S. nmap -A (as an option) claims to do that - by guessing - i imagine based on the ports (and responses to specific messages).

Any system which is secured in any reasonable way wont directly advertise the O/S - since that will give an attacker a number of clues.

I would also have to ask why do you want to know this ? If you own the box - you would know the O/S on it - if you don't - why does it matter what it has ?
The reason i want to do this is because i want to create a lan messenger and i want to display some details of the client in my app.....after connecting it with my machine using sockets....

---

### Post by Beacon11 on 2011-06-21
> **Dhiraj Thakur(Invincible) said:**
> The reason i want to do this is because i want to create a lan messenger and i want to display some details of the client in my app.....after connecting it with my machine using sockets....

Well if you're writing your client, why don't you just add in protocols for asking the client for the OS on which it's running?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
i want to do it in python....and that is wat i am asking ... i just dont know how to code it.... :(

---

### Post by Beacon11 on 2011-06-21
> **Dhiraj Thakur(Invincible) said:**
> i want to do it in python....and that is wat i am asking ... i just dont know how to code it.... :(

Alright, say you write a chat client, and it's being used by person A and person B. If I was designing your chat client, I would use knowledge from this thread ([http://stackoverflow.com/questions/110362/how-can-i-find-the-current-os-in-python](http://stackoverflow.com/questions/110362/how-can-i-find-the-current-os-in-python)) to write a function that obtained a string representing the OS upon which my client is currently running. Both A and B would run this function, thus A knows the OS upon which A is running, and B knows the OS upon which B is running. Then program in a way of exchanging this string, so that now A knows the OS upon which B is running and vice-versa. Would that work?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
thanks fr that besides that is thre any way to obtain its name by machines ip..??...

---

### Post by Beacon11 on 2011-06-21
> **Dhiraj Thakur(Invincible) said:**
> thanks fr that besides that is thre any way to obtain its name by machines ip..??...

Not by IP, but using the same method as above (i.e. obtaining local info and sending to other clients) you can obtain local computer name by socket.gethostname() and then exchange.

---

### Post by Petrolea on 2011-06-21
> **Dhiraj Thakur(Invincible) said:**
> thanks fr that besides that is thre any way to obtain its name by machines ip..??...

No, I don't think there is. It's like looking at a house from the outside and telling what furniture they use. You can't know, but you can ask them (as another post said, client/server would send a string containing info about OS), you can look inside and check (boot up a computer and see) or you can guess (their furniture must be weird since owners always wear weird clothes).

---

### Post by papillion on 2011-06-21
If you just want to find out what OS it's running try this:

import platform
print platform.system(), platform.release

This should yield something like: "Windows XP"

Full doc is here:
[http://docs.python.org/library/platform.html](http://docs.python.org/library/platform.html)

There's a lot of useful stuff in that module. Sounds like what you're looking for.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-22
thans fr help guys....thanks fr introducing me to platform module...:)

---

