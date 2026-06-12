---
title: "[SOLVED] Need help setting up file sharing and want to learn"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by boof1988 on 2008-10-26
Want to learn more about using inputs in the Terminal so I can understand more about what I'm actually doing to/with my system.  And setting up file sharing may be a good way to learn.  I don't necessarily want to do everything using Terminal, but would like to use it some.

Sorry for so many questions in one post.  Even just a little help at a time would be helpful.  Thanks in advance for your help with this.

I have set up printer sharing on my home network already:
[INDENT][LIST=1]
[*]Set-up printer on desktop computer.
[*]Set-up desktop computer firewall as follows:
```
sudo ufw enable
sudo ufw default deny
sudo ufw allow from 192.168.2.0/16 to any
```
[*]Set-up notebook computer to use desktop computer as a print server.
[/LIST][/INDENT]

Now I want to set-up file-sharing on home network for both computers:
[INDENT][LIST=1]
[*]Allow file sharing to/from both computers on home network.
[*]Change notebook computer firewall settings to higher security when using public wifi hotspots.
[/LIST][/INDENT]

Already enabled ufw on notebook computer:
[INDENT]Here is the status of ufw on notebook computer:
```
To                         Action  From
--                         ------  ----
Anywhere                   ALLOW   192.168.0.0/16
631:tcp                    ALLOW   192.168.0.0/16
631:udp                    ALLOW   192.168.0.0/16
Anywhere                   ALLOW   192.168.2.7

```
[LIST=1]
[*]The 1st line allows the displayed (range of) addresses access to anywhere on notebook computer?
[*]What do the "631:tcp" and "631:udp" on 2nd and 3rd lines mean?
[*]The 3rd line allows 192.168.2.7 access to notebook computer?
[/LIST]
[/INDENT]

Regarding the meaning of the commands:
[INDENT][LIST=1]
[*]What is the meaning of "sudo"?  Does it just allow a user to access 'stuff' at the 'root' level?

[*]I think the "ufw" part just indicates what application is being accessed/modified?
[/LIST][/INDENT]

---

### Post by markharding557 on 2008-10-26
you may find many of your answers here
[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

---

### Post by boof1988 on 2008-10-26
> **markharding557 said:**
> you may find many of your answers here
[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

I am looking at this link and other places as well.  It's just hard for me to weed through to the answers.  So any answers here are much appreciated.  Is the original post too long?

---

### Post by boof1988 on 2008-10-26
Right now this link looks useful.

[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

The syntax and how to construct the commands is something I lack.  Am a definite noob... but I want to learn.

---

### Post by boof1988 on 2008-10-26
I used this (below posted method recommended by Confused57 on another thread) and it worked like a charm.  Just wanted to post it here in case it can help anyone else.

> **confused57 said:**
> You might want to look into ssh networking for file sharing:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

The network is running now.  My next objective is to ***see*** if I can get access to an external drive plugged into the "server".

Thanks for everyone's help.

---

### Post by Xiong Chiamiov on 2008-10-26
> **boof1988 said:**
> 
Regarding the meaning of the commands:
[INDENT][LIST=1]
[*]What is the meaning of "sudo"?  Does it just allow a user to access 'stuff' at the 'root' level?

[*]I think the "ufw" part just indicates what application is being accessed/modified?
[/LIST][/INDENT]

You are correct about [sudo]("https://help.ubuntu.com/community/RootSudo").  UFW is the Uncomplicated Firewall, a very nice app that sits on top of iptables and makes it easy to control access.

Personally, I'd use [nfs]("http://delicious.com/xiong.chiamiov/nfs") to share between Linux machines.  It's super-easy to setup.  You can, of course, very easily do it through the GUI, but you're doing it as a learning excercise.

---

### Post by boof1988 on 2008-10-26
> **Xiong Chiamiov said:**
> You are correct about [sudo]("https://help.ubuntu.com/community/RootSudo").  UFW is the Uncomplicated Firewall, a very nice app that sits on top of iptables and makes it easy to control access.

Personally, I'd use [nfs]("http://delicious.com/xiong.chiamiov/nfs") to share between Linux machines.  It's super-easy to setup.  You can, of course, very easily do it through the GUI, but you're doing it as a learning excercise.

Thanks for the help.  I set up access using ***Places>>Connect to Server*** and when I restarted Ubuntu (after using MS Windows XP) the link to the other computer's drive was no longer on my desktop.  It seems that the link disappeared.

Will try 'nfs' and see how it works.  It'll help me learn more that way.  Using actual commands will help me understand what is actually going on.  My frustration with Windows has occurred cause I don't know what is going on when I click a button.

Thanks Again,  :)

---

