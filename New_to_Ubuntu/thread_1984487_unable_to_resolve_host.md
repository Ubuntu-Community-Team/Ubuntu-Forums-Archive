---
title: "unable to resolve host"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by John Peschken on 2012-05-21
j```
john@ASUS-904ha:~$ sudo add-apt-repository ppa:myunity/ppa
sudo: unable to resolve host ASUS-904ha
[sudo] password for john: 

```I attempted to change the name of my system according to a method I found somewhere out on the Worldwide Network of Computers.  That method failed, sort of,  Now I get the above error when I try to run something from the command line.  

Sudo says it can't resolve the host "ASUS-904ha" As the prompt indicates, that is the computer I am running the command on.

Everything seems to work, but this seems like something that will bite me some day.  How can I sort this out?

---

### Post by plucky on 2012-05-22
> **John Peschken said:**
> j```
john@ASUS-904ha:~$ sudo add-apt-repository ppa:myunity/ppa
sudo: unable to resolve host ASUS-904ha
[sudo] password for john: 

```I attempted to change the name of my system according to a method I found somewhere out on the Worldwide Network of Computers.  That method failed, sort of,  Now I get the above error when I try to run something from the command line.  

Sudo says it can't resolve the host "ASUS-904ha" As the prompt indicates, that is the computer I am running the command on.

Everything seems to work, but this seems like something that will bite me some day.  How can I sort this out?


Post output from a terminal for ```
cat /etc/hosts /etc/hostname
```

---

### Post by John Peschken on 2012-05-22
> **plucky said:**
> Post output from a terminal for ```
cat /etc/hosts /etc/hostname
```

Here it is.

```
john@ASUS-904ha:~$ cat /etc/hosts /etc/hostname
127.0.0.1    localhost
127.0.1.1    john-1000H

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ASUS-904ha
john@ASUS-904ha:~$ 


```

---

### Post by plucky on 2012-05-22
> 127.0.1.1    john-1000H

ASUS-904ha

These two have to be the same.Which one do you want as your **hostname**?

Use ```
gksudo gedit /etc/hosts /etc/hostname
``` if gksudo is working.You need to edit both at the same time and use admin privilege.

Good Luck

---

### Post by John Peschken on 2012-05-22
> **plucky said:**
> These two have to be the same.Which one do you want as your **hostname**?
 
Use ```
gksudo gedit /etc/hosts /etc/hostname
``` if gksudo is working.You need to edit both at the same time and use admin privilege.
 
Good Luck
 
I was trying to change it to ASUS-904ha and didn't get the whole job done, somehow.
 
How is gksudo different from plain old sudo?
 
When you say "use admin privlege" do you mean I need to be logged in as an admin, or something else?
 
Thanks for the help.

---

### Post by roelforg on 2012-05-22
> **John Peschken said:**
> I was trying to change it to ASUS-904ha and didn't get the whole job done, somehow.
 
How is gksudo different from plain old sudo?
 
When you say "use admin privlege" do you mean I need to be logged in as an admin, or something else?
 
Thanks for the help.
 
IIRC, it has to do with how it authenticates

---

### Post by John Peschken on 2012-05-22
> **roelforg said:**
> IIRC, it has to do with how it authenticates
 
Sorry, but noob here. "IIRC" Irrational Inquisitors Relief Council?
 
You say GKSUDO authenticates differently. Sadly, I have only the vaguest idea what that means. I can't get at the machine in question until tonight, but I think you're saying I DO have gksudo on my box.

---

### Post by roelforg on 2012-05-22
> **John Peschken said:**
> Sorry, but noob here. "IIRC" Irrational Inquisitors Relief Council?
 
You say GKSUDO authenticates differently. Sadly, I have only the vaguest idea what that means. I can't get at the machine in question until tonight, but I think you're saying I DO have gksudo on my box.

IIRC: If I Remember Correctly

Yeah, stuff as how the passwd and shadow files work and pam is all old news for me...
gksudo is installed by default.
gksudo uses either sudo or su to elevate the permissions to root.
I think it uses su by default. su /etc/passwd for auth and couldn't care less about the hostname.
sudo uses pam, which does care about the hostname because it has to connect back to the account-deamon (or whatever it's called now) to verify the login and if the entry in /etc/hosts for the hostname is missing or pointing to another machine, it will prevent sudo from connecting.

---

### Post by John Peschken on 2012-05-22
That's probably where I went wrong in the first place.  When I read the online article, I thought gksudo was some sort of Kubuntu version of sudo or something.  I didn't have the proper rights, so I got the mess I have.
 
So, I get in these two files and change the incorrect name to what I want it to be, reboot probably, and my little weirdness should away, right?
 
I'll try it this evening.

---

### Post by roelforg on 2012-05-22
> **John Peschken said:**
> That's probably where I went wrong in the first place.  When I read the online article, I thought gksudo was some sort of Kubuntu version of sudo or something.  I didn't have the proper rights, so I got the mess I have.
 
So, I get in these two files and change the incorrect name to what I want it to be, reboot probably, and my little weirdness should away, right?
 
I'll try it this evening.

Well, if you modify your /etc/hosts to read this:
```

127.0.0.1    localhost
127.0.1.1    ASUS-904ha
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters 

```
It should work fine after a reboot.

---

### Post by John Peschken on 2012-05-22
I'll try that tonight.  Thanks for the help!

---

### Post by John Peschken on 2012-05-22
> **roelforg said:**
> Well, if you modify your /etc/hosts to read this:
```

127.0.0.1    localhost
127.0.1.1    ASUS-904ha
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters 

```It should work fine after a reboot.

Perfect now.  Thanks for the good advice.

I guess this is how we learn our way around Linux.  It's how I learned my way around Windows, but that was so long ago, and I spent so many years as a network administrator that  it seems like I was born knowing Windows and Netware.  This is exciting and terrifying.  I could blow it up at any minute!

---

