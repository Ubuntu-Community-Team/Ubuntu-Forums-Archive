---
title: "Network Problems"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jakl_53 on 2008-10-18
I have a laptop and a regular computer both with Ubuntu 8.04 on them. the laptop is fine on the network. It can see the two other Vista machines in the house but not the other Ubuntu machine. But the regular computer cant see anything. And the vista machines can see the laptop. I dont know whats wrong.

---

### Post by wolfen69 on 2008-10-18
have you installed NFS and nautilus-share?

---

### Post by jakl_53 on 2008-10-19
i dont think so.. but i havent installed either on the laptop and its fine..

---

### Post by superprash2003 on 2008-10-19
if this is for file sharing, you could try this [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by jakl_53 on 2008-10-19
no this really doesnt have anything to do with windows. i was just saying that they couldnt see my computer either. Actually I want to see my shared folders off of my computer on my laptop.

---

### Post by superprash2003 on 2008-10-19
which OS is the computer running??have you enabled file sharing on it?

---

### Post by jakl_53 on 2008-10-19
maybe im just confusing you guys. i want to share the files off of my computer with Ubuntu 8.04 on it. No computers can see it nor can it see any other computers. But my laptop with a fresh install of 8.04 on it can be seen and see other computers. But i want files off of my main computer to be shareable. But its not on the network or something.

---

### Post by jakl_53 on 2008-10-19
I would really like some help with this.:(

---

### Post by lswb on 2008-10-19
Does the system have any net connectivity at all? Can it reach the internet? Maybe it's just a bad cable or hardware fault.

---

### Post by jakl_53 on 2008-10-19
yeah im on it right now. and i also know that both of my ubuntu machines can ping each other.

---

### Post by fslezak on 2008-10-19
Try installing Samba (sudo apt-get install samba) on the regular machiene. Then going to System->Administration->Samba and making the folder that you want into a read only OR Writable share. Try it out.

P.S. Don't stop checking the cables:

:KS

---

### Post by jakl_53 on 2008-10-19
i ran that and it says that samba is already at its highest version. and i dont even have that samba menu..

---

### Post by lswb on 2008-10-19
Is it possibly a firewall or iptables problem? Have you ever run ufw or any other firewall programs on the machine?

What does the system report as its ip address and does it match the subnet being used by the other systems?

---

### Post by fslezak on 2008-10-26
...

---

### Post by fslezak on 2009-04-18
OK. Uninstall tle old samba [sudo apt-get-remove samba] and then install samba from the Add Remove feature in the main menu. That should fix the problem.

---

