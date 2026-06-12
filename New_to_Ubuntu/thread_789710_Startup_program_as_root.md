---
title: "Startup program as root"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Tekk on 2008-05-10
Alright, I've looked around the forums/internet but haven't found a solution that fits my scenario. 

Basically I'm trying to enable a program called Synergy to start-up automatically upon boot. This program enables mouse/keyboard control from another networked computer via the LAN. As such, I don't normally have a keyboard or mouse connected to the system. 

So, essentially I need to run the command to connect to the Synergy server as root after the network is up. I tried doing this via the Sessions options as "sudo ...," but I'm fairly certain it's not working as I don't have a way to feed it the root password. I also tried using rc.local, but I believe using this method it is starting before the network is up. 

So now you see my conundrum. Any tho'ts? Thanks!

---

### Post by spiderbatdad on 2008-05-10
I'm thinking put the program in /usr/sbin and your start script in /etc/init.d  A proper script should be able to check that networking is established. Making root the owner of the program, I think will solve your 'root' problem. sudo chown root:root program_name
Of course the program need to have execute permission: sudo chmod a+x program_name

Start up manager can be quirky, if you go that route. Sometimes takes several attempts before sticking.

---

### Post by sdennie on 2008-05-10
There may be a better way but, I think a simple script like this would work for you:

```

#!/bin/bash
while ! ifconfig eth0 | grep "inet addr" ; do
    sleep 1
done

thing_you_want_to_run


```

That just wakes up once a second to see if eth0 has been assigned an IP address and, if so, it runs "thing_you_want_to_run".  You could either call that script from rc.local or remove the "#!/bin/bash" and paste it directly into rc.local.

---

