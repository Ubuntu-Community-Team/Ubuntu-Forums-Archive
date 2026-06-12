---
title: "Howto: Fix any RNDC problems durind DNS instalation/configuration"
date: 2010-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by martis on 2010-08-01
Hi guys!
Once and for all I want to help you solve all problems that connected with RNDC during *bind9*/*named* setup.

Many people and so do I during setup of DNS server on Ubuntu have encountered a problem that look like this when you trying to startup DNS:
> * Stopping domain name service… bind9
rndc: connect failed: 127.0.0.1#953: connection refused
…done.
* Starting domain name service… bind9
There are dozens of problems that can cause this output on DNS server restart failure. I'll try to categorize them and give a unified solution.

[SIZE="4"]**Prologue**[/SIZE]

There are many solutions on the WEB. Many of them seems similar and close to others and many times the symptom of the problem is something different. After I have read and tried approximately 8 of different solutions that didn't helped me. I spend couple of days to eliminate the problem and learn how things actually works so I realizing what actually is happing.
In this tutorial I'm assuming that you are running as a **root**. Use > sudo su -To gain root pwer or prepend "*sudo*" before any command.

**Sources of the problem**[LIST]
[*]Incorrect permissions
[*]Bad **rndc-key** definition or usage
[*]Syntax errors in configuration files
[/LIST]
[SIZE="3"]**Incorrect permissions**[/SIZE]
In theory *bind9*/*named* _conf_igs should be readable for user who runs the daemon. Which is usually is **bind** and not root. By default if you installed DNS and DHCP daemons for your servers from Ubuntu's repository (ex: apt-get install bind9) you should not have problems with that.

But be sure that configuration files have the read access for group of user that going to start the daemon.

Check if you already have a **bind** user on your system
> cat /etc/passwd | grep bind
You should receive one line that should look like this:
> bind:x:103:108::/var/cache/bind:/bin/false
Use *dpkg* to reconfigure *bind9*. The first question is the user name to be used to run *bind9*.
> dpkg-reconfigure bind9 
Go through the wizard by answering positively on any question. 
Now check that in the [COLOR="Blue"]/etc/bind[/COLOR] any [COLOR="Blue"]*conf*[/COLOR] file have permissions like those: read and write for user **root** read only for group **bind** and others.
Use next command to check this.
> ls -l /etc/bind/*conf*
Output should begin like this:
> -rw-r--r-- root bind …
-rw-r--r-- root bind …
-rw-r--r-- root bind …
If some permissions are wrong use next command to fix it:
> chown root:bind /etc/bind/*conf* ; chmod 644 /etc/bind/*conf*
[SIZE="3"]**Definition and usage of rndc-key**[/SIZE]

There are several places where you can define **rndc-key** or override it or include it.
The best is to have only one file for **rndc-key** definition which is [COLOR="Blue"]/etc/bind/rndc.key[/COLOR] and it should have only one statement – **key** which look like that:
> [FONT="Courier New"]key "rndc-key" {
     algorithm hmac-md5;
     secret "SOmeSeCretHerE123+456+E==";
};[/FONT]
You may use *rndc-confgen* command to produce one. For example:
> rndc-confgen > /etc/bind/rndc.key
**PLEASE NOTE:**
[LIST]
[*]It seems that *rndc-confgen* uses [COLOR="Blue"]/dev/random[/COLOR] device to produce secret for the key. It is strong generator for the random data but some time need user interaction to collect garbage data for the seed. If you run command mentioned above and it seems that it stuck just hit some buttons on the keyboard until it finishes. Matter of couple seconds.
[*]*rndc-confgen* used to generate a [COLOR="Blue"]rndc.conf[/COLOR] and we don't want [COLOR="Blue"]rndc.conf[/COLOR] we want [COLOR="Blue"]rndc.key[/COLOR] because *named* likes [COLOR="Blue"]rndc.key[/COLOR] and don't love [COLOR="Blue"]rndc.conf[/COLOR] please don't ask me why.
[/LIST]
If you used *rndc-confgen* to produce [COLOR="Blue"]rndc.key[/COLOR] as mentioned above you must use your text editor to remove any line before and after **key** definition statement.
You must include [COLOR="Blue"]rndc.key[/COLOR] in [COLOR="Blue"]named.conf[/COLOR]. Just use your text editor again to add this line at the end of the file [COLOR="Blue"]/etc/bind/named.conf[/COLOR]:
> [FONT="Courier New"]#include "/etc/bind/rndc.key"[/FONT]
It is optional and not bad to include in [COLOR="Blue"]/etc/bind/named.conf[/COLOR] **controls** statement that looks like this:
> [FONT="Courier New"]controls {
	inet 127.0.0.1 port 953
		allow {127.0.0.1;} keys { "rndc-key"; };
};[/FONT]
And of course don't forget the permissions issue. If you configured *bind9* daemon to run as user **bind** you should set permissions for our [COLOR="Blue"]rndc.key[/COLOR] file:
> chown root:bind /etc/bind/rndc.key ; chmod 644 /etc/bind/rndc.key
[SIZE="3"]**Syntax errors in _conf_iguration files**[/SIZE]

It's impossible to describe every possible error in the _conf_igs that can trigger described problem but usually most common problems that I found in was a syntax problem like missing semicolon ';' during customizing DNS forwarders and/or **rndc-key** editing because people used mixed tutorials which used different concepts or configurations.

Use this magic command combination to read log:
> tail /var/log/daemon | grep named
Output will tell you what was the source of the problem on last try of getting DNS up.

Here is an example (thanks to [Coogan]("http://ubuntuforums.org/member.php?u=14016")'s post on the thread “[Howto: Setup a DNS server with bind9]("http://ubuntuforums.org/showthread.php?t=236093&page=2")”) of what you'll see:
> Nov 21 21:59:47 localhost named[10645]: starting bind9 9.3.2 -u bind9
Nov 21 21:59:47 localhost named[10645]: found 1 CPU, using 1 worker thread
Nov 21 21:59:47 localhost named[10645]: loading configuration from '/etc/bind/named.conf'
Nov 21 21:59:47 localhost named[10645]: /etc/bind/named.conf:55: unknown option 'forwarders'
Nov 21 21:59:47 localhost named[10645]: loading configuration: failure
Nov 21 21:59:47 localhost named[10645]: exiting (due to fatal error)
You'll usually see that problem described on the next line to “**loading configuration from …**”
It will tell you filename and line number within file that was a source of  the fatal error.

[SIZE="4"]**Epilogue**[/SIZE]

In this case of problem the best is to read log, look at the place where error occurred and try to fix it by yourself rather then find and mix different solutions from different tutorials and different sources. Use this simple algorithm until you'll fix your problem

[LIST=1]
[*]Read the log from command: tail /var/log/daemon | grep named
[*]Try to fix what log tells you to fix
[*]Restart DNS server by using command: /etc/init.d/bind9 restart
[*]If problem still exists go to step one
[/LIST]

It took me 11 cycles of this algorithm to fix all my problems. So **Never give up!**

---

### Post by dmizer on 2010-08-08
Courtesy bump.

Thanks for posting this.

---

