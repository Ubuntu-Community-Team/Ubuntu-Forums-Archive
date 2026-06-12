---
title: "samba shares with ip, computer name and user name is constrained only to one user?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by digilevi on 2008-09-04
hi everyone.

im new to ubuntu but i really am in love with samba shares. is it possible that i constrain username with his ip and computer name? so that he cannot log in on other machines on the network? ive been to samba.org but i think theres no forum there.

i hope its possible.

thanks

cheers!

---

### Post by jonabyte on 2008-09-04
You can set it up to accept certain users only. See below:

```
valid users = username
```

Place this in the share name section and you will have to add all the valid users to the box.

---

### Post by digilevi on 2008-09-08
> **jonabyte said:**
> You can set it up to accept certain users only. See below:

```
valid users = username
```

Place this in the share name section and you will have to add all the valid users to the box.

Hi jonabyte, 
thanks for replying. will this code restrict users from using other machines to log in. meaning using other computer names? What I really want to do is to restrict users from using other PC's on the network to login with their usernames. Is this possible in Samba? :confused::-k

ex.
valid users = tom[192.168.1.190+Tom's Computer]

---

### Post by jonabyte on 2008-09-08
It will restric by username that was used to log into the computer.

But to restrict users from logging into other computers, you may need to use an Active Directory for this, I think Samba can handle this but not sure how. You may need to read up on the docs.

---

### Post by gregphil on 2008-09-08
What, exactly, are you trying to prevent?

Samba can easily limit which user(s) are allowed to connect to a specific share (on the machine Samba is running on)   

in /etc/samba/smb.conf

[Global]
    security = USER
[Constrained]
    guest ok = no
    valid users = user1

But maybe you are trying to do something else.....

---

### Post by bab1 on 2008-09-08
With the Samba suite, Ubuntu can act as a Domain Controller for a Windows/Linux environment.  This is NT4; old windows domain style. It is capable of maintaining a centralized users login database.  This is really not Samba's strength though.  There are more current methods for this.  LDAP is one way.  Google OpenLDAP.

---

### Post by digilevi on 2008-09-09
Thanks for the help guys! 

> What, exactly, are you trying to prevent?

hi gregphil. I just want to prevent users from accessing the share on other computer aside from theirs'. So If one username to the share is "tom", I would like to constrain that username to *ex. 192.168.1.xxx* and *Tom's Computer*. So if they try to connect on another PC, samba doesnt allow it because they are not on their respective computer and/or IP. 

Is this possible?

thanks in advance

cheers! :)

---

### Post by digilevi on 2008-09-12
i think its really not possible :( but ill try to rtfm :D

---

### Post by gregphil on 2008-09-15
I am not sure, but I think you are just asking for 
 
security = USER
 
This will require each connection to authorize with a username / password.  It that username or password is not setup (or allowed by guest ok = true) then the connection is refused.   So normally each machine would be setup for a specific user and not others, thus only the "real" user could connect.
 
Now...in a non-peer-to-peer setup, like a Domain login, one machine is setup as the authorization master so any valid user can login to any machine in the domain (this is claimed to be a feature).  However even in the doamin setup you can have different /etc/samba/smb.comf files on each machine and then only allow any share to a certain user(s).  See "man smb.conf" for the syntax of the "allow" settings, by default all users who can logon are allowed, but you can easily limit this.
 
I am sure what you want can be done, you just need to state it more clearly.  You aren't in a school trying to deal with sharing computers to students are you?
 
Thnak You.

---

### Post by digilevi on 2008-09-18
> **gregphil said:**
> You aren't in a school trying to deal with sharing computers to students are you?
 
Thnak You.


hi gregphil. thanks for the help. i will try this as soon as i reformat my pc. 

Im not on a school but an office with lots of shares, so i would be dealing with many officemates :D. I just want to make sure they dont log in from other computers other than theirs.

thanks again

---

### Post by Bucky Ball on 2008-09-18
Found this in Synaptic Package Manager that might be of some use. Open and do a search for:

                                       **system-config-samba**


Neat GUI you might find helpful and could be what you're after.

---

### Post by Tilex on 2008-12-05
If you use this option in the smb.conf file:

> # Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

You use a smb.conf configuration for each computer in your office, and for example the line: "username = Patrick" would only be existing on the file "smb.conf.patrick" if "patrick" is the netbios name.

Or am I off-track here?

---

### Post by digilevi on 2008-12-12
> **Tilex said:**
> If you use this option in the smb.conf file:



You use a smb.conf configuration for each computer in your office, and for example the line: "username = Patrick" would only be existing on the file "smb.conf.patrick" if "patrick" is the netbios name.

Or am I off-track here?

thanks Tilex

i think this is what im trying to accomplish. if this code constrains one share to a specific ip **and** its netbios name as one and only one session and if the user will not be able to login his username and password on another computer with a different netbios name, then this is totally, 100% cool. :guitar:

is this what this code do? did i explain my self well? :confused:

---

