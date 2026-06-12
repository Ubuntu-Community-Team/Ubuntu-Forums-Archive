---
title: "Need help creating a bash script"
date: 2011-03-26
forum: Programming Talk
---

### Post by fixnodecomputer on 2011-03-26
Hello
 
I'm new to linux (specifically to ubuntu server edition 10.10) so excuse me for my lack of knowledge in linux scripting language. Anyhow, I work for a company that does remote computer support, we use vnc protocol to help our clients. I installed a VNC repeater that allows my clients to connect to me going through all firewalls and port forwarding. The linux VNC repeater outputs all connection information to /var/log/vnc.log and looks something like 
```

UltraVnc Linux Repeater version 0.14
UltraVnc Tue Mar 22 03:37:02 2011 > routeConnections(): starting select() loop, terminate with ctrl+c
UltraVnc Tue Mar 22 03:37:12 2011 > acceptConnection(): connection accepted ok from ip: 55.555.555.55
UltraVnc Tue Mar 22 03:37:25 2011 > acceptConnection(): connection accepted ok from ip: 55.555.555.55
UltraVnc Tue Mar 22 03:37:28 2011 > cleanUpAfterRepeaterProcExit(): closing connection (server=5, viewer=6)^C
UltraVnc Tue Mar 22 03:37:36 2011 > main(): relaying done 

```
 
I need the script to check if it sent the last notice, if it did do not send again. The logic behind is if that line exists and has not been already sent then do mail -s, otherwise ignore and do not send. 
 
I got this code from users help in another forum, I was hoping someone could help me add on and elaborate onto it. 
```

#!/bin/bash
while [ 1 = 1 ]
do
grep -e "acceptConnection():" /var/log/vnc.log | tail -1 | mail -s "subject" [EMAIL="email@email.com"]email@email.com[/EMAIL]
done 

```
 
can anyone help a NOOB out! ANY HELP is GREAT!!
 
Thanks,
Phillip K
 
P.S. tried to configure logcheck and similar tools with no success I just need a "Quick and dirty way" as another user mentioned

---

### Post by gmargo on 2011-03-26
I covered a similar problem in this thread: [http://ubuntuforums.org/showthread.php?t=1712940](http://ubuntuforums.org/showthread.php?t=1712940)

The loop there can be adapted for your purposes.  Something like:
```

#!/bin/sh
tail -F -q /var/log/vnc.log | \
grep --line-buffered 'acceptConnection():' | \
while read -r line ; do
    # send each line by mail
    echo "$line" | mail -s "subject" email@email.com
done

```

---

### Post by fixnodecomputer on 2011-03-27
> **gmargo said:**
> I covered a similar problem in this thread: [http://ubuntuforums.org/showthread.php?t=1712940](http://ubuntuforums.org/showthread.php?t=1712940)

The loop there can be adapted for your purposes.  Something like:
```

#!/bin/sh
tail -F -q /var/log/vnc.log | \
grep --line-buffered 'acceptConnection():' | \
while read -r line ; do
    # send each line by mail
    echo "$line" | mail -s "subject" email@email.com
done

```

thanks code worked great!... only problem I had with it is when I first started the code it sent the last 5 occurrences (trashing my mail server temporarily) but after that it worked for every occurrence! 

Thanks again
Phillip K

---

