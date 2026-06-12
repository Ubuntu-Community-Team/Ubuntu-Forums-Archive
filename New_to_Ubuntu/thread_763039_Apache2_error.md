---
title: "Apache2 error"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Alessandro Allegri on 2008-04-22
Hi everybody. I hope someone can help me with this one.
I tried looking around but looks like the solutions already posted don't work for my case.

Ubuntu 7.10, apache2, working fine until maybe a couple days ago. Don't know what happened then, but now apache2 isn't working anymore.
Trying to restart it, I get:

(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

I tried looking at /etc/apache2/ports.conf, and it says:

Listen 80
<IfModule mod_ssl.c>
    Listen 443
</IfModule>

And that's it. So... what could be wrong?
Thanks for any hint,
A.A

---

### Post by tjajab on 2008-04-22
To bind to ports lower than a certain value (1000 or so), you have to be root. So try sudo /etc/init.d/apache2 restart.

---

### Post by Alessandro Allegri on 2008-04-23
well, yes, I forgot to mention it but I did everything as root...

---

### Post by Oldsoldier2003 on 2008-04-23
what does your /etc/apache2/sites-avaialble/default file say? generally you do not need to edit ports conf...

also if you are running multiple virtual hosts listening to different ports default needs to be the one listening on 80 and if you have a site listening on for instance :8080 make it another, separate conf file and use a2ensite to enable it.

---

### Post by Alessandro Allegri on 2008-04-23
And this is the output to
```
more /var/log/apache2/error.log:
```

```
[Sun Apr 20 07:37:24 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming norm
al operations
[Sun Apr 20 15:31:19 2008] [notice] caught SIGWINCH, shutting down gracefully

```

This is the latest modified error.file, and in spite of all attempts of reviving apache2, no activity is reported in it later than apr 20...

---

### Post by Alessandro Allegri on 2008-04-23
this is the /etc/apache2/sites-available/default file:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by Oldsoldier2003 on 2008-04-23
everything looks to be in order. have you done a netstat
 to see if for some insane reason another service has hijacked port 80?

---

### Post by Alessandro Allegri on 2008-04-23
well, netstat gives an extremely long answer... what do I look for exactly?

---

### Post by Oldsoldier2003 on 2008-04-23
actually let me show you an easier way:

```
sudo lsof -i :80

COMMAND   PID     USER   FD   TYPE DEVICE SIZE NODE NAME
apache2 28566     root    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 28572 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 28573 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 28574 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 28575 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 28576 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 29572 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 29578 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
apache2 29593 www-data    4u  IPv6  53514       TCP *:www (LISTEN)
```

lsof should be installed on your server, I run an etch Server but i've verified that lsof works on Ubuntu as well. if you get a command not found then
```
sudo apt-get install lsof
```

---

### Post by Alessandro Allegri on 2008-04-23
this is weird...
```

alessandro@alluntu:~$ lsof -i :80
COMMAND    PID       USER   FD   TYPE DEVICE SIZE NODE NAME
flock-bin 7925 alessandro   11u  IPv4  85281       TCP 192.168.1.3:49813->8.6.19.68:www (ESTABLISHED)
flock-bin 7925 alessandro   33u  IPv4  87505       TCP 192.168.1.3:46000->eh-in-f121.google.com:www (ESTABLISHED)
flock-bin 7925 alessandro   66u  IPv4  87515       TCP 192.168.1.3:58897->79.140.81.48:www (ESTABLISHED)
flock-bin 7925 alessandro   71u  IPv4  85652       TCP 192.168.1.3:49896->8.6.19.68:www (ESTABLISHED)

```

---

### Post by Oldsoldier2003 on 2008-04-23
> **Alessandro Allegri said:**
> this is weird...
```

alessandro@alluntu:~$ lsof -i :80
COMMAND    PID       USER   FD   TYPE DEVICE SIZE NODE NAME
flock-bin 7925 alessandro   11u  IPv4  85281       TCP 192.168.1.3:49813->8.6.19.68:www (ESTABLISHED)
flock-bin 7925 alessandro   33u  IPv4  87505       TCP 192.168.1.3:46000->eh-in-f121.google.com:www (ESTABLISHED)
flock-bin 7925 alessandro   66u  IPv4  87515       TCP 192.168.1.3:58897->79.140.81.48:www (ESTABLISHED)
flock-bin 7925 alessandro   71u  IPv4  85652       TCP 192.168.1.3:49896->8.6.19.68:www (ESTABLISHED)

```

did you ssh to the server and run the command? another command that will be useful is
```
sudo netstat -a |grep LISTEN |grep -v unix
```
again run it from the server. I just want to see if there is something else using prot 80 on your server. My next thought would be to reboot the server, though i don't think its the answer a restart has fixed issues on Ubuntu server for me in the past.

---

### Post by Alessandro Allegri on 2008-04-23
plus, if I close my flock browser, lsof -i :80 gives a blank answer.
I then try restarting apache2, but the answer is still the same:

```

 * Restarting web server apache2                                                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by Alessandro Allegri on 2008-04-23
> **Oldsoldier2003 said:**
> did you ssh to the server and run the command?
sorry? :-) I just went to terminal and run it from there...

```

alessandro@alluntu:~$ sudo netstat -a |grep LISTEN |grep -v unix
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:1025                  *:*                     LISTEN     
tcp        0      0 *:imaps                 *:*                     LISTEN     
tcp        0      0 *:pop3s                 *:*                     LISTEN     
tcp        0      0 *:3140                  *:*                     LISTEN     
tcp        0      0 *:46628                 *:*                     LISTEN     
tcp        0      0 *:loc-srv               *:*                     LISTEN     
tcp        0      0 *:5000                  *:*                     LISTEN     
tcp        0      0 *:58089                 *:*                     LISTEN     
tcp        0      0 *:nameserver            *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:3372                  *:*                     LISTEN     
tcp        0      0 *:pop3                  *:*                     LISTEN     
tcp        0      0 *:imap2                 *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 *:webmin                *:*                     LISTEN     
tcp        0      0 localhost:50001         *:*                     LISTEN     
tcp        0      0 *:6129                  *:*                     LISTEN     
tcp        0      0 *:ssmtp                 *:*                     LISTEN     
tcp        0      0 *:38642                 *:*                     LISTEN     
tcp        0      0 *:5554                  *:*                     LISTEN     
tcp        0      0 *:27347                 *:*                     LISTEN     
tcp        0      0 *:17300                 *:*                     LISTEN     
tcp        0      0 *:ftp                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:3127                  *:*                     LISTEN     
tcp        0      0 *:2103                  *:*                     LISTEN     
tcp        0      0 *:nessus                *:*                     LISTEN     
tcp        0      0 *:eklogin               *:*                     LISTEN     
tcp        0      0 *:2745                  *:*                     LISTEN     
tcp        0      0 localhost:smtp          *:*                     LISTEN     
tcp        0      0 *:2107                  *:*                     LISTEN     
tcp        0      0 *:https                 *:*                     LISTEN     
tcp        0      0 *:imap3                 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 *:1023                  *:*                     LISTEN     
tcp6       0      0 *:5900                  *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN     
tcp6       0      0 *:ipp                   *:*                     LISTEN     

```
don't know what you mean "run it from the server"... my laptop IS the server.

---

### Post by Oldsoldier2003 on 2008-04-23
ok if you are running it from the same machine then disregardthe whole run from the server thing :)

from what i can see from the grep you have webmin and www listening to ports. Since apache isnt running, you either have another http daemon running or have a stale pid for apache ( thinking out loud here) can you to a ps aux and see if you see anything strange?

---

### Post by Alessandro Allegri on 2008-04-23
well first of all thanks for helpin so much.
now ps aux gives:

```

alessandro@alluntu:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.6  0.1   2948  1852 ?        Ss   19:22   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   19:22   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        SN   19:22   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S<   19:22   0:00 [watchdog/0]
root         5  0.1  0.0      0     0 ?        S<   19:22   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   19:22   0:00 [khelper]
root        25  0.0  0.0      0     0 ?        S<   19:22   0:00 [kblockd/0]
root        26  0.0  0.0      0     0 ?        S<   19:22   0:00 [kacpid]
root        27  0.0  0.0      0     0 ?        S<   19:22   0:00 [kacpi_notify]
root       128  0.0  0.0      0     0 ?        S<   19:22   0:00 [kseriod]
root       147  0.0  0.0      0     0 ?        S    19:22   0:00 [pdflush]
root       148  0.0  0.0      0     0 ?        S    19:22   0:00 [pdflush]
root       149  0.0  0.0      0     0 ?        S<   19:22   0:00 [kswapd0]
root       199  0.0  0.0      0     0 ?        S<   19:22   0:00 [aio/0]
root      1239  0.0  0.0      0     0 ?        S<   19:22   0:00 [ksnapd]
root      1999  0.0  0.0      0     0 ?        S<   19:22   0:00 [ksuspend_usbd]
root      2000  0.0  0.0      0     0 ?        S<   19:22   0:00 [khubd]
root      2047  0.0  0.0      0     0 ?        S<   19:22   0:00 [ata/0]
root      2048  0.0  0.0      0     0 ?        S<   19:22   0:00 [ata_aux]
root      2085  0.0  0.0      0     0 ?        S<   19:22   0:00 [khpsbpkt]
root      2185  0.0  0.0      0     0 ?        S<   19:22   0:00 [scsi_eh_0]
root      2186  0.0  0.0      0     0 ?        S<   19:22   0:00 [scsi_eh_1]
root      2224  0.0  0.0      0     0 ?        S<   19:22   0:00 [knodemgrd_0]
root      2393  0.0  0.0      0     0 ?        S<   19:22   0:00 [kjournald]
root      2723  0.1  0.1   3060  1408 ?        S<s  19:22   0:00 /sbin/udevd --d
root      3607  0.0  0.0      0     0 ?        S<   19:22   0:00 [pccardd]
root      3663  0.0  0.0      0     0 ?        S<   19:22   0:00 [kpsmoused]
root      4533  0.0  0.0      0     0 ?        S<   19:23   0:00 [kjournald]
root      4536  0.0  0.0   2552   956 ?        Ss   19:23   0:00 /sbin/mount.ntf
daemon    4665  0.0  0.0   1812   504 ?        Ss   19:23   0:00 /sbin/portmap
statd     4684  0.0  0.0   1880   720 ?        Ss   19:23   0:00 /sbin/rpc.statd
root      4874  0.0  0.0   1692   516 tty4     Ss+  19:23   0:00 /sbin/getty 384
root      4875  0.0  0.0   1696   520 tty5     Ss+  19:23   0:00 /sbin/getty 384
root      4876  0.0  0.0   1756   560 ?        Ss   19:23   0:00 /bin/sh /etc/in
root      4878  0.0  0.0   1696   516 tty2     Ss+  19:23   0:00 /sbin/getty 384
root      4880  0.0  0.0   1692   516 tty3     Ss+  19:23   0:00 /sbin/getty 384
root      4881  0.0  0.0   1692   516 tty1     Ss+  19:23   0:00 /sbin/getty 384
root      4882  0.0  0.0   1692   516 tty6     Ss+  19:23   0:00 /sbin/getty 384
root      5077  0.0  0.1   2432  1320 ?        Ss   19:23   0:00 /usr/sbin/acpid
root      5106  0.0  0.0      0     0 ?        S<   19:23   0:00 [kondemand/0]
syslog    5177  0.0  0.0   1912   700 ?        Ss   19:23   0:00 /sbin/syslogd -
root      5230  0.0  0.0   1836   536 ?        S    19:23   0:00 /bin/dd bs 1 if
klog      5232  0.0  0.1   2508  1376 ?        Ss   19:23   0:00 /sbin/klogd -P
104       5253  0.1  0.1   2904  1148 ?        Ss   19:23   0:00 /usr/bin/dbus-d
root      5269  0.0  0.1  12564  2036 ?        Ssl  19:23   0:00 /usr/sbin/Netwo
root      5283  0.0  0.1   3280  1276 ?        Ss   19:23   0:00 /usr/sbin/Netwo
root      5296  0.0  0.0   3084   812 ?        Ss   19:23   0:00 /usr/bin/system
root      5297  0.0  0.1   2772  1252 ?        S    19:23   0:00 dbus-daemon --s
108       5316  0.2  0.3   5628  3728 ?        Ss   19:23   0:00 /usr/sbin/hald
root      5317  0.0  0.0   3092  1024 ?        S    19:23   0:00 hald-runner
108       5358  0.0  0.0   2160   892 ?        S    19:23   0:00 hald-addon-keyb
108       5360  0.0  0.0   2164   892 ?        S    19:23   0:00 hald-addon-keyb
108       5361  0.0  0.0   2160   888 ?        S    19:23   0:00 hald-addon-keyb
108       5362  0.0  0.0   2160   888 ?        S    19:23   0:00 hald-addon-keyb
108       5365  0.0  0.0   2164   880 ?        S    19:23   0:00 hald-addon-acpi
108       5366  0.0  0.0   2160   888 ?        S    19:23   0:00 hald-addon-keyb
root      5409  0.0  0.1  13352  1684 ?        Ss   19:23   0:00 /usr/sbin/gdm
root      5412  0.0  0.2  13812  3060 ?        S    19:23   0:00 /usr/sbin/gdm
root      5419  1.0  2.2  29748 22924 tty7     SLs+ 19:23   0:01 /usr/bin/X :0 -
108       5420  0.0  0.1   3264  1184 ?        S    19:23   0:00 hald-addon-stor
root      5452  0.0  0.0   5284   972 ?        Ss   19:23   0:00 /usr/sbin/sshd
avahi     5473  0.0  0.1   2732  1400 ?        Ss   19:23   0:00 avahi-daemon: r
avahi     5474  0.0  0.0   2732   456 ?        Ss   19:23   0:00 avahi-daemon: c
root      5524  0.0  0.2   5964  2448 ?        Ss   19:23   0:00 /usr/sbin/cupsd
virtual   5781  3.6  6.0  64952 62380 ?        Ss   19:23   0:03 /usr/sbin/clamd
clamav    5873  0.3  0.1   3076  1164 ?        Ss   19:23   0:00 /usr/bin/freshc
121       6162  0.0  0.0   5488   888 ?        Ss   19:23   0:00 /usr/sbin/exim4
1000      6314  0.0  0.1  13432  1844 ?        SL   19:23   0:00 /usr/bin/gnome-
1000      6317  0.0  0.7  27684  7324 ?        Ssl  19:23   0:00 x-session-manag
root      6576  0.0  0.0      0     0 ?        S<   19:23   0:00 [irda_sir_wq]
1000      6637  0.0  0.0   4436   544 ?        Ss   19:23   0:00 /usr/bin/ssh-ag
1000      6638  0.0  0.0   4436   544 ?        Ss   19:23   0:00 /usr/bin/ssh-ag
root      6645  0.0  0.0   1756   528 ?        S    19:23   0:00 /bin/sh /usr/bi
mysql     6685  0.3  1.8 127700 18752 ?        Sl   19:23   0:00 /usr/sbin/mysql
root      6686  0.0  0.0   1676   548 ?        S    19:23   0:00 logger -p daemo
1000      6710  0.4  0.3   6744  4008 ?        S    19:23   0:00 /usr/lib/libgco
115       6771  0.0  0.2   6564  2992 ?        S    19:23   0:00 /usr/sbin/nepen
root      6773  0.0  0.0   1752   524 ?        S    19:23   0:00 /bin/sh -e /etc
1000      6789  0.0  0.1   2900  1064 ?        Ss   19:23   0:00 dbus-daemon --f
1000      6791  0.2  0.9  30244  9924 ?        Sl   19:23   0:00 /usr/lib/gnome-
1000      6798  0.1  0.3  39912  3128 ?        Ssl  19:23   0:00 /usr/lib/bonobo
1000      6802  1.6  0.5  16380  5836 ?        S    19:24   0:00 /usr/lib/vino/v
1000      6803  0.2  0.8  16432  9188 ?        S    19:24   0:00 /usr/bin/metaci
1000      6807  2.8  1.7  41800 17772 ?        D    19:24   0:01 gnome-panel --s
1000      6808  1.0  2.0  79788 21244 ?        S    19:24   0:00 nautilus --no-d
1000      6817  0.0  0.4  19476  4900 ?        Ss   19:24   0:00 gnome-volume-ma
1000      6824  0.0  0.2  16460  2688 ?        Ss   19:24   0:00 gnome-screensav
1000      6827  0.0  0.3   8724  3400 ?        S    19:24   0:00 /usr/lib/gnome-
1000      6828  0.0  0.6  19340  6864 ?        R    19:24   0:00 vino-session --
1000      6829  0.0  0.5  13284  5432 ?        S    19:24   0:00 bluetooth-apple
root      6835  0.3  1.2  41824 12480 ?        Sl   19:24   0:00 /usr/sbin/fires
1000      6839  0.2  1.1  32700 12352 ?        S    19:24   0:00 update-notifier
root      6846  0.3  0.3   6604  3808 ?        S    19:24   0:00 /usr/lib/libgco
1000      6851  0.6  0.6  27084  7080 ?        SNl  19:24   0:00 trackerd
1000      6854  0.2  1.1  22812 11720 ?        S    19:24   0:00 python /usr/sha
1000      6855  0.3  1.0  40520 11196 ?        S    19:24   0:00 nm-applet --sm-
1000      6985  0.1  0.8  49316  8520 ?        S    19:24   0:00 gnome-cups-icon
1000      7156  0.0  0.4   7492  4328 ?        S    19:24   0:00 ddclient - slee
1000      7198  0.2  0.7  22580  8144 ?        Rs   19:24   0:00 gnome-power-man
1000      7213  0.1  0.8  63140  9092 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7226  0.0  0.0   2664   892 ?        S    19:24   0:00 /usr/lib/nautil
1000      7232  0.3  1.0  29376 10908 ?        R    19:24   0:00 /usr/lib/notifi
1000      7295  2.8  1.5  56700 16368 ?        Sl   19:24   0:00 gnome-terminal
root      7301  0.0  0.3   6796  3708 ?        Ss   19:24   0:00 nessusd: waitin
root      7302  0.0  0.0   1676   416 ?        S    19:24   0:00 sleep 5
1000      7303  0.0  0.0   2668   736 ?        S    19:24   0:00 gnome-pty-helpe
1000      7304  3.2  0.3   6172  3552 pts/0    Ss   19:24   0:00 bash
1000      7323  3.6  1.1  33648 11436 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7325  1.0  0.6  19584  6992 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7332  1.6  0.8  20044  8396 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7334  3.3  1.1  32564 11572 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7336  3.0  0.9  31136  9520 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7338  3.3  1.0  33180 11200 ?        S    19:24   0:00 /usr/lib/gnome-
1000      7361  0.0  0.0   2624  1000 pts/0    R+   19:25   0:00 ps aux

```

... is there anything useful in this?

---

### Post by Oldsoldier2003 on 2008-04-23
nothing jumps out at me right away. look in /var/run and if there is an apache2.pid file delete that and try restarting apache. if there isn't one and you might try a complete restart of your computer.

---

### Post by Alessandro Allegri on 2008-04-23
gosh... :-(

no apache*.pid in /var/run (only and empty apache2 dir)

and no, restarting the computer won't help: apache2 is still not working.
should I try apt-removing-'n'-installing it?

---

### Post by Oldsoldier2003 on 2008-04-23
> **Alessandro Allegri said:**
> gosh... :-(

no apache*.pid in /var/run (only and empty apache2 dir)

and no, restarting the computer won't help: apache2 is still not working.
should I try apt-removing-'n'-installing it?

sounds like a pretty drastic measure. i am sure its something we've overlooked. you could give it a shot though since it won't wipe out the configs.

---

### Post by Alessandro Allegri on 2008-04-23
pretty drastic, but unfortunately not enough... :-(
did it but the problem persists.

---

### Post by Oldsoldier2003 on 2008-04-23
just a quick thought.. you running skype? I just stumbled across a post elsewhere where someone had the same problem and it was skype...

---

### Post by Oldsoldier2003 on 2008-04-23
basically the issue was that skype was using alternate listening ports and once if it was started prior to apache then apache couldnt start since Skype used 80 and 443. Wouldn't be an issue on a server but in a case where the server is also being used as a workstation (your case) it could become an issue. just a thought though. maybe we got lucky...

---

### Post by Alessandro Allegri on 2008-04-23
I occasionally use skype.
Not right now, anyway, nor since I restarted the pc...
I would tend to exclude that.

---

### Post by Oldsoldier2003 on 2008-04-23
> **Alessandro Allegri said:**
> I occasionally use skype.
Not right now, anyway, nor since I restarted the pc...
I would tend to exclude that.

another possibility is explored here: [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/669001969831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/669001969831)

Seems having listen defined in too many places could also lead to this problem.

---

### Post by Alessandro Allegri on 2008-04-23
ok, I think I got it.
first of all I set my ServerName as in the directions given by the site you sent me above.
then I did 

```

sudo lsof -i :80

```

getting
```

COMMAND    PID      USER   FD   TYPE DEVICE SIZE NODE NAME
nepenthes 6771 nepenthes   34u  IPv4  20759       TCP *:www (LISTEN)

```

then I did
```

sudo kill 6771
sudo /etc/init.d/apache2 restart

```

and everything went back to normal.
I have no idea why nepenthes got in apache's way. I think I'm going to uninstall it...

thank you so much for your support! nice being in trouble once in a (long) while, to find such helpful ubuntumates!

---

### Post by Oldsoldier2003 on 2008-04-23
> **Alessandro Allegri said:**
> ok, I think I got it.
first of all I set my ServerName as in the directions given by the site you sent me above.
then I did 

```

sudo lsof -i :80

```

getting
```

COMMAND    PID      USER   FD   TYPE DEVICE SIZE NODE NAME
nepenthes 6771 nepenthes   34u  IPv4  20759       TCP *:www (LISTEN)

```

then I did
```

sudo kill 6771
sudo /etc/init.d/apache2 restart

```

and everything went back to normal.
I have no idea why nepenthes got in apache's way. I think I'm going to uninstall it...

thank you so much for your support! nice being in trouble once in a (long) while, to find such helpful ubuntumates!

glad to have been of help, I just wish we would have got our brains wrapped around it sooner instead of taking so long.

---

