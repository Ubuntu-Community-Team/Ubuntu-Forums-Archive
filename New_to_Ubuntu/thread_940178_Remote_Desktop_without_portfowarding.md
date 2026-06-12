---
title: "Remote Desktop without portfowarding"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by jmscharff2 on 2008-10-06
Ok so to give you a basic idea of why I want to be able to set this up...I am on a college campus, so obviously they block everything and you cannot directly edit the ports on the routers(obviously) so I have a computer in my room, that I would like to be able to remote into to either move files or start a dl or anything else.  So is there a solution that I can use that will make it so I can remote in without having to change ports.

(Both the host and client are using Ubuntu 8.08)

Also is there any way to do the same with an ftp type idea?

---

### Post by taqkavar on 2008-10-06
I have not tried it my self ever, but I think something similar to a reverse ssh should work.
Try searching for reverse <what ever you want behind the nat>
If you get reverse VNC to work, then you can use your desktop that is behind the NAT from outside and log in an FTP server like gproftpd hosted in the computer that is outside the NAT. 
I'm sure there are much better ways, but this is all I could think of right now.

Related thread: [http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

Edit: Wait a sec, are both computers on the campus network, or one is in campus, and other is outside? If both computers are within the campus network, then I can think of no other way than to add a 3rd computer outside the campus to sort things out.

---

### Post by jmscharff2 on 2008-10-06
thanks I will try that when I get back to my room.

---

