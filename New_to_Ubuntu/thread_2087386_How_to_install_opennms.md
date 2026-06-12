---
title: "How to install opennms?"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by Rbacon on 2012-11-23
I am attempting to install opennms on my server. I have been on a few sites and have not yet found anything that will work for me. I am getting stuck when it tells me to deb [http://debian.opennms.org](http://debian.opennms.org) stable main and I get the response of No command 'deb' found, did you mean: I know i keep hearing you cant do this in command but from a folder but I am not sure how to navigate to that folder... very new but want to learn.:confused:

---

### Post by nothingspecial on 2012-11-23
Please post a link to the instructions you are following and give a more detailed explanation of what you are trying to do.

---

### Post by newb85 on 2012-11-23
> **nothingspecial said:**
> Please post a link to the instructions you are following and give a more detailed explanation of what you are trying to do.

+1

If I had to guess, I'd say you're supposed to add that line to one of your sources.list files (probably /etc/apt/sources.list).  But I'd need a better idea of what you're doing to be sure.

---

### Post by JRV on 2012-11-23
deb is not a command.

The "deb" and "deb-src" are lines that need to be added to your /etc/apt/sources.list file.

to add them run the command:
```

sudo nano /etc/apt/sources.list

```

Add the lines to the bottom of the file.
Use CTRL-X to close the editor and save the file.

Continue following the directions from the page you linked.

(It is always a good idea to make a backup copy before editing an important system file.)

---

### Post by Rbacon on 2012-11-23
[http://www.opennms.org/wiki/Installation:Debian](http://www.opennms.org/wiki/Installation:Debian)

I am a 100% noob to this so if I need to add something to my source I need to learn how to do that and if you know a website that will help teach me I am game for that!

Not sure about the smile face but the link is still working

---

### Post by Rbacon on 2012-11-23
Now that I ran that command how do I add them...

---

### Post by JRV on 2012-11-23
Use copy/paste to copy these lines to the bottom of the file.

> # contents of /etc/apt/sources.list.d/opennms.list
 deb [http://debian.opennms.org](http://debian.opennms.org) stable main
 deb-src [http://debian.opennms.org](http://debian.opennms.org) stable main


I copied these lines directly from the instructions you linked.

---

### Post by Rbacon on 2012-11-23
> **JRV said:**
> Use copy/paste to copy these lines to the bottom of the file.



I copied these lines directly from the instructions you linked.

I didn't know if they went in here or in the command line after this was edited. Thank you!

---

### Post by Rbacon on 2012-11-23
How do i save my sources.list file once i made added those lines?

---

### Post by Lars Noodén on 2012-11-23
> **Rbacon said:**
> How do i save my sources.list file once i made added those lines?

You have to edit it as root.

```

sudo nano -w /etc/apt/sources.list
sudo apt-get update

```

---

### Post by newb85 on 2012-11-23
Ctrl+X is the command to close nano, and it will ask if you want to save the file, if you haven't already.

For future reference, you might find a window-based text editor like gedit easier to use than nano.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by Rbacon on 2012-11-23
Thank you very much I am starting to get a good grip I beleive but now I ran into another problem I type in sudo apt-get update now and nothing is able to connect but I am able to use the get-apt and install a program. My computer is not connected to my server so I cant copy anything back and forth :(

I would not mind using a window-based editor but this is the first time I ever did anything on a server so I am going by trial and error

---

### Post by Rbacon on 2012-11-23
Is there a way to see if I have a connection to the internet? a command to just test that?

---

### Post by Lars Noodén on 2012-11-23
You can see the status of your network interface with [ifconfig](http://manpages.ubuntu.com/manpages/precise/en/man8/ifconfig.8.html) and test the connection with [ping](http://manpages.ubuntu.com/manpages/precise/en/man8/ping.8.html)

```

ifconfig eth0
ping -c 1 -w 1 8.8.8.8

```

Where 8.8.8.8 is an external machine to aim at.

---

### Post by Rbacon on 2012-12-11
I am back and once again while installing on the save server after a week off I found this when I type in [HTML]/usr/share/opennms/bin/install -dis I get an error Caused by:org.postgresql.util.PSQLExcaption:FATAL: password authenication failed for user "postgres"[/HTML]

My pg_hba.conf file looks like this
local
host     all     all                       trust
IPv4
host     all     all  127.0.0.1/32         trust
IPv6
host     all     all  ::1/128              trust

local replication postgres                 ident
host  replication postgres  127.0.0.1/32   md5
host  replication postgres  ::1/128        md5

Why would I still get this error?

---

