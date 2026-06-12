---
title: "Squid3 blocks all traffic"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by andrew_hansen on 2014-08-01
G'day all,

Firstly, apologies for such a basic question but I can't get this horse over the first hurdle.

I added squid to my little 14.04 server and configured a basic conf file as described at [https://help.ubuntu.com/14.04/serverguide/squid.html](https://help.ubuntu.com/14.04/serverguide/squid.html) so my conf file is:

```
http_port 8888
visible_hostname proxy
acl homenet src 192.168.1.0/24
http_access allow homenet
```

When I try to connect via the proxy I get a refused connection message.

What is the next step?

Ta,
A.

---

### Post by Dave.YNA on 2014-08-01
Are you trying to connect through the same machine or another on the network? If it is the same you might be connecting as 127.0.0.1 aka local host.

---

### Post by andrew_hansen on 2014-08-01
Thanks Dave,

No, it's another machine.  I have only configured it to  proxy http traffic and everything else is fine.  I just can't get anything through squid.

Ta,
A.

---

### Post by Lars Noodén on 2014-08-01
How are you configuring your clients to connect to Squid?  Have you opened port 8888 on the proxy using iptables or UFW?

---

### Post by SeijiSensei on 2014-08-01
From a client, use "telnet ip.of.the.server 8888" and see if you get a response.

---

### Post by andrew_hansen on 2014-08-01
Thanks Lars,

My test machine is connecting with Firefox which is  set to proxy http traffic only with the ip of the server and port 8888.   I have opened 8888 to all tcp traffic in both directions on the  firewall (iptables).
I know I'm missing something fundamental.

Thanks again,

---

### Post by andrew_hansen on 2014-08-01
I don't know if this tells you much but the response is:

andrew@desktop:~$ telnet 192.168.1.10 8888
Trying 192.168.1.10...
telnet: Unable to connect to remote host: Connection refused

Thanks for helping with my problem.

---

### Post by SeijiSensei on 2014-08-01
Is Squid actually running?  Did you run "sudo service squid3 start" or "restart"?

On the server, run the command "ps ax | grep squid"?  Do you see any entries?  Usually you should see something like
```

24441 ?        Ss     0:00 squid -f /etc/squid3/squid.conf
24444 ?        S    1802:17 (squid) -f /etc/squid3/squid.conf

```
The first line represents the "stub" or "parent" that runs with root privileges.  It spawns a child process, the second in the list, which is owned by the squid user and handles all the traffic.

---

### Post by andrew_hansen on 2014-08-02
I had wondered that.  I have been restarting squid and I get a process id but here's the output of the ps command:

 8644 ?        Ss     0:00 squid3 -sY -f /etc/squid3/squid.conf
 8646 ?        S      1:49 (squid-1) -sY -f /etc/squid3/squid.conf
 8647 ?        S      0:00 (logfile-daemon) /var/log/squid3/access.log

So squid is running.

It shouldn't be this hard.

Thanks again,

---

### Post by Lars Noodén on 2014-08-02
squid3 is running there.   What is it listening to?

```

sudo netstat -nltp | grep squid

```

That will show which port it is listening to.  If it is listening at port 8888, try telnet again but from the same host as squid3 is running on.

```

telnet 192.168.1.10 8888
telnet localhost 8888

```

---

### Post by andrew_hansen on 2014-08-02
Thanks Lars,

Interestingly the result of the netstat command is:

```
andrew@odin:~$ sudo netstat -nltp | grep squid
tcp6       0      0 :::3128                 :::*                    LISTEN      8646/(squid-1)  
andrew@odin:~$ 
```

I tried changing the proxy port on the clients and now I get an "Access Denied" response from Squid which I'm going to take as an improvement in my situation.

Trying to connect via telnet gives:

```
andrew@odin:~$ telnet 192.168.1.10 3128
Trying 192.168.1.10...
Connected to 192.168.1.10.
Escape character is '^]'.
^C
Connection closed by foreign host.
andrew@odin:~$ telnet localhost 3128
Trying ::1...
Connected to localhost.
Escape character is '^]'.
^C
Connection closed by foreign host.
andrew@odin:~$ 
```

... which I am also goint to take as an improvement.

Now my questions are why is squid on the wrong port and why is it denying access?

Thanks again,

---

### Post by andrew_hansen on 2014-08-04
A bit more info for folks.  Following a suggestion from the IT folks at work I shut squid down and restarted it from the command line.  This what happened:

```
andrew@odin:/etc/init$ sudo service squid3 stop
stop: Unknown instance: 
andrew@odin:/etc/init$ sudo service squid3 status
squid3 stop/waiting
andrew@odin:/etc/init$ /usr/sbin/squid3 -N -YC -f /etc/squid3/squid.conf
2014/08/04 17:13:40| ALERT: setgid: (1) Operation not permitted
WARNING: Cannot write log file: /var/log/squid3/cache.log
/var/log/squid3/cache.log: Permission denied
         messages will be sent to 'stderr'.
2014/08/04 17:13:40| ALERT: setgid: (1) Operation not permitted
2014/08/04 17:13:40| ALERT: setgid: (1) Operation not permitted
WARNING: Cannot write log file: /var/log/squid3/cache.log
/var/log/squid3/cache.log: Permission denied
         messages will be sent to 'stderr'.
2014/08/04 17:13:40| WARNING: Closing open FD    2
2014/08/04 17:13:40| Starting Squid Cache version 3.3.8 for i686-pc-linux-gnu...
2014/08/04 17:13:40| Process ID 8912
2014/08/04 17:13:40| Process Roles: master worker
2014/08/04 17:13:40| With 65536 file descriptors available
2014/08/04 17:13:40| Initializing IP Cache...
2014/08/04 17:13:40| DNS Socket created at [::], FD 4
2014/08/04 17:13:40| DNS Socket created at 0.0.0.0, FD 5
2014/08/04 17:13:40| Warning: Could not find any nameservers. Trying to use localhost
2014/08/04 17:13:40| Please check your /etc/resolv.conf file
2014/08/04 17:13:40| or use the 'dns_nameservers' option in squid.conf.
2014/08/04 17:13:40| Logfile: opening log daemon:/var/log/squid3/access.log
2014/08/04 17:13:40| Logfile Daemon: opening log /var/log/squid3/access.log
2014/08/04 17:13:40| ALERT: setgid: (1) Operation not permitted
2014/08/04 17:13:40| WARNING: no_suid: setuid(0): (1) Operation not permitted
2014/08/04 17:13:40| ALERT: setgid: (1) Operation not permitted
2014/08/04 17:13:40| WARNING: no_suid: setuid(0): (1) Operation not permitted
fopen: Permission denied
2014/08/04 17:13:40| Unlinkd pipe opened on FD 11
2014/08/04 17:13:40| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2014/08/04 17:13:40| Store logging disabled
2014/08/04 17:13:40| Swap maxSize 102400 + 262144 KB, estimated 28041 objects
2014/08/04 17:13:40| Target number of buckets: 1402
2014/08/04 17:13:40| Using 8192 Store buckets
2014/08/04 17:13:40| Max Mem  size: 262144 KB
2014/08/04 17:13:40| Max Swap size: 102400 KB
2014/08/04 17:13:40| ERROR opening swap log /var/spool/squid3/swap.state: (13) Permission denied
2014/08/04 17:13:40| ALERT: setgid: (1) Operation not permitted
FATAL: UFSSwapDir::openLog: Failed to open swap log.
Squid Cache (Version 3.3.8): Terminated abnormally.
CPU Usage: 0.036 seconds = 0.020 user + 0.016 sys
Maximum Resident Size: 55824 KB
Page faults with physical i/o: 13
andrew@odin:/etc/init$
```

There seem to be a lot of warnings and denied's for something that is assumed to be running normally.

Can anyone help unravel this?

Cheers,
A.

---

### Post by Lars Noodén on 2014-08-04
Usually squid3 on Ubuntu runs as the [user and group 'proxy'](http://www.squid-cache.org/Doc/config/cache_effective_user/), unless you changed it to something else.  Either way, squid needs to be launched as root so it can assume the new user and group.  

```

sudo /usr/sbin/squid3 -N -YC -f /etc/squid3/squid.conf

```

It might be more useful to see what you have in the configuration file.

```

grep -P '^\s*\w' /etc/squid3/squid.conf 

```

The directive [http_port](http://www.squid-cache.org/Doc/config/http_port/) is the main one to look for.  As you show in the output in #11 above squid3 is running but listening on 3128.

---

### Post by andrew_hansen on 2014-08-05
Thanks Lars,

Starting squid from sudo got rid of the errors.  Squid is still listening on 3128 as shown:

```
andrew@odin:/var/log/squid3$ sudo netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.10:53         0.0.0.0:*               LISTEN      892/named       
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      892/named       
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      892/named       
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      9387/smbd       
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      969/mysqld      
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      9387/smbd       
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      795/sshd        
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1359/perl       
tcp6       0      0 :::53                   :::*                    LISTEN      892/named       
tcp6       0      0 :::3128                 :::*                    LISTEN      8646/(squid-1)  
tcp6       0      0 ::1:953                 :::*                    LISTEN      892/named       
tcp6       0      0 :::443                  :::*                    LISTEN      6829/apache2    
tcp6       0      0 :::445                  :::*                    LISTEN      9387/smbd       
tcp6       0      0 :::139                  :::*                    LISTEN      9387/smbd       
tcp6       0      0 :::2222                 :::*                    LISTEN      795/sshd        
tcp6       0      0 :::80                   :::*                    LISTEN      6829/apache2  
```  


I'm not sure that squid being in parentheses is right but I really don't know.

The conf file as per your instruction is:

```
andrew@odin:/var/log/squid3$ grep -P '^\s*\w' /etc/squid3/squid.conf
acl localnet src 192.168.0.0/16    # RFC1918 possible internal network
acl SSL_ports port 443
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl CONNECT method CONNECT
http_access allow !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost manager
http_access deny manager
http_access deny to_localhost
http_access allow localnet
http_access allow localhost
http_port 8888
    cache_dir ufs /var/spool/squid3 100 16 256
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320
cache_effective_user proxy
visible_hostname odin_proxy
dns_nameservers 192.168.1.1
cache_effective_group proxy
andrew@odin:/var/log/squid3$ 
```

Sadly I'm beginning to wonder if this is not config issue but rather a gremlin in my version of Squid on my Ubuntu server.

Thanks again,
A.

---

### Post by Lars Noodén on 2014-08-05
The only thing that might be a little odd that I can see is that it is listening only using IPv6.  Since you were trying to contact it via an IPv4 address maybe you should have it explicitly listen on IPv4.  

```

http_port 0.0.0.0:8888

```

But I still can't see where port 3128 is coming from.  Is there another, older squid configuration file lying around there?

By the way, which version of squid3 do you have?

```

apt-cache policy squid3

```

---

### Post by andrew_hansen on 2014-08-06
G'day Lars,

Thanks for your ongoing efforts.

I saw the IPv6 thing too but I read somewhere that Squid3 onwards defaults to IPv6 and then picks up IPv4 subsequently ... or something like that.

Anyway, I changed the http_port entry from:

```
http_port 8888
```

to:

```
http_port 0.0.0.0:8888
```

and restarted squid but again no change since it's not reading the config file (apparently).

I looked around for other config files related to Squid and found /etc/init/squid3.conf which is the startup config that points to /etc/squid3/squid.conf for the config file anyway.  For interest here is that file:

```
# squid - SQUID HTTP proxy-cache
#

description     "HTTP proxy-cache"
author          "Chuck Short <zulcss@ubuntu.com>"

# The second "or" condition is to start squid in case it failed to start
# because no real interface was there.
start on runlevel [2345]
stop on runlevel [!2345]

respawn
normal exit 0

env CONFIG="/etc/squid3/squid.conf"
env SQUID_ARGS="-YC"

pre-start script
        /lib/init/apparmor-profile-load usr.sbin.squid3
        if [ -f /etc/default/squid3 ]; then
                . /etc/default/squid3
        fi

        find_cache_dir () {
                w="     " # space tab
                res=`sed -ne '
                        s/^'$1'['"$w"']\+[^'"$w"']\+['"$w"']\+\([^'"$w"']\+\).*$/\1/p;
                        t end;
                        d;
                        :end q' < $CONFIG`
                [ -n "$res" ] || res=$2
                echo "$res"
        }

        find_cache_type () {
          w="   " # space tab
          res=`sed -ne '
            s/^'$1'['"$w"']\+\([^'"$w"']\+\).*$/\1/p;
            t end;
            d;
            :end q' < $CONFIG`
          [ -n "$res" ] || res=$2
          echo "$res"
        }

        cache_dir=`find_cache_dir cache_dir`
        cache_type=`find_cache_type cache_dir`

        if [ "$cache_type" = "coss" -a -d "$cache_dir" -a ! -f "$cache_dir/stripe" ] ||
           [ "$cache_type" != "coss" -a -d "$cache_dir" -a ! -d "$cache_dir/00" ]
        then
                /usr/sbin/squid3 $SQUID_ARGS -z -f $CONFIG
        fi
end script

script
        if [ -f /etc/default/squid3 ]; then
                . /etc/default/squid3
        fi

        umask 027
        ulimit -n 65535
        exec /usr/sbin/squid3 -N $SQUID_ARGS -f $CONFIG
end script
```

I've got a few other squid.conf.???? files with previous attempts at a config but 

```
find / -name "squid.conf"
```

only brings up one squid.conf in /etc/squid3/ right where it is supposed to be.

In answer to your question about squid version:


```
andrew@odin:/var/log/squid3$ sudo apt-cache policy squid3
squid3:
  Installed: 3.3.8-1ubuntu6
  Candidate: 3.3.8-1ubuntu6
  Version table:
 *** 3.3.8-1ubuntu6 0
        500 http://au.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
andrew@odin:/var/log/squid3$ 
```

I wish I could just fast forward and see how this turns out.

Thanks again,
A.

---

### Post by Lars Noodén on 2014-08-09
I have the same version of Squid and Ubuntu but cannot duplicate your error.  I'm still suspecting some kind of error in your configuration file.  Have you checked it to be sure?

```

squid3 -k parse

```

Otherwise I'm at a loss as what to try next.

---

### Post by andrew_hansen on 2014-08-11
G'day Lars,

```
andrew@odin:~$ sudo squid3 -k parse
2014/08/10 18:44:06| Startup: Initializing Authentication Schemes ...
2014/08/10 18:44:06| Startup: Initialized Authentication Scheme 'basic'
2014/08/10 18:44:06| Startup: Initialized Authentication Scheme 'digest'
2014/08/10 18:44:06| Startup: Initialized Authentication Scheme 'negotiate'
2014/08/10 18:44:06| Startup: Initialized Authentication Scheme 'ntlm'
2014/08/10 18:44:06| Startup: Initialized Authentication.
2014/08/10 18:44:06| Processing Configuration File: /etc/squid3/squid.conf (depth 0)
2014/08/10 18:44:06| Processing: acl localnet src 192.168.0.0/16    # RFC1918 possible internal network
2014/08/10 18:44:06| Processing: acl SSL_ports port 443
2014/08/10 18:44:06| Processing: acl Safe_ports port 80        # http
2014/08/10 18:44:06| Processing: acl Safe_ports port 21        # ftp
2014/08/10 18:44:06| Processing: acl Safe_ports port 443        # https
2014/08/10 18:44:06| Processing: acl Safe_ports port 70        # gopher
2014/08/10 18:44:06| Processing: acl Safe_ports port 210        # wais
2014/08/10 18:44:06| Processing: acl Safe_ports port 1025-65535    # unregistered ports
2014/08/10 18:44:06| Processing: acl Safe_ports port 280        # http-mgmt
2014/08/10 18:44:06| Processing: acl Safe_ports port 488        # gss-http
2014/08/10 18:44:06| Processing: acl Safe_ports port 591        # filemaker
2014/08/10 18:44:06| Processing: acl Safe_ports port 777        # multiling http
2014/08/10 18:44:06| Processing: acl CONNECT method CONNECT
2014/08/10 18:44:06| Processing: http_access allow !Safe_ports
2014/08/10 18:44:06| Processing: http_access deny CONNECT !SSL_ports
2014/08/10 18:44:06| Processing: http_access allow localhost manager
2014/08/10 18:44:06| Processing: http_access deny manager
2014/08/10 18:44:06| Processing: http_access deny to_localhost
2014/08/10 18:44:06| Processing: http_access allow localnet
2014/08/10 18:44:06| Processing: http_access allow localhost
2014/08/10 18:44:06| Processing: http_port 0.0.0.0:8888
2014/08/10 18:44:06| Processing: cache_dir ufs /var/spool/squid3 100 16 256
2014/08/10 18:44:06| Processing: coredump_dir /var/spool/squid3
2014/08/10 18:44:06| Processing: refresh_pattern ^ftp:        1440    20%    10080
2014/08/10 18:44:06| Processing: refresh_pattern ^gopher:    1440    0%    1440
2014/08/10 18:44:06| Processing: refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
2014/08/10 18:44:06| Processing: refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
2014/08/10 18:44:06| Processing: refresh_pattern .        0    20%    4320
2014/08/10 18:44:06| Processing: cache_effective_user proxy
2014/08/10 18:44:06| Processing: visible_hostname odin_proxy
2014/08/10 18:44:06| Processing: dns_nameservers 192.168.1.1
2014/08/10 18:44:06| Processing: cache_effective_group proxy
andrew@odin:~$ 

```

I don't see anything unusual here so I assume it's all OK.

I think at this point it's time to see if I can scrub Squid from the system and try a reinstall.  If that doesn't work I'll have to consider how much I need a proxy server.

Thanks again for all your time and effort.

Cheers,

---

### Post by andrew_hansen on 2014-08-15
The final chapter in this saga is this.

I scrubbed the system clean of all squid and for no other reason than I had a bit of time I re-installed.  The difference was that originally I installed from my Webmin interface and Webmin ran automated apt-get scripts to install Squid.  This time I did it all manually for the CLI.  Now the netstat command shows squid listening on the correct port and devices on the LAN can connect through the proxy.

I have no idea why the "Webmin" install of Squid should have been able to pass every diagnostic test and still not work but the take home message is "install everything manually".

Thanks to all who contributed.

Cheers,

---

