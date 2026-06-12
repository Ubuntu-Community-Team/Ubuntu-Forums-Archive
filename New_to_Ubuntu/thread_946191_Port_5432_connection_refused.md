---
title: "Port 5432 connection refused"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by rybaxs on 2008-10-13
Ive trust all at the pg_hba.conf
but nothing happened.. 

How can I open a port? eq. :5432

---

### Post by Orange_and_Green on 2008-10-13
Hello rybaxs :)

You can go the hard way and set up iptables manually, or you could install a program that compiles iptables rules for you.

[Gufw]("http://gufw.tuxfamily.org/index.html") (with ufw installed from the repos) is a very nice one.

Good luck :KS

---

### Post by rybaxs on 2008-10-13
> **Orange_and_Green said:**
> Hello rybaxs :)

You can go the hard way and set up iptables manually, or you could install a program that compiles iptables rules for you.

[Gufw]("http://gufw.tuxfamily.org/index.html") (with ufw installed from the repos) is a very nice one.

Good luck :KS

Hello Orange and Green, Ive already installed gufw, but I can't find where it goes? Is the installed program can be found at the Applications?

I just wonder in this Ubuntu, I've installed lots of programs but I don't know where they go? Where can I find the [Program files in Windows] here in Ubuntu?

---

### Post by cariboo on 2008-10-13
THe equivalent to Program Files in Windows is /usr/bin

Jim

---

### Post by rybaxs on 2008-10-13
I've just search the file at the "Search for files".
Other files are installed separately. 

gufw seems not working. Its like an inactive program.?

---

### Post by Orange_and_Green on 2008-10-13
It should be in System->Administration->Set up firewall (a blue shield icon)

It should give you a window where you can set up things.

If for some reason you cannot use gufw, I guess there's still the option to set up ufw manually...

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by rybaxs on 2008-10-13
Everything is on 
```

ERROR: /var/lib is world writable!

```

Well I think, I need time to relax.. just got frustrated.. 
Thank you for everything..

---

### Post by stephanvaningen on 2008-10-13
To see where a package installed its files you can go to the Synaptic Package Manager (menu System -> Administration -> Synaptic Package manager) and there go to the package you installed, then right-click, choose Properties and click the Tab 'Installed Files'.

Possibly (in some cases) the package added itself to the Applications-menu but did not enable itself to add itself to the menu: you can verify this by right-clicking Application on the menu and select 'Edit Menus': then go through some menu/sub-menus and see if the program is in the list somewhere but just hte check-box in front of it is not yet checked.

> **rybaxs said:**
> Hello Orange and Green, Ive already installed gufw, but I can't find where it goes? Is the installed program can be found at the Applications?

I just wonder in this Ubuntu, I've installed lots of programs but I don't know where they go? Where can I find the [Program files in Windows] here in Ubuntu?

---

### Post by Kevbert on 2008-10-13
ufw is a command line program. If you want to open the port, in terminal,  use
```
sudo ufw allow 5432
```
if you want to close the port, it is
```
sudo ufw deny 5432
```
and to check status
```
sudo ufw status
```
This info can be found [[COLOR="Red"]here.[/COLOR]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

---

### Post by Orange_and_Green on 2008-10-13
> **rybaxs said:**
> Everything is on 
ERROR: /var/lib is world writable!


If this information can be of any use to you, permissions on everything in my /var/lib (including the directory itself) are drwxr-xr-x (755), except PolicyKit which is drwxrwx--- (770) and slocate which is drwxr-x--- (750)...

So, I guess, if you feel desperate you can cross your fingers and do a chmod 755 -R...

---

### Post by rybaxs on 2008-10-13
> **Orange_and_Green said:**
> If this information can be of any use to you, permissions on everything in my /var/lib (including the directory itself) are drwxr-xr-x (755), except PolicyKit which is drwxrwx--- (770) and slocate which is drwxr-x--- (750)...

So, I guess, if you feel desperate you can cross your fingers and do a chmod 755 -R...

Hello, Thank you for everything, I really appreciated..

I've tried chmod 666/755/770/750/777 ufw and ufw/
Error message
```

ERROR: /var/lib is world writable!
ERROR: /var/lib/ufw is world writable!

```
Bash Query 
```

user@user-desktop:/var/lib$ sudo chmod 755 *
user@user-desktop:/var/lib$ sudo chmod 755 ufw

```

Is there a conflict/issue if I upgraded my Gutsy Gibbon to Hardy Heron with this problem? 

I've search "world writable!" and read some forums. They have answers but there is no connection with this problem.

Other Ubuntu PC here are working good with the "ufw". I guess(awildthinkingguess) the problem is the upgrade installation or some configuration I'd made before.

Is there any way I can get rid Port 5432 connection refused?

---

### Post by Orange_and_Green on 2008-10-14
Hi :)

Since it is complaining about var/lib/ being world writable (that is, users that are not in the owner's root can write to it - permission bits are like *******w*), I'd try

```
sudo chmod 755 /var/lib
```
Which only changes permissions for the directory itself. If that still doesn't work, then the command 

```
sudo chmod 755 -R /var/lib
```
Will recursively set this permission to everything inside /var/lib. **Be warned that while the first of the two is safe, the second might severely break other things** so I would suggest you try the latter only if it's something that really really matters to you, and you back up the entire directory before attempting this anyway.

Keepin my fingers crossed my friend,:KS

---

### Post by aska786 on 2008-10-14
Earn Money Online for Clicking the Ads [Sign up]("http://bux.to/?r=aska786") here

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by rybaxs on 2008-10-14
Hi Again,

Yup, ufw is now working after I chmod */*/*/*/*/*, and -R the command
(I closed my eyes and cross my fingers) 
I would like to ask some idea about this issue, 
is the problem is between the connection or in the db configuration?

ufw status
I allow connection from the two PC's, Pc1 and Pc2 have the same ufw Rule.
```

user@user-desktop:~$ sudo ufw allow from 192.168.2.50 to any port 5432
Rule added
user@user-desktop:~$ sudo ufw enable
Firewall started and enabled on system startup
user@user-desktop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
5432:tcp                   ALLOW   192.168.2.129
5432:udp                   ALLOW   192.168.2.129
5432:tcp                   ALLOW   192.168.2.50
5432:udp                   ALLOW   192.168.2.50

```

Im using PostgreSQL, pgAdminIII connection  
```

The server doesn't accept connections:the connection library reports

[B]could not connect to server: Connection refused Is 
the server running on host "192.168.2.50" 
and accepting TCP/IP connections on port 5432?[/B]

```

---

