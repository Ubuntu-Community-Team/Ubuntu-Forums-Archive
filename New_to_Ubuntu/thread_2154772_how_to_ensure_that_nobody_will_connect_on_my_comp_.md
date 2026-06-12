---
title: "how to ensure that nobody will connect on my comp via ssh?"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by kom333 on 2013-06-15
Hello lovely GNU/Linus users!

I have been wondering something. I want to know how to ensure that nobody will connect on my comp via ssh, but not forever, only when I am using the computer.
I tried```
watch -n 1 killall sshd
``` but there is a counter strike: ```
ssh user@host killall watch
```. So question is how to disable others to connect at all, but not forever? 
I'd really like to know the answer, so if someone knows what it is, I'd be grateful! :D

---

### Post by Derek Karpinski on 2013-06-15
First, only allow key based ssh logins:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Second, modify your ssh configuration file to only allow certain users to log in and deny users like root, admin, etc. 

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
Third, install fail2ban.

---

### Post by Cheesehead on 2013-06-16
> **kom333 said:**
>  I want to know how to ensure that nobody will connect on my comp via ssh, but not forever, only when I am using the computer.

You can kill the ssh server upon login and restart it upon logout.
You can restart the ssh server upon login and logout (to reload the conf file), and change the conf file to not listen while logged in.
You can use IPtables to block the ssh port while logged in, and open the port when you log out.

All these are fairly easy to script. Just a matter of what you prefer.
It also depends upon how the system is supposed to know that you are using the computer. Screensaver kicks on? Some other length of time? Some activity or lack of it?

---

### Post by HiImTye on 2013-06-16
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
use keys and disable non-key based logins.
disable other users access.
limit the standard ssh port to your network only, and use a non-standard ssh port for extra-network connections.
use denyhosts or similar software.
optionally, use a port knocker
if you want to see who's logged in use one of```
w
who
```

---

### Post by kom333 on 2013-06-16
Thank you, Derek, for your helpful links. [[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1269065")  Be sure that  I will try out advices I will find there and let you know the outcome. Also, I googled about fail2ban and that seems helpful too. ;)

Cheesehead, thanks to you too for giving me that awesome solutions. All 3 look nice and now   am wondering  if you could give me code for each one. I' d be very grateful!  :)

---

### Post by kom333 on 2013-06-16
HilmTye, that is not helpful- I mean, now I must google almost every single thing you said

---

### Post by HiImTye on 2013-06-17
[http://en.wikipedia.org/wiki/Experiential_learning](http://en.wikipedia.org/wiki/Experiential_learning)
I gave you several starting points, and most of them were previously mentioned and linked. as your question is a far cry from 'Absolute Beginner' I figured you'd be able to do a little bit of leg work after being given direction. my mistake.
[http://lmgtfy.com/?q=ubuntu+port+knocker](http://lmgtfy.com/?q=ubuntu+port+knocker)
[http://lmgtfy.com/?q=ubuntu+denyhosts](http://lmgtfy.com/?q=ubuntu+denyhosts)
[http://lmgtfy.com/?q=ubuntu+sshd_config](http://lmgtfy.com/?q=ubuntu+sshd_config)
[http://lmgtfy.com/?q=ubuntu+ufw](http://lmgtfy.com/?q=ubuntu+ufw)

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by kom333 on 2013-06-17
well yes. i am a little bit advanced user. yeah, sure i could do a little bit if leg work, but i am lazy. plus, when i google i don't always find the answer that will satisfy me. so don't try to judge me dude.

and btw thanks for your link and patience.

---

### Post by Lars Noodén on 2013-06-17
The single most useful thing you could do to limit access via ssh would be to disable password logins and allow keys only.  

There are tutorials all over the net for that including here at Ubuntu:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

The gist is that you create a key pair with a strong passphrase, then copy the public key to the server and put it there inside the file ~/.ssh/authorized_keys

On the server side of things open /etc/ssh/sshd_config and make sure these lines are there:

```

PasswordAuthentication no
PermitRootLogin no

```

---

### Post by kom333 on 2013-06-17
Lars, that seems helpful :)

---

### Post by Hipptambius on 2013-06-17
Just stop ssh when u dont want it running..
sudo service sshd stop
start it again when needed
sudo service sshd start
Simple ;-) thats what i do

---

### Post by LinuxUser666 on 2013-08-13
I quickly ran through [COLOR=#000000]some links that [/COLOR][COLOR=#000000][HiImTye ]("http://ubuntuforums.org/member.php?u=843901") added to your thread and I have one question....since ssh can be ran from virtually any port and not just port 22, how to defend yourself from the matter of an "attacker" trying to connect using different port, and for instance if he uses port 8080 which is http port, does it disable me a usage of http or is my http data traffic rerouted to some other port? 

One more question...can you limit computers that can connect to your host, meaning can you set up your sshd service on your ssh host to just accept data or being connected from certain computer by filtering them somehow, by mac address or other host's name or does all that require setting up a SSH server to manage all that? 

Thank you community, stay brutal [/COLOR]:KS

---

### Post by SeijiSensei on 2013-08-13
I'm not sure I understand your first question.  Someone trying to connect to an SSH server via port 8080 will only be able to connect if the server is listening on that port.  If you want to obfuscate your SSH port, choose some arbitrary high port like 32537.  Any number in the range 1024-65534 is appropriate.

The answer to your second question is to use firewalling rules to limit access.  Do a search for "iptables" to get some examples.

---

### Post by LinuxUser666 on 2013-08-14
Ok thanks for the answer, so is that the most reliable method of blocking someone from accessing my machine? 

My regards.

---

### Post by SeijiSensei on 2013-08-15
As I said, you need to use **iptables** to create firewalling rules.

---

### Post by kom333 on 2013-08-16
[[COLOR=#000000]Hipptambius[/COLOR]]("http://ubuntuforums.org/member.php?u=1830759"), that method you gave me, sounds pretty awesome. :) thanks

---

