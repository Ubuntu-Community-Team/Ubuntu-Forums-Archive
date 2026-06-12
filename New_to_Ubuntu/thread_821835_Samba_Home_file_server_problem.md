---
title: "Samba Home file server problem"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-07
Hi all,

Been trying to set up a home server as per this tutorial:

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/4)

and I am now stuck at the point where it says I should just be able to go onto another machine and connect to it. I cant.

I am trying a "Places > Connect to server > Windows Share> ip addy of server and "homes" as share folder.

I just get "contents cannot be displayed error"

What am I doing wrong...where can I start trouble shooting. I am very new to this. I can follow tutorials no problem, but when it doesn't work when it says it should I am lost.

Hope you can help.

ps. I went into "network" on the server and fixed the wired connection to a static ip addy.

---

### Post by Happy_Man on 2008-06-07
Hm... can you post your /etc/samba/smb.conf?

---

### Post by kamaji792 on 2008-06-07
I take it you are trying to use a windows box to connect to samba?

Just a few basics.  Can you ping from the box running samba to the windows box?  And the other way round.

Windows:
```
ping <ip address of samba box>
```
Linux
```
ping -c 4 <ip address of windows box>
```

If that works then I guess we want to see your **smb.conf** file.

---

### Post by bodhi.zazen on 2008-06-07
Could be a number of issues, including firewall or networking issues as well.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jcr1 on 2008-06-08
My conf file contains just what is in that tutorial:

```
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "Name"
netbios name = "Server name"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
```

I have added my username (the one on the server) to samba with a password.

I am trying to connect to it now from a ubuntu laptop, which is connecting to the router via Wireless. The server is wired. 

I have been trying to just use Connect to Server and Windows Share... But nowhere does it ask me to enter my user name and password. So a bit confused.

Thanks for the replies.

---

### Post by Happy_Man on 2008-06-08
Well, for one, your workgroup and netbios names have to be filled in, and your share folders haven't been defined. 

```

[global]
    ; General server settings
    netbios name = "THE NAME YOU GAVE YOUR COMPUTER WHEN YOU INSTALLED UBUNTU"		
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[Files]
    path = "path to folder"
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = "your username"
    force group = "your username"

```

Use that one instead of the crap template that other tutorial gave you, and edit whatever is in quotes to match your settings. Remember to run ```
sudo /etc/init.d/samba stop
``` before you start editing, and to restart samba once you're done with ```
sudo /etc/init.d/samba start
```

---

### Post by jcr1 on 2008-06-08
OK, I had filled in my name and netbios name..but now I am using the new suggested one. I filled in my computer name for netbios. and also my username in two places in the bottom. 

For the path to folder to share I put in '/home/username' which is just the home directory of the server.

I restarted the samba daemon and tried to 'Connect to Server' from other ubuntu laptop. I just entered the ip addy. Doing this puts a link on the desktop to that ip addy and when I open it, it contains a folder called 'homes'... not sure where its getting that from?

When I try to enter 'homes' I just get an error: "homes" couldn't be found. Perhaps it has recently been deleted.

Thank you for the help!

---

### Post by jcr1 on 2008-06-08
Aha! Success!

Big stupid error by me... I was entering all that info into the smbpasswd.conf file! Doh! I erased all that and then put it into the right smbb.conf file and it works!!

Thanks ever so much...thats the first hurdle overcome...

Few more things I wish to acomplish... firstly when I browse to the shred folder on the server, i can create things on there, but cannot then delete them, so i guess permissions are set up wrong.

Also I can only log on with the username of the username i created on the server. This is obviously different to the username I am using on the laptop...how do i add more usernames? I.e. a name for whoever wants to connect and an individual password?

i tried ```
smbpasswd -a <newuser>
```

But it gives me an error: ```
Failed to modify password entry for <newuser>
```

Thanks again for all the help!

---

### Post by lisati on 2008-06-08
> **jcr1 said:**
> Aha! Success!

Big stupid error by me... I was entering all that info into the smbpasswd.conf file! Doh! I erased all that and then put it into the right smbb.conf file and it works!!

Thanks ever so much...thats the first hurdle overcome...

Few more things I wish to acomplish... firstly when I browse to the shred folder on the server, i can create things on there, but cannot then delete them, so i guess permissions are set up wrong.

Also I can only log on with the username of the username i created on the server. This is obviously different to the username I am using on the laptop...how do i add more usernames? I.e. a name for whoever wants to connect and an individual password?

i tried ```
smbpasswd -a <newuser>
```But it gives me an error: ```
Failed to modify password entry for <newuser>
```Thanks again for all the help!

You might want to check out the following:
```

smbpasswd -L -a <newuser>
smbpasswd -L -e <newuser>

```
You should have more success adding "<newuser>" with the first line, and the second line enables <newuser>

---

### Post by jonandrews on 2008-06-09
Sounds like you are almost there.
I've put illustrated guides to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


They may help with some final bits & pieces

---

