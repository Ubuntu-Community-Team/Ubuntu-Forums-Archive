---
title: "PERL - Dumping output into a logfile."
date: 2007-08-08
forum: Programming Talk
---

### Post by misconfiguration on 2007-08-08
Hello all,

I'm currently writing a simple stop/start script in PERL for Apache and Tomcat, I could write a simple shell script like so;
```
echo "Stopping Tomcat..............."
/usr/local/tomcat/bin/shutdown.sh
echo "stopping Apache..............."
/usr/local/apache2/bin/apachectl stop
echo "Starting Tomcat..............."
/usr/local/tomcat/bin/startup.sh
echo "Waiting 20 seconds to start Apache..............."
sleep 20
echo "Starting Apache..............."
/usr/local/apache2/bin/apachectl start
```

Essentially I would be finished, but being an aspiring PERL scripter I'd like to be able to write something a little more fancy.

These boxes are Mission Critical and I'd like to see if and when even by WHOM executed the command and what time etc. So I wrote this;
 ```
       print "Restarting services Tomcat5 And Apache.......\n\n";
my $date =`date`;
@arr = "Apache", "Tomcat";
        print "Stopping Tomcat....\n";
system `/usr/local/tomcat/bin/shutdown.sh`;
        print ".....done\n";
        sleep 5;
        print "Stopping Apache\n";
system `/usr/sbin/apachectl stop`;
        print "Starting Tomcat....\n";
system `/usr/local/tomcat/bin/startup.sh`;
        sleep 20;
        print "......done\n";

# Start/Stop Apache.
        print "Starting Apache....\n";
system `/sbin/apachectl start`;
        sleep 5;
        print ".....done\n";
        print "The command was completed successfully by $ENV{USER}, on $date machine $ENV{HOSTNAME}\n\n";
```

**Now to my main questions..**

1.) I know how to open files etc, but how would I be able to open /var/log/httpd/error_log and dump the output of the last print statement to the log file.

2.) How would I be able to initiate a PERL script to execute on boot time like an init script?
I know I could dump it in rc.local but that's not soon enough.

Any help would be wonderful!

---

### Post by misconfiguration on 2007-08-08
I'm just going to do it the easy way.

system ` echo $ENV{USER}, $ENV{HOSTNAME} $ENV{DATE} >>log.file`;

---

### Post by slavik on 2007-08-09
no (to the bash thing you have there), here's sample code :)

```

open $log, "somelogfile" or die $!;

print $log "some crazy stuff happened\n";

```

basically, print is like fprintf (in C) where the first parameter is assumed to be STDOUT unless you give it a reference to another stream. :)

---

### Post by misconfiguration on 2007-08-09
Thanks for the suggestion but as I was digging through my PERL in a nutshell book last night I came up with this. 

I just did the bash command to get it done for now, these boxes are mission critical. 

open(LOGFILE, "/usr/httpd/error_log")
                   ||warn "Could not open /usr/httpd/error_log.\n";
open(DATA, ">>/usr/local/httpd/error_log" || die "Could not write to the log file\n";

Thanks for the reply man, I appreciate it. It seems to be pretty darn hard to find PERL help anymore besides the CPAN.

Sometimes you just need human interaction, lol.

---

### Post by slavik on 2007-08-09
well, my piece of code is similar to what you have with data, except mine clears the file (opens as write)

to change it, just do ">>somecrazylog" (like it is in your example. :)

---

### Post by misconfiguration on 2007-08-09
See I changed from yours because I couldn't get the data to write TO the log file, so what you mean is this?

open $log, "somelogfile" or die $!;

print $log >>"some crazy stuff happened\n";

Is this what you mean?

Sorry if I'm not understanding fully, I'm very new to PERL and just now getting into filehandles and regular expressions. 

Another thing that is odd, since $log isn't referenced how is PERL smart enough to know to store the input in the string, I didn't think scalers were able to store data like that.

Thanks for your reply's you're helping me a lot.

---

### Post by misconfiguration on 2007-08-09
```
#!/usr/sbin/perl -w
# Written by Nate dobbs
# Restart services and dump output into /var/log/httpd/error_log
        print "Restarting services Tomcat5 And Apache.......\n\n";
my $date =`date`;
my $env = "$ENV{USER}";
@app = ("Apache", "Tomcat");
@function = ("/usr/local/tomcat/bin/shutdown.sh", "/usr/local/tomcat/bin/startup.sh", "apachectl restart", "apachectl stop");
        print "Stopping $app[1]....\n";
system ($function[0]);
        print ".....done\n";
        sleep 5;
        print "Stopping $app[0]\n";
system ($function[3]);
        print "Starting $app[1]....\n";
system ($function[1]);
        sleep 20;
        print "......done\n";

# Start/Stop Apache.
        print "Starting $app[0]....\n";
system ($function[2]);
        sleep 5;
        print ".....done\n";
         open(httpd_log, ">>/var/log/httpd/error_log");
        print httpd_log "<===The /sbin/restart.pl script was run successfully by $env at $date===>\n\n";
         close httpd_log;

```


```
[root@oailxnfw2 sbin]# perl restart.pl
Restarting services Tomcat5 And Apache.......

Stopping Tomcat....
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/java/jdk1.5.0_12
Aug 9, 2007 12:55:23 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop:
java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
        at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
        at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
        at java.net.Socket.connect(Socket.java:519)
        at java.net.Socket.connect(Socket.java:469)
        at java.net.Socket.<init>(Socket.java:366)
        at java.net.Socket.<init>(Socket.java:179)
        at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:394)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:324)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:415)
.....done
Stopping Apache
[Thu Aug 09 12:55:28 2007] [warn] _default_ VirtualHost overlap on port 443, the first has precedence
[Thu Aug 09 12:55:28 2007] [warn] NameVirtualHost 10.90.2.146:80 has no VirtualHosts
Starting Tomcat....
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/java/jdk1.5.0_12
......done
Starting Apache....
[Thu Aug 09 12:55:31 2007] [warn] _default_ VirtualHost overlap on port 443, the first has precedence
[Thu Aug 09 12:55:31 2007] [warn] NameVirtualHost 10.90.2.146:80 has no VirtualHosts
httpd not running, trying to start
.....done

```

```
cat /var/log/httpd/error_log
<===The /sbin/restart.pl script was run successfully by root at Thu Aug  9 12:55:23 EDT 2007
===>

```

This is exactly what I needed, thanks for your help!

---

### Post by Mr. C. on 2007-08-09
It is generally a bad idea to have two processes write to the same file at the same time.  Your script has the apache error file open, as will apache, so you've created a race condition on who writes first.

MrC

---

### Post by slavik on 2007-08-09
> **Mr. C. said:**
> It is generally a bad idea to have two processes write to the same file at the same time.  Your script has the apache error file open, as will apache, so you've created a race condition on who writes first.

MrC
QFT!!!

you may want to create a named pipe and have apache output error to there and your script can read the named pipe and put the stuff into the error file and also print stuff itself whenever it needs/wants to

---

### Post by misconfiguration on 2007-08-13
This is why I posted in the forums; I'm not very familiar with programming practice, this is making learn a lot!

Another thing that I was thinking is this; 

Would it be best to go with hashes VS arrays?
key=Apache, value = array of apache fns.
HoH (hash of hashes)
%progs = ();
$progs{'Apache'}{'start'} = "cmd to start apache";
$progs{'Apache'}{'stop'} = "cmd to stop apache";

---

### Post by slavik on 2007-08-13
that can work, and seems extendible enough to add support for other things. :)

---

### Post by Mr. C. on 2007-08-13
Use the "logger" utility to send your start/stop entries to syslog's general messages or syslog file.  See:
```

man logger
man syslog
man syslog.conf
```

Use whatever data types (array, hash) that works best for you, and suits your needs.

MrC

---

### Post by misconfiguration on 2007-08-13
You guys rock, thank you!

---

