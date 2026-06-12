---
title: "I've lost my internet!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by dover19 on 2008-05-02
I installed Ubuntu on my work PC and I installed VirtualBox to run Adobe CS2 properly as well as install the Xerox/Fiery with Command Workstation because it will only run under Windows or OSX.

In order to install the network printer on VB using it's IP someone said I needed to bridge the network together, so I was trying to do that and got to a point where I added the following code to [FONT="Courier New"]/etc/network/interfaces[/FONT]
```
auto br0
iface br0 inet dhcp
    bridge_ports eth0
```

I then saved the changes and restarted networking. When getting to the next command I got an error so I went online to figure out why I was getting an error, but the internet didn't work anymore. So I went back to [FONT="Courier New"]/etc/network/interfaces[/FONT] and removed the code I had previously inputed, saved and restarted networking again.

I had my internet back. So I stared searching for answers and turns out my version of VirtualBox doesn't have the command I was trying to use. After about 5-10 minutes I couldn't load any page in Firefox anymore, so now I have absolutely no internet on Ubuntu.

I don't understand because I didn't make any changes to anything after I removed the code and got my internet back. It just stopped working at some point and I had to boot into Windows to get here.

---

### Post by mozetti on 2008-05-02
The help function in Virtualbox is very good, and it has extensive entries on networking and bridging. It's how I set up my network bridge. Fire up the help and see what you can work out.

---

### Post by dover19 on 2008-05-02
Thanks, I'll keep that in mind, but I gotta get my internet working first since a bit more of a priority.

---

### Post by w4lgh on 2008-05-02
How are you editing the INTERFACES file? I am logged in as ADMIN and when I try to save it it says I do not have permission. If I can save my additions, I think I can fix my wireless problems.

It says INTERFACES is owned by root, but I thought as ADMIN you have full privledges. Somebody please help...
My direct email is: [email]agj2@bellsouth.net[/email]

---

### Post by dover19 on 2008-05-02
> **w4lgh said:**
> How are you editing the INTERFACES file? I am logged in as ADMIN and when I try to save it it says I do not have permission. If I can save my additions, I think I can fix my wireless problems.

It says INTERFACES is owned by root, but I thought as ADMIN you have full privledges. Somebody please help...
My direct email is: [email]agj2@bellsouth.net[/email]

Well I type ```
sudo gedit /etc/network/interfaces
``` and then I input my password when it asks me to.

---

### Post by w4lgh on 2008-05-02
Thanks...that allowed me to edit the INTERFACES file and save it, but it didn't fix my problem. The system still does NOT see my wireless card. I set the INTERFACES file to read:

auto ath0
iface ath0 inet dhcp
wireless essid {my SSID HERE}

Thought that would force it to see it.

---

### Post by dover19 on 2008-05-04
So nobody has any idea on what has happened here? 

Is there any command I could do in the Terminal and then post the results?

---

