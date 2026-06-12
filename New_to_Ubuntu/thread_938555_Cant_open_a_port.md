---
title: "Cant open a port"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by NyTE on 2008-10-05
Ive been trying to use Nicotine(a linux soulseek client)
and i cant use the port 2234

[http://daelstorm.thegraveyard.org/slsktest.php](http://daelstorm.thegraveyard.org/slsktest.php)
says its closed

Im not behind a firewall
and my router is forwarded on that port
but it wont open

---

### Post by NyTE on 2008-10-05
ok i unplugged my router and its still blocked

i thought ubuntus ports are all open??

---

### Post by ibuclaw on 2008-10-05
Nope, all Ubuntu ports are stealthed by default.

If you wish to open one, either have a client that is listening on the port, or use **[ufw]("http://ubuntuforums.org/showthread.php?t=823741")** to open that port up.

[EDIT]
Oh, you have a client app listening...
Well, make sure that you know which port it is listening on, and secondly, use your router to "port-forward" it on your IP.

Regards
Iain

---

### Post by NyTE on 2008-10-05
my router isnt connected anymore and it still wont open

---

