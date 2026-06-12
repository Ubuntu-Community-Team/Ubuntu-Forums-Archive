---
title: "linux code 4 checking up or down server"
date: 2010-12-23
forum: Programming Talk
---

### Post by keimasi on 2010-12-23
Hello dear frnds.:KS
Plz help me if it’s possible 4 u
I wanna write a code in my linux in VIM editor that it must check a server by sending ping to it and send an e-mail to admin and aware him or her that server is down.
It is not complete, I know that. Wt should I do?
Plz guide me.  Thanx  a lot.
keimasi



#version 0.0001
#write by keimasi
#date 23 dec 2010
Clear
read  -p “ please enter your IP : “  IP
  ping   -c1 $IP
      if  [$?  !=0]
        then 
            mail  -s “ server is down”   admin 
     fi

---

### Post by tgalati4 on 2010-12-23
rwhod
ruptime

---

### Post by keimasi on 2010-12-23
sorry what you mean by this. please guide me more. thanks

---

### Post by keimasi on 2010-12-23
ok. My Dear frnd i see wt u mean. :)
thanks

---

### Post by keimasi on 2010-12-24
dear friend i studied abt these command you guide me. thanks a lot. but i wanna use ping command. i mean i must write a code like that i said. is it work or not. if it doesnt work and i m wrong please tell me.

thanx.

---

### Post by soltanis on 2010-12-24
The **ping** manual page details all the useful options here, but here are the ones that you'll probably want to use:

```

       -c count
              Stop after sending count ECHO_REQUEST packets. With deadline option, ping waits for count ECHO_REPLY packets, until the timeout expires.

       -q     Quiet output.  Nothing is displayed except the summary lines at startup time and when finished.

       -w deadline
              Specify  a  timeout,  in  seconds, before ping exits regardless of how many packets have been sent or received. In this case ping does not
              stop after count packet are sent, it waits either for deadline expire or until count probes are answered or for  some  error  notification
              from network.

```

Combine this with a little bit of bash and a properly configured sendmail in a script, and you can run this as a cron job at whatever interval you find appropriate.

```

#!/bin/sh

host="server.ip.or.dns"
email="your@email.addr"

ping -w 15 -c 1 -q $host || echo "$host is down" | mail -s "network outage" $email

```

If you do not have sendmail/exim/postfix configured to send mail, and you do not want to configure a mail server, but you do have an SMTP server to send mail through, you can use [msmtp]("http://msmtp.sourceforge.net/") which is a sendmail-like replacement that sends mail through an external mail server (and it can be installed through apt-get).

---

### Post by t4thfavor on 2010-12-24
I wrote a crazy perl script not too long ago that works on multiple hosts, and multiple pings. When I find it I will post it for all to see.

---

### Post by keimasi on 2010-12-25
thanks a lot for your guiding. I use and test it.

thanks again:)

---

### Post by keimasi on 2010-12-26
> **soltanis said:**
> The **ping** manual page details all the useful options here, but here are the ones that you'll probably want to use:

```

       -c count
              Stop after sending count ECHO_REQUEST packets. With deadline option, ping waits for count ECHO_REPLY packets, until the timeout expires.

       -q     Quiet output.  Nothing is displayed except the summary lines at startup time and when finished.

       -w deadline
              Specify  a  timeout,  in  seconds, before ping exits regardless of how many packets have been sent or received. In this case ping does not
              stop after count packet are sent, it waits either for deadline expire or until count probes are answered or for  some  error  notification
              from network.

```Combine this with a little bit of bash and a properly configured sendmail in a script, and you can run this as a cron job at whatever interval you find appropriate.

```

#!/bin/sh

host="server.ip.or.dns"
email="your@email.addr"

ping -w 15 -c 1 -q $host || echo "$host is down" | mail -s "network outage" $email

```If you do not have sendmail/exim/postfix configured to send mail, and you do not want to configure a mail server, but you do have an SMTP server to send mail through, you can use [msmtp]("http://msmtp.sourceforge.net/") which is a sendmail-like replacement that sends mail through an external mail server (and it can be installed through apt-get).


   :KSOk . it just ping my ip but  how it check  the server is down or not. I mean how it check the status??
  In my opinion we can use ->   $? 
  By this we understand the status of pinging. But I don’t know it’s continue…

---

### Post by Sub101 on 2010-12-26
> **keimasi said:**
> :KSOk . it just ping my ip but  how it check  the server is down or not. I mean how it check the status??
  In my opinion we can use ->   $? 
  By this we understand the status of pinging. But I don’t know it’s continue…

If server is down then it does not ping.

---

### Post by keimasi on 2010-12-26
> **Sub101 said:**
> If server is down then it does not ping.

yes I now  that. 
see     [FONT=&quot]Code:[/FONT]
    [FONT=&quot]#!/bin/sh[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]host="server.ip.or.dns"[/FONT]
  [FONT=&quot]email="your@email.addr"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]ping -w 15 -c 1 -q $host || echo "$host is down" | mail -s "network outage" $email[/FONT]
  
  
but how does it check it is down and shoild be snd email??

---

### Post by keimasi on 2010-12-28
Hi to all of friends guide me in here. Finally i wrote it and it works!!!  :)

thank a lot
>          #write by keimasi
  
  [FONT=&quot]#!/bin/bash
Clear
read -p “ please enter your IP : “ IP
ping -c1 $IP
if [ $?  != 0]
then 
[/FONT]**[COLOR=#548DD4][FONT=&quot]echo  IP $IP is down on `date`  | mail -s [/FONT][/COLOR]****[COLOR=#548DD4][FONT=&quot]“ server is down alert ”  admin[/FONT][/COLOR]**[FONT=&quot] 
fi[/FONT]
  

---

