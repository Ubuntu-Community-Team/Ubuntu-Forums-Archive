---
title: "UFW  Logfile ?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-20
Hello.All

Can someone please help me, with this. How do I look at the logging file I can't seem to find it anywhere. Is it done from a Term. :(

Thank you

Badoxide

---

### Post by tuxxy on 2008-08-20
Try this from terminal

```
sudo ufw | grep LOG
```

If no luck you may need to enable LOGGING first,

```
sudo ufw logging on
```

---

### Post by Badoxide on 2008-08-20
Hello.tuxxy

Hm when I do the command it ask, for my pass then nothing happens. Talking about this one here sudo ufw | grep LOG

Thank you

Badoxide

---

### Post by bhadotia on 2008-08-20
Just type in your passwd and press enter (What you type will not show up on screen). If then there is no output  you need to enable logging I think.

---

### Post by Badoxide on 2008-08-20
Hello.bhadotia

Yes I know about the pass not showing. What I am not getting is an output from logging file using the.

code

sudo ufw | grep LOG

And yes I do have logging turned on.

Thank you

Badoxide

---

### Post by Badoxide on 2008-08-20
Hey.All

Anyone else have an idea to get this to show me, some type of logging.

Thank you

Badoxide

---

### Post by tuxxy on 2008-08-20
Type in

```
sudo ufw
```

now you can see all the command available, including logging

---

### Post by Badoxide on 2008-08-20
Hi.tuxxy

Yes I had a look at that. Anyways here is what I get.

sudo ufw
[sudo] password for me: 

Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information


So far I have tried to use

sudo ufw enable <--- This had me do a restart.

sudo ufw logging on.

sudo ufw status

Still no happy for me. ;)

NOTE:

Please I also installed the Gufw, and had enabled the firewall I was thinking this may of had something to do with it so I disabled it to make sure, but I still had the same problem no logging.

Thank you

Badoxide

---

### Post by Badoxide on 2008-08-21
Hey.All

Well not all to sure what it was I just did, but I think its starting to do something just don't know what it is, Yet could someone have a look at this what is it that its saying. How do I find some info on this stuff please.

Logging enabled
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK FORWARD]: ' 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK INPUT]: ' 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK NOT-TO-ME]: ' 

None of the above looks bad to me, but what do I know. ;)

Thank you

Badoxide

---

### Post by gaiterin on 2008-09-17
Hi!
In Gufw 0.20.0 you have got Gufw Log and enable/disable ufw log ;)
Best regards!
Marcos

---

### Post by manishsk on 2008-12-21
i think this should work at your end...

```
sudo iptables -L -n | grep LOG
```

---

### Post by thesavager on 2009-03-07
Hi all, 

Let me explain something here:

the command: ```
sudo ufw | grep LOG
``` only shows you the output of the command "sudo uwf" and then piped to a filter to filterout the word "LOG", so infact this command is useless to us.
in commandlist of ufw is no "LOG" text, so NO output here, with this command.

Also the command:```
 sudo iptables -L -n | grep LOG
``` is useless to us.
It shows you the list of rules of iptables and again filtered for the word "LOG"
so thats why you see these iptables rules:

LOG all -- 0.0.0.0/0 0.0.0.0/0 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK FORWARD]: '
LOG all -- 0.0.0.0/0 0.0.0.0/0 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK INPUT]: '
LOG all -- 0.0.0.0/0 0.0.0.0/0 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK NOT-TO-ME]: '

Even with logging enabled in GUI, or manualy, ufw doesn't log at all.
The only logfile i could find was /var/log/gufw_log.txt but is no use , since this logfile doesnt log any traffic. !!
This issue will be reported directly to the maintainers of ufw !!!

to have a quick view at your logfiles you can use the "cat" option in your console.(you don't have to be root)
example: ```
cat /var/log/gufw_log.txt
```
You can also view your logfiles live!!! to see whats happening:
```
tail -f /var/log/gufw_log.txt
```

Thanx for reading this article

---

### Post by thesavager on 2009-03-10
Hi again, 

GUFW firewall finaly starts logging, in /var/log/messages

To filter out everything of UFW firewall, we can do like this:
```
cat /var/log/messages | grep UFW
```

 and save it to a file is also possible.

```
cat /var/log/messages | grep UFW > ufw.log
```
now you can view everything, in your own time.

Also live! viewing is possible.
```
tail -f /var/log/messages | grep UFW
```

Hope this helps .....

---

### Post by intel352 on 2009-09-24
thanks thesavager, your post helped, unlike the many others that had us grepping the wrong output for the wrong term :-)

---

### Post by kennethsoona on 2010-01-09
just read:
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html#firewall-logs](https://help.ubuntu.com/8.04/serverguide/C/firewall.html#firewall-logs)

or

[https://help.ubuntu.com/8.10/serverguide/C/firewall.html#firewall-logs](https://help.ubuntu.com/8.10/serverguide/C/firewall.html#firewall-logs)

or

[https://help.ubuntu.com/9.04/serverguide/C/firewall.html#firewall-logs](https://help.ubuntu.com/9.04/serverguide/C/firewall.html#firewall-logs)

or

[https://help.ubuntu.com/9.10/serverguide/C/firewall.html#firewall-logs](https://help.ubuntu.com/9.10/serverguide/C/firewall.html#firewall-logs)

---

### Post by SuperMike on 2010-05-25
What file do I edit for the ufw config so that I can point the ufw logfile to another location?

---

