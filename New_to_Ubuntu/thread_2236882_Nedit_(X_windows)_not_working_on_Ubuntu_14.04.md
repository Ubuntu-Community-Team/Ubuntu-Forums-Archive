---
title: "Nedit (X windows) not working on Ubuntu 14.04"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by bulrush2 on 2014-07-29
[LIST=1]
[*]I ended up installing Ubuntu Server 14.04 on a new server. X Windows is not installed with the Server edition, so I installed it with : 'sudo apt-get install xorg xauth openbox' per a webpage. 
[*]Server config: Ubuntu 14.04 running as a VM under Vsphere. Server now has a static IP. 
[*]Client: Windows 7 running Putty 0.62 
[*]Server hardware is already behind a firewall and there will only be one user using this server, me. 
[*]I installed OpenSSH when Ubuntu was installed. 
[*]I installed nedit also, just as a test for X Windows. 
[*]'which xterm' gives me '/usr/bin/xterm'. 
[*]'which xstart' gives me no reply. 
[*]I login to a bash shell, but sometimes want to use nedit as a separate X Window. 
[/LIST]

When I ran 'nedit test.txt' I got an error "Nedit: Can't open display". My DISPLAY variable is blank. My XTERM variable says 'xterm'. 


[LIST=1]
[*]How can I get nedit to run in a separate X window? 
[*]I guess I'm not sure how to set up Putty to open a shell window, and allow X window apps from the shell command line. Nor do I know how to make sure Xorg is setup properly. Does someone have a webpage that will walk me through setting up Ubuntu server correctly, and Putty correctly? I've been reading links from Google for 7 hours now with nothing gained. 
[/LIST]
 

Any other thing you need about my system? 

Thanks.

---

### Post by dave131 on 2014-07-29
Does this help you any?

[http://www.cse.yorku.ca/tdb/_doc.php/userg/login/x11-from-home.html](http://www.cse.yorku.ca/tdb/_doc.php/userg/login/x11-from-home.html)

---

### Post by bulrush2 on 2014-07-29
> [http://www.cse.yorku.ca/tdb/_doc.php...from-home.html]("http://www.cse.yorku.ca/tdb/_doc.php/userg/login/x11-from-home.html")


Hm. That is similar to another web page I read, but it has one more piece of info. I'll try it Wednesday. On Putty I did not check the "Remote X11 auth protocol" of MIT-Magic-Cookie-1, which was clearly in my ~/.Xauthority file on the Ubuntu server in my home dir.

I'm also thinking I did not add my user "user@hostname" to the Ubuntu server .Xauthority file via 'xauth add' correctly. I'm still looking for info to confirm that.

---

### Post by dave131 on 2014-07-30
Wish I could help you more but I'm a newbie and I just found that link via a Google search - otherwise I don't know anything about it.

---

