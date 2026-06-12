---
title: "Auto-start noip2"
date: 2018-11-01
forum: New to Ubuntu
---

### Post by jeppezon on 2018-11-01
Hello!
I've been trying to get noip to start when my ubuntu server starts. However, I don't get it to work...
I followed this "guide":
[https://ubuntuforums.org/showthread.php?t=915750](https://ubuntuforums.org/showthread.php?t=915750)
and did what WRDN said.
I got the script I use from: (line 54-71)
[https://github.com/jamesstout/no-ip/blob/master/README.FIRST#L52](https://github.com/jamesstout/no-ip/blob/master/README.FIRST#L52)

I can start/stop the process by running sudo /etc/init.d/noip2 start/stop
However, how do I do so it automatically run the start command on boot?...

---

### Post by dino99 on 2018-11-01
No real  tweak, but maybe related to init/systemd (a possible path issue)
What related error do you get from 'journalctl -b' ?

---

### Post by jeppezon on 2018-11-01
> **dino99 said:**
> No real  tweak, but maybe related to init/systemd (a possible path issue)
What related error do you get from 'journalctl -b' ?
The only thing in red that shows up is:

Nov 01 13:58:35 media kernel: Couldn't get size: 0x800000000000000e
Nov 01 13:58:35 media kernel: MODSIGN: Couldn't get UEFI db list
Nov 01 13:58:35 media kernel: Couldn't get size: 0x800000000000000e


However not sure if that is related to path error?
Is there a way to filter the logs to show what i'm looking for?

Edit: can't find anything related to noip.

---

### Post by dino99 on 2018-11-01
still can grep ip or noip for example, or net(work)

journalctl -b | grep ip

I have no clue about noip, but i can find some related threads to 'ubuntu server noip' , like [https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/](https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/)

---

### Post by jeppezon on 2018-11-01
> **dino99 said:**
> still can grep ip or noip for example, or net(work)

journalctl -b | grep ip

I have no clue about noip, but i can find some related threads to 'ubuntu server noip' , like [https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/](https://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client-on-ubuntu/)

Yeah I have looked on that guide as well, however they refer to the readme file to make it auto-run. And I put in the script there. Is there no way to by-pass this to just make ubuntu execute the command /usr/local/bin/noip2 when it boots up?

Edit: there is nothing even in the logs about noip, don't think its trying to start it at all.
Edit 2: or just run noip2 at boot should also work...

---

### Post by dino99 on 2018-11-01
A list of threads to activate a systemd script at boot time
[https://www.google.fr/search?q=make+systemd+script+activated+at+boot+time&oq=make+systemd+script+activated+at+boot+time&aqs=chrome..69i57j33.21730j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8](https://www.google.fr/search?q=make+systemd+script+activated+at+boot+time&oq=make+systemd+script+activated+at+boot+time&aqs=chrome..69i57j33.21730j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8)

---

### Post by jeppezon on 2018-11-02
> **dino99 said:**
> A list of threads to activate a systemd script at boot time
[https://www.google.fr/search?q=make+systemd+script+activated+at+boot+time&oq=make+systemd+script+activated+at+boot+time&aqs=chrome..69i57j33.21730j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8](https://www.google.fr/search?q=make+systemd+script+activated+at+boot+time&oq=make+systemd+script+activated+at+boot+time&aqs=chrome..69i57j33.21730j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8)

Okay, tried: sudo systemctl start noip2.service
it failed and in the log: systemctl status noip2.service
I got the following:
```

&#9679; noip2.service
   Loaded: loaded (/etc/init.d/noip2.sh; generated)
   Active: failed (Result: exit-code) since Fri 2018-11-02 09:36:07 CET; 16s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2216 ExecStart=/etc/init.d/noip2.sh start (code=exited, status=203/EXEC)


Nov 02 09:36:07 media systemd[1]: Starting noip2.service...
Nov 02 09:36:07 media systemd[2216]: noip2.service: Failed to execute command: Exec format error
Nov 02 09:36:07 media systemd[2216]: noip2.service: Failed at step EXEC spawning /etc/init.d/noip2.sh: Exec format error
Nov 02 09:36:07 media systemd[1]: noip2.service: Control process exited, code=exited status=203
Nov 02 09:36:07 media systemd[1]: noip2.service: Failed with result 'exit-code'.
Nov 02 09:36:07 media systemd[1]: Failed to start noip2.service.

```

running: sudo journalctl -xe |grep noip2
```

Nov 02 09:36:07 media sudo[2207]: XXX : TTY=pts/1 ; PWD=/home/ XXX; USER=root ; COMMAND=/bin/systemctl start noip2.service
Nov 02 09:36:07 media systemd[1]: Starting noip2.service...
-- Subject: Unit noip2.service has begun start-up
-- Unit noip2.service has begun starting up.
Nov 02 09:36:07 media systemd[2216]: noip2.service: Failed to execute command: Exec format error
Nov 02 09:36:07 media systemd[2216]: noip2.service: Failed at step EXEC spawning /etc/init.d/noip2.sh: Exec format error
-- Subject: Process /etc/init.d/noip2.sh could not be executed
-- The process /etc/init.d/noip2.sh could not be executed and failed.
Nov 02 09:36:07 media systemd[1]: noip2.service: Control process exited, code=exited status=203
Nov 02 09:36:07 media systemd[1]: noip2.service: Failed with result 'exit-code'.
Nov 02 09:36:07 media systemd[1]: Failed to start noip2.service.
-- Subject: Unit noip2.service has failed
-- Unit noip2.service has failed.
Nov 02 09:39:35 media sudo[2475]: XXX : TTY=pts/1 ; PWD=/home/ XXX; USER=root ; COMMAND=/bin/systemctl start noip2.service
Nov 02 09:39:35 media systemd[1]: Starting noip2.service...
-- Subject: Unit noip2.service has begun start-up
-- Unit noip2.service has begun starting up.
Nov 02 09:39:35 media systemd[2478]: noip2.service: Failed to execute command: Exec format error
Nov 02 09:39:35 media systemd[2478]: noip2.service: Failed at step EXEC spawning /etc/init.d/noip2.sh: Exec format error
-- Subject: Process /etc/init.d/noip2.sh could not be executed
-- The process /etc/init.d/noip2.sh could not be executed and failed.
Nov 02 09:39:35 media systemd[1]: noip2.service: Control process exited, code=exited status=203
Nov 02 09:39:35 media systemd[1]: noip2.service: Failed with result 'exit-code'.
Nov 02 09:39:35 media systemd[1]: Failed to start noip2.service.
-- Subject: Unit noip2.service has failed
-- Unit noip2.service has failed.

```

So it seems to be something wrong with the script?

---

### Post by HermanAB on 2018-11-04
Hmm, before playing with these dynamic toys, first ensure that you have a method to recover if it fails to work.  If your machine is right next to you and has a keyboard and screen, then it is OK I suppose, but if it is somewhere in a dark corner of a dank and scary data centre, then you better have a static IP address and the phone number of a friendly monkey at the hell desk at the ready...

---

