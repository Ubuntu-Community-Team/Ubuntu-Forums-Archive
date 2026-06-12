---
title: "Best way to dual boot (linux) and share data?"
date: 2008-03-31
forum: Other OS Talk
---

### Post by shane2peru on 2008-03-31
Ok, I enjoy dual booting so much that I would like to be able to dual boot and still be able to access my data without all the headaches of permissions etc.  Here is my setup:  
```

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934        7662    54050692+  83  Linux
/dev/sda3            9523        9729     1662727+  82  Linux swap / Solaris
/dev/sda4            7663        9522    14940419+   5  Extended
/dev/sda5            9330        9522     1550241   83  Linux
/dev/sda6            7663        9329    13390146   83  Linux

```
1 is my Ubuntu     /
2 is my  Ubuntu /home
3 is swap
5 is the partition I boot into to backup 1, 2, and 6
6 is my extra partition for loading other OS, or dual booting

I really don't want to change my partition setup, it is too much work. :lol:  So given that, is there any good recommendations to sharing data between two Linux operating systems?  Ubuntu is one, and probably Slackware will be the other, however that is always subject to change. :D  Can I create folder on my /home partition that can be owned and used by anyone?  How could I accomplish such a security breach?  :) 

Shane

---

### Post by gsmanners on 2008-04-01
No problem.

sudo -i
mkdir /home/share
chmod 777 /home/share

Then just make sure you don't reuse a user name or "share" for different installs.

---

### Post by shane2peru on 2008-04-01
Doing that then I won' t have to worry about groups and user id's and all that stuff correct?  Anyone would have access to that folder and data correct?  I'm working in a 'home' setting, so I'm not really worried about security on the inside, just the outside like the web.

Shane

---

### Post by prshah on 2008-04-01
> **shane2peru said:**
> Doing that then I won' t have to worry about groups and user id's and all that stuff correct? 
Shane

Not correct.

Sharing a home partition on two linuxes MAY break your /home/username folder. See [http://ubuntuforums.org/showthread.php?t=725314&highlight=prshah+sharing+home](http://ubuntuforums.org/showthread.php?t=725314&highlight=prshah+sharing+home)
 for the details and resolution. Note the caveat.

Aside from the point of UID and GID mentioned in the link above, the tip given by gsmanners is OK.

But a better way is to simply create a partition with a mount point of "/shared" and give it all the permissions with chmod 777. Note that even in this case, your /home partition will still be at risk, unless "treated" as suggested in the link above.

---

### Post by shane2peru on 2008-04-01
> **prshah said:**
> Not correct.

Sharing a home partition on two linuxes MAY break your /home/username folder. See [http://ubuntuforums.org/showthread.php?t=725314&highlight=prshah+sharing+home](http://ubuntuforums.org/showthread.php?t=725314&highlight=prshah+sharing+home)
 for the details and resolution. Note the caveat.

Aside from the point of UID and GID mentioned in the link above, the tip given by gsmanners is OK.

But a better way is to simply create a partition with a mount point of "/shared" and give it all the permissions with chmod 777. Note that even in this case, your /home partition will still be at risk, unless "treated" as suggested in the link above.

If you read the link carefully it seems to me that you are not creating the same username for both distros, simple making a folder called share, and then giving permission to the world to write, execute, or read that folder and putting only the data to be shared (ie.  Documents, Music, Pictures, etc.)  No configuration files would be shared that way.  Each distro would have it's own username setup.  I have been down that road before. :)  Thanks for the concern though.

Shane

---

