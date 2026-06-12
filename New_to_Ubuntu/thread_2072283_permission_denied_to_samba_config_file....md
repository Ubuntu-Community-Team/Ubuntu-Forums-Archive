---
title: "permission denied to samba config file..."
date: 2012-10-17
forum: New to Ubuntu
---

### Post by souar on 2012-10-17
I've installed samba and as root enter: 

/etc/samba/smb.conf

however I get the following message: 

-bash: /etc/samba/smb.conf: Permission denied

How can I not even be able to access this file as the root user? I'm stumped!

Any help would be amazing!

---

### Post by cjhabs on 2012-10-17
It looks like you are trying to execute it and it is not a program, it is a configuration file. You should be editing it to change the configuration and then restarting SAMBA. It won't execute because it does not have the execute permissions set - which is correct for this file.

---

### Post by souar on 2012-10-17
Ahhh okay that makes sense, how do I got about opening it in the correct way then?

Edit: Having just looked at Ubuntu servers own guide on how to set up samba they told me to use the exact same command I used... how can they say this works but it doesn't? I would of thought this is an issue with permission hence the 'permission denied' rather than one of how or what I'm trying to launch? 

I may be completely wrong but seems odd to me that what they tell you to do doesn't work unless I've set something up wrong?

---

### Post by deadflowr on 2012-10-17
Graphically:
```
gksu gedit /etc/samba/smb.conf
```

or
In the terminal:
```
sudo nano /etc/samba/smb.conf
```

---

### Post by cjhabs on 2012-10-18
What is the URL of the guide you are using?

---

### Post by ubh on 2012-10-18
> **cjhabs said:**
> What is the URL of the guide you are using?
Don't know the exact link used by deadflowr, but hope this could satisfy you [https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba_Server_Configuration_in_terminal](https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba_Server_Configuration_in_terminal)

---

### Post by deadflowr on 2012-10-18
> **ubh said:**
> Don't know the exact link used by deadflowr, but hope this could satisfy you [https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba_Server_Configuration_in_terminal](https://help.ubuntu.com/community/Samba/SambaServerGuide#Samba_Server_Configuration_in_terminal)

Those aren't links, their terminal commands.

To the OP, the samba configuraton file can only be edited in root. As such, in Ubuntu the easy way to do so, as there is no root user per se(well technically there is, but it is locked and disabled by default so...), is to open up a terminal, and use either of the commands I have listed.
What you're going to do after that is entirely up to you.

Simple way to get a terminal, ctrl+T.

Read this about sudo, rootsudo and graphical sudo:

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo")

---

