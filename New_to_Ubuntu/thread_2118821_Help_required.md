---
title: "Help required"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by Abhilashjoy on 2013-02-22
HI 

I have a system with ubuntu 12.10

I have installed all my applications like Wine, Eclipse ect installed in Root login.
Now i am not able to access the programs and folders from a user login.
How can i give root access to other users????


Thanks
Abhi

---

### Post by slickymaster on 2013-02-22
What you're aiming defeats the security model that's been in place for years. Applications are meant to be run with non-administrative security so you have to elevate their privileges to modify the underlying system.
It's just good practice on any operating system to run your applications on a user level and leave administrative tasks to the root user, and only on a per-need basis.

Giving root access to individual users can lead to the following issues (to name a few):
**Machine Misconfiguration** — Users with root access can misconfigure their machines, open up security holes without knowing it.
**Running Insecure Services** — Users with root access may run insecure servers on their machine, such as FTP or Telnet, potentially putting usernames and passwords at risk as they pass over the network in the clear.
**Running Email Attachments As Root** — Although rare, email viruses that affect Linux do exist. The only time they are a threat, however, is when they are run by the root user.

---

### Post by Mark Phelps on 2013-02-22
> **Abhilashjoy said:**
> I have installed all my applications like Wine, Eclipse ect installed in Root login.
BEFORE you jump into using Wine, you need to go to the WineHQ website, look up the application compatibility database page, and do searches for the apps and versions you want to run.  If the tool doesn't find anything, or the rating is less than Gold, installing those apps is essentially going to be a waste of your time.  Just telling you now before you get frustrated later.
> Now i am not able to access the programs and folders from a user login. You should be able to RUN apps without being root.  If you have to become root to run the apps, then something else is wrong.
> How can i give root access to other users????
Basically -- you DON'T!  This completely undermines the security model in place in Ubuntu, and is strongly discouraged.  You need to find out why you can't run the apps without root access.


Thanks
Abhi[/QUOTE]

---

### Post by cybergalvez on 2013-02-22
> **Abhilashjoy said:**
> HI 

I have a system with ubuntu 12.10

I have installed all my applications like Wine, Eclipse ect installed in Root login.
Now i am not able to access the programs and folders from a user login.
How can i give root access to other users????


Thanks
Abhi

It looks like you are following the windows model where things install to a "all user" get to be used by everyone. Thats not how it works in *nix. binaries get located to folders such as /usr/bin and places like that. Most programs end like stuff that google would install end up in the opt folder. You could move your programs to the opt folder and them make them readable to everyone. That should accomplish essentually what you are trying to do.

---

### Post by fdrake on 2013-02-22
> **Abhilashjoy said:**
> HI 
How can i give root access to other users????

uninstall the applications with root . logout and login with your regular user . Install the applications using your username. If you need permissions access use sudo command.

---

### Post by Abhilashjoy on 2013-02-25
Thanks for your valuable feedback sir. 

Abhi

---

