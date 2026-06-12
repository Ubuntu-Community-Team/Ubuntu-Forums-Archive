---
title: "is this going to create problems ?"
date: 2006-04-17
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-04-17
Hi,

 I am new to linux, am trying to write data to a serial port in one of the thread which sends it to a modem  and trying to read data from the same port on another thread when the modem replies. will it create problems? if so what should i  do to avoid this problem. :confused: 

What if my process is running in the background and the user tries to shutdown the machine. and one of my thread is writng into a file at that particular moment, then i guess the file will get corrupted or can i handle this if yes? How should I.

If i am running multiple threads and in the run time i want a certain thread should work with high priority.. can i change it at the runtime. 

I know these are too many to answer but please help me

Thanks a lot in advance

---

### Post by nagilum on 2006-04-17
If one thread is only reading and the other one only writing to the serial port this should work fine. Nonetheless you might want to use the select() call to see if writing or reading will succeed. If both threads need read/write access at the same time some locking mechanism is inevitable, for example using mutexes.

The system-shutdown-event can be easily dealt with. I guess the application will be run as a daemon? By placing a shutdown script in /etc/init.d and linking it to /etc/rc{6,0}.d/ (shutdown, reboot) you let it send your daemon a TERM signal, which may be intercepted by applications. Your application must provide a signal handler for this signal and can perform cleanup operations as soon as it is triggered. This will ensure a proper shutdown.

---

### Post by kolichina_s_s on 2006-04-17
[QUOTE=nagilum]
The system-shutdown-event can be easily dealt with. I guess the application will be run as a daemon? By placing a shutdown script in /etc/init.d and linking it to /etc/rc{6,0}.d/ (shutdown, reboot) you let it send your daemon a TERM signal, which may be intercepted by applications. Your application must provide a signal handler for this signal and can perform cleanup operations as soon as it is triggered. This will ensure a proper shutdown.[/QUOTE]

Thanks for the reply,Yes it will run as a Daemon. I have another question please answer if possible. How much time i will be left with to terminate successfully in case of shutdown? will it give enough time to do all my clean ups? or can i extend my time ? and any idea where i can find such a script(Example)?

A link or two will be of gr8 Help

Thanks again

---

### Post by nagilum on 2006-04-17
In principle as much time as you need. The scripts are executed in order, so as long as your script is running the shutdown process is does not proceed any further until your script exits.
There are already a lot of such scripts installed on your system, under /etc/init.d. For a shutdown they are linked to /etc/rc0.d. Each link begins with Kxx where 'xx' is a number that defines the order in which they are executed on shutdown. One application that has a waiting script is Squid: /etc/init.d/squid (look for stop() function, if you have installed squid of course...). There's also a skeleton-file you can use to write your own script: /etc/init.d/skeleton

---

### Post by kolichina_s_s on 2006-04-17
Thanks again for the Reply :D .
I will look into this now. I hope I  can proceed now. :)

---

