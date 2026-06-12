---
title: "Setting diferent accesses to the internet for diferent users"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by JLeite on 2012-05-17
I have a computer with Ubuntu12.04 with 3 different users. One of them, I don't want to have Internet access.
I already have set his user privileges according to my purpose. But when I log in as him I continue to have internet access.
His there a way to solve my problem? I need something that can be easily undone to provide Internet access  to him whenever I decide.

---

### Post by idoitprone on 2012-05-17
> **JLeite said:**
> I have a computer with Ubuntu12.04 with 3 different users. One of them, I don't want to have Internet access.
I already have set his user privileges according to my purpose. But when I log in as him I continue to have internet access.
His there a way to solve my problem? I need something that can be easily undone to provide Internet access  to him whenever I decide.

Time to help you to be a jerk

Save each code tag into a script. with its own name
try to make the name simple with no special characters and spaces because you will be typing over and over again.
All these scripts must be run with sudo

```
sudo scriptName
```Restrict access to user
just change "USERNAME" to desired user
```
 #!/bin/bash

iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j DROP
```If I am right on re-enabling a user

```
 #!/bin/bash
iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j ACCEPT
```


[http://www.youtube.com/watch?v=vCmSybYFbgY](http://www.youtube.com/watch?v=vCmSybYFbgY)


[http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html](http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

add this to upstart to block permissions on boot

---

### Post by JLeite on 2012-05-17
@Idoitprone:
This solved my problem. Thank you very much.
The person which i want to provide internet access or not is my son. Sometimes he passes to much time looking at the computer instead of his school books.
Thank you, once more.

---

### Post by idoitprone on 2012-05-17
> **JLeite said:**
> @Idoitprone:
This solved my problem. Thank you very much.
The person which i want to provide internet access or not is my son. Sometimes he passes to much time looking at the computer instead of his school books.
Thank you, once more.

then comes you son on ubuntu forums saying how can he unblock his internet.

lol 

I will help him indifferently.

---

### Post by JLeite on 2012-05-17
Ok. It's fair.
If he get's the skills to undo what I've done I'll be proud of his ways to workaround problems. He'll get the  internet connection for good and I'll try a different approach to the problem.
 In the meantime, I've my problem solved and I thank you that.
Best regards

---

### Post by Derek Karpinski on 2012-05-17
> **idoitprone said:**
> Time to help you to be a jerk

Uncalled for IMO.

---

### Post by idoitprone on 2012-05-17
> **Derek Karpinski said:**
> Uncalled for IMO.

Yea that true, but I will say that everyone who prevents others from using the computer precious resources.

LOL I am being the troll by helping the op.

---

### Post by JLeite on 2012-05-18
After all my problem is not solved, because I've just found that after a shutdown and after a  new boot, all users can connect to the internet. It wasn't my goal, I need something more permanent.

---

### Post by chamber on 2012-05-18
[https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables)

Might be of some help.

---

### Post by JLeite on 2012-05-18
@Chamber:
You mean that in a terminal i should do:
 #!/bin/bash
iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j DROP
iptables-save

to limit internet access
and to open the connection: 
 #!/bin/bash
iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j ACCEPT
iptables-save 
to restore the "USERNAME" access?

---

### Post by chamber on 2012-05-18
I would follow the instructions for Solution 1

```
sudo sh -c "iptables-save > /etc/iptables.rules"
```

Then,

```
gksudo gedit /etc/network/interfaces
```

When in the file, search for the interface you found, and at the end of the network related lines for that interface, add the line:

```
pre-up iptables-restore < /etc/iptables.rules
```

So it would look like

```
auto eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.rules
```

Reboot and test.

---

### Post by JLeite on 2012-05-18
The machine inn question has wireless accesses to the internet.

---

### Post by idoitprone on 2012-05-18
> **JLeite said:**
> @Chamber:
You mean that in a terminal i should do:
 #!/bin/bash
iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j DROP
iptables-save

to limit internet access
and to open the connection: 
 #!/bin/bash
iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j ACCEPT
iptables-save 
to restore the "USERNAME" access?

There are many way to do this I said in the last sentence to add it to upstart. Oh well the post above method is simpler than adding to upstart
run this command



 You choice this is method 2
```
 iptables -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j DROP
```then this
```
sudo sh -c "iptables-save > /etc/iptables.rules"
``````
# Generated by iptables-save v1.3.1 on Sun Apr 23 06:19:53 2006
 *filter :INPUT ACCEPT
 [368:102354] :FORWARD ACCEPT
 [0:0] :OUTPUT ACCEPT
 [92952:20764374] -A INPUT -i lo -j ACCEPT 
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
 -A INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
 -A INPUT -i eth0 -p tcp -m tcp --dport 80 -j ACCEPT -A INPUT -m limit --limit 5/min -j LOG
 --log-prefix "iptables denied: " --log-level 7 -A INPUT -j DROP
[B] -A OUTPUT -p tcp -m owner --uid-owner USERNAME -j ACCEPT # make sure it has this line
 [/B]COMMIT # Completed on Sun Apr 23 06:19:53 2006


```make a file /etc/network/if-pre-up.d/iptablesload
with these contents

```
#!/bin/sh 
iptables-restore < /etc/iptables.rules 
exit 0
```and another file /etc/network/if-post-down.d/
  ```
#!/bin/sh
iptables-save -c > /etc/iptables.rules
 if [ -f /etc/iptables.downrules ]; then 
   iptables-restore < /etc/iptables.downrules
 fi 
exit 0
```now run these 
```
sudo chmod +x /etc/network/if-post-down.d/iptablessave 
sudo chmod +x /etc/network/if-pre-up.d/iptablesload

```taken from the wiki
[https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables)

---

