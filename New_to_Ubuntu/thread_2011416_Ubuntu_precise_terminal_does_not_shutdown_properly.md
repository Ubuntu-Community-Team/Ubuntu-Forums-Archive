---
title: "Ubuntu precise terminal does not shutdown properly"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by emekadavid on 2012-06-27
My 12.04 precise terminal does not shutdown properly. I get the following message on the “shutdown now” command, even when I use “shutdown 5” or more minutes it still gives the same message, thus:  modem-manager[34201]: Could not get the system bus. Make sure the message bus daemon is running! Message: Failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory. 
  Help needed to resolve this issue.

---

### Post by na5h on 2012-06-27
Try:
```
sudo shutdown -h now
```

---

### Post by drpjkurian on 2012-06-27
What I understood is that you are not able to shutdown the machine through terminal
I sometimes try the command
```
sudo halt
```

---

### Post by emekadavid on 2012-06-27
shutdown -h now, was the initial command that refused to shutdown. 
every shutdown command in the book gives me the message as printed above. 
tanx

---

### Post by sudodus on 2012-06-27
Excuse my question (it may be stupid), but did you run it with superuser privileges (using sudo)?
```
sudo shutdown -h now
```

---

### Post by emekadavid on 2012-06-27
i think i did although i cannot remember. i always use root on the xterm.
well, when i log onto ubuntu again (using windows 7 now) i will try it but i believe i did use "sudo su" because i tried several ways to debug the problem message. 
will get back to you

---

### Post by matt_symes on 2012-06-27
Hi
 
> **emekadavid said:**
> My 12.04 precise terminal does not shutdown properly. I get the following message on the &#8220;shutdown now&#8221; command, even when I use &#8220;shutdown 5&#8221; or more minutes it still gives the same message, thus: modem-manager[34201]: Could not get the system bus. Make sure the message bus daemon is running! Message: Failed to connect to socket /var/run/dbus/system_bus_socket: no such file or directory. 
Help needed to resolve this issue.
 
Is this a fresh install of 12.04 or an upgrade from 11.10 ?
 
That is a small L after ls. Please post the output of
 
```
ls -l /var/run/dbus/
```
 
Please post the oputput between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```
 
Kind regards

---

### Post by emekadavid on 2012-06-27
a fresh install from a dvd. will post the requested output soonest. not logged on with ubuntu right now. 
thanks

---

### Post by emekadavid on 2012-06-27
tanx everyone. i logged onto ubuntu precise and tried:
```
sudo shutdown -h now
```and it worked. 
confused ```
sudo -s
```  for the above.
just for the record, [FONT=&quot]the output of ls -l /var/run/dbus/[/FONT]  ```
[FONT=&quot]total 4[/FONT]
  [FONT=&quot]-rw-r--r-- 1 root root 4 Jun 27 15:18 pid[/FONT]
  [FONT=&quot]srwxrwxrwx 1 root root 0 Jun 27 15:18 system_bus_socket[/FONT]
```lots of love and tanx

---

### Post by sudodus on 2012-06-27
Glad it works for you now :KS

Please click on Thread Tools at the top of this page and mark this thread as SOLVED

---

