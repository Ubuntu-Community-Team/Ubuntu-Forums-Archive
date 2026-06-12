---
title: "HELP: irssi cant connect to any server"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by gpy on 2012-01-26
Hello, im a new Ubuntu user, im using 11.10 Oneiric Ocelot. Im dual booting windows 7 and Ubuntu on 2 separate hdds. Everything went smooth from instalation to first booth until ...
I installed irssi and couldnt connect to any server. i reinstaled Ubuntu and im getting the same problem. I rebooted to Windows 7 and run Mirc, and i could connect to any server with no issues.

What i get in irssi

> Irssi: Looking up irc.freenode.net
Irssi: Connecting to irc.freenode.net [32.1.6.176] port 6667
Irssi: Unable to connect server irc.freenode.net port 6667 I looked up in the forums and i couldnt find an awnser to this problem.
[FONT=Arial]
i used the telnex command[/FONT] as sugested in this [thread ]("http://ubuntuforums.org/showthread.php?t=1633293&highlight=connect+freenode")and this is what i get when i use % **telnet **[I]irc.freenode.net 6667

[/I]> kilo11@delta:~$ telnet irc.freenode.net 6667
Trying 32.1.6.176...
Trying 2001:6b0:e:2018::172...
Trying 2001:1418:13:1::25...
Trying 2001:6b0:5:1688::200...
Trying 2a01:270:0:666f::1...
Trying 2001:820:2::6...
Trying 2001:19f0:feee::dead:beef:cafe...
telnet: Unable to connect to remote host: Network is unreachable[FONT=Arial]I can browse normally and i havent done anything to the hosts file. [/FONT]

[FONT=Arial]Thanks, gpy.[/FONT]

---

### Post by |{urse on 2012-01-26
Try chat.freenode.net instead. ;)

Here's a current list of server names.

[http://freenode.net/irc_servers.shtml](http://freenode.net/irc_servers.shtml)

---

### Post by gpy on 2012-01-26
hi, thanks for the fast answer but i still cant connect to any irc server, i tried chat.freenode.net and heres what i get

```
13:54 -!- Irssi: Looking up chat.freenode.net
13:54 -!- Irssi: Connecting to chat.freenode.net [32.1.6.176] port 6667
13:57 -!- Irssi: Unable to connect server chat.freenode.net port 6667 
          [Connection timed out]
```

---

### Post by |{urse on 2012-01-26
Are you running firestarter or another firewall? Have you checked your router to make sure the port is open? do this before we proceed :)

Have you tried to connect to a different irc server?
in irssi..
> /server snape.p2pchat.net 6667

if youre getting the same connection problems at least we can rule out things to be on your end.

If there is no obvious port blockage, run irssi, try to connect then open a new term and run this and paste its output.

> lsof -P | grep :6667

I just fired up irssi and connected with no problems with /server chat.freenode.net 6667 and /server irc.freenode.net so theres something "firewally" going on here lol.

You weren't banned or kicked recently or anything were you?

---

### Post by gpy on 2012-01-26
this is what i get after doing netstat -antp with irssi open

```
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:8089          0.0.0.0:*               LISTEN      5914/banshee    
tcp        0      1 192.168.1.2:39739       199.59.148.87:443       SYN_SENT    14471/firefox   
tcp        0      0 192.168.1.2:58231       74.125.159.132:80       ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:38223       74.125.229.248:80       ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:49530       91.189.94.12:80         ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:57687       209.85.145.120:80       ESTABLISHED 14471/firefox   
tcp        1      0 192.168.1.2:45876       91.189.88.33:80         CLOSE_WAIT  31916/gvfsd-http
tcp        0      0 192.168.1.2:54744       74.125.159.84:443       ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:44440       74.125.229.202:80       ESTABLISHED 14471/firefox   
tcp        0      1 192.168.1.2:49502       91.189.94.12:80         FIN_WAIT1   -               
tcp        1      0 192.168.1.2:40070       208.93.140.180:80       CLOSE_WAIT  5914/banshee    
tcp        0      0 192.168.1.2:49532       91.189.94.12:80         ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:49533       91.189.94.12:80         ESTABLISHED 14471/firefox   
tcp        1      0 192.168.1.2:40067       208.93.140.180:80       CLOSE_WAIT  5914/banshee    
tcp        1      0 192.168.1.2:40068       208.93.140.180:80       CLOSE_WAIT  5914/banshee    
tcp        0      0 192.168.1.2:49526       91.189.94.12:80         TIME_WAIT   -               
tcp        1      0 192.168.1.2:40069       208.93.140.180:80       CLOSE_WAIT  5914/banshee    
tcp        0      0 192.168.1.2:58232       74.125.159.132:80       ESTABLISHED 14471/firefox   
tcp        0     38 192.168.1.2:33037       69.50.232.54:443        FIN_WAIT1   -               
tcp        0      0 192.168.1.2:49527       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:54596       74.125.229.243:80       ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:49529       91.189.94.12:80         ESTABLISHED 14471/firefox   
tcp        0      0 192.168.1.2:49531       91.189.94.12:80         ESTABLISHED 14471/firefox   
tcp        1      0 192.168.1.2:53175       72.233.119.202:80       CLOSE_WAIT  31916/gvfsd-http
tcp        1      0 192.168.1.2:40065       208.93.140.180:80       CLOSE_WAIT  5914/banshee    
tcp        0      1 192.168.1.2:47060       72.29.166.157:80        SYN_SENT    5914/banshee    
tcp        0      0 192.168.1.2:49528       91.189.94.12:80         ESTABLISHED 14471/firefox   
tcp        1      0 192.168.1.2:45877       91.189.88.33:80         CLOSE_WAIT  31916/gvfsd-http
tcp        0      1 192.168.1.2:39738       199.59.148.87:443       SYN_SENT    14471/firefox   
tcp        1      0 192.168.1.2:40066       208.93.140.180:80       CLOSE_WAIT  5914/banshee    
tcp        1      0 192.168.1.2:45875       91.189.88.33:80         CLOSE_WAIT  31916/gvfsd-http
tcp        0      0 192.168.1.2:49524       91.189.94.12:80         TIME_WAIT   -               
tcp        0      0 192.168.1.2:49522       91.189.94.12:80         TIME_WAIT   -               
tcp        1      0 192.168.1.2:54827       91.189.89.31:80         CLOSE_WAIT  31916/gvfsd-http
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -   
```

as for firewalls, nope i havent installed one, i just reinstaled ubuntu for mmm 2 hours maybe, so its a clean install, everything is on default i guess.

---

### Post by gpy on 2012-01-27
i have trying to connect to irc with different clients now with no success. i can connect via mibbit tho, any ideas?

---

### Post by gpy on 2012-01-29
allright i somewhat know whats wrong. irssi wasnt resolving dns hostnames. i checked this out by connecting freenode with its ip address and i managed to connect! how can i fix that dns resolve problem?

---

### Post by dodo3773 on 2012-01-29
> **gpy said:**
> allright i somewhat know whats wrong. irssi wasnt resolving dns hostnames. i checked this out by connecting freenode with its ip address and i managed to connect! how can i fix that dns resolve problem?

If that is the problem I would say the next logical step to test would be to try another dns server. Maybe google or opendns or similar to make sure that you really found the root of the problem.

---

### Post by andrew.46 on 2012-01-30
It all sounds a little odd. Perhaps before getting too radical you could simply close irssi, move your irssi config file and the restart irssi, thus letting irssi generate its *default* configuration:

```
mv -v $HOME/.irssi/config $HOME/.irssi/config_bak
```

This may not help but it is a logical first step...

---

