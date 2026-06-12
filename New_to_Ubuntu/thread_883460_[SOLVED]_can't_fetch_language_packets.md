---
title: "[SOLVED] can't fetch language packets"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by brokenhachi on 2008-08-08
hey guys,

i'm trying to install language support for arabic, first of all, when i open language support it tells me its not totally installed so i click install and it tells me that it failed to fetch the packets, then when i look at the dialog box it says 404 error, then when i try to install arabic it gives me the same thing... 

w:failed to fetch something something, then a URL then it says 404 not found


someone help me out?

i'm using hardy

---

### Post by sklyer on 2008-08-08
It sounds like you don't have all the necessary software repositories installed. Go to System > Administration > Software Sources and make sure that all the Ubuntu sources are selected. (I assume that you can access the internet since you were able to post this question.)

---

### Post by brokenhachi on 2008-08-08
yea i have all of the ubuntu sources checked though ...

and yes i am posting with the same computer :)

---

### Post by Dylock on 2008-08-08
You should trying pinging the server to make sure wherever your hitting isn't down
```
ping -c 5 SERVER
```

---

### Post by brokenhachi on 2008-08-08
sorry.. im not sure i get what you mean.. i tried that command, but it didnt work just as it is.. what server should i be pinging?

---

### Post by Dylock on 2008-08-08
You said a URL showed up with a 404 error?
Lets say the URL was [http://www.google.com](http://www.google.com) If I wanted to ping that server to see if it was 'communicating' with me ide say ```
 ping -C 5 google.com 
``` The ping command will send out a packet to the google.com server and see if it gets a response, it will repeat this process for 5 packets (-C sets the number of packets to send)

---

### Post by brokenhachi on 2008-08-08
edit: i guess that was a syntax error.


this is what i get when i ping it:

```
~$ ping -c 5 jp.archive.ubuntu.com
PING ubuntutym.u-toyama.ac.jp (160.26.2.179) 56(84) bytes of data.
64 bytes from ubuntutym.u-toyama.ac.jp (160.26.2.179): icmp_seq=1 ttl=53 time=31.3 ms
64 bytes from ubuntutym.u-toyama.ac.jp (160.26.2.179): icmp_seq=2 ttl=53 time=35.1 ms
64 bytes from ubuntutym.u-toyama.ac.jp (160.26.2.179): icmp_seq=3 ttl=53 time=35.1 ms
64 bytes from ubuntutym.u-toyama.ac.jp (160.26.2.179): icmp_seq=4 ttl=53 time=39.3 ms
64 bytes from ubuntutym.u-toyama.ac.jp (160.26.2.179): icmp_seq=5 ttl=53 time=35.5 ms

--- ubuntutym.u-toyama.ac.jp ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 31.328/35.285/39.303/2.532 ms

```

---

### Post by sklyer on 2008-08-08
Sorry my reply was so stupid. I don't know how to help solve your current problem, but I wanted to make you aware of a problem that I had when trying to install locales--you can get a sense of it [here.]("http://ubuntuforums.org/showthread.php?t=861194") I don't know if this problem will affect you, but beware that it's out there.

---

### Post by brokenhachi on 2008-08-10
well, i tried it again today and it worked, so it must have been that the servers were down or something... even though i was able to ping them... wierd..

anyways thanks for the help guys.

---

