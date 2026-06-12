---
title: "Is there any variable (that I can use in C) that contains the machine's IP?"
date: 2007-11-07
forum: Programming Talk
---

### Post by raul_ on 2007-11-07
I'm trying to create a simple client/server program, but on the server side, I need to know what is the ip, so the client can connect. How can I assign that value to a variable?

I found some code that references INADDR_ANY but it only returns 0. 

Thanks

---

### Post by dwhitney67 on 2007-11-07
Huh?  The server shouldn't tell the client what the IP is, the client should already know it (and the port to use)... otherwise how would it connect to the server?

If both the client and the server are on the same system, then the IP is 127.0.0.1, or easier yet, "localhost".

If the client is on a separate system, then the server's IP should be given to it as startup information.  For instance:

```
$ runClient -h serverHostIP -p serverPortNum
```

If you want to avoid using IP addresses, rely on the /etc/hosts file for storing aliases.

P.S.  On the server machine, you can run "/sbin/ifconfig" to determine what the system's assigned IP address is.

---

### Post by raul_ on 2007-11-08
Thank you for your response. That's not my question though. I want the server to print it's address so I know with which value I should call my client with :) it works fine with localhost, but I want to run my server on a remote machine. for example:

```

ssh user@some.machine.net
Password:

bashwhatever@somemachine: /.myserver
This machine's IP is 123.456.789

```

:)

---

### Post by Tuna-Fish on 2007-11-08
use ifconfig?

---

### Post by Zugzwang on 2007-11-08
I guess, Tuna-Fish's answer is the best, and that's mainly because there is no IP-address for the server, just one for each of its interfaces. So for example it can have a wireless connection and an ethernet connection, both with different IPs (although they *could* be connected to the same network). So there could only be a C-function that gives you the IP-address of a given interface. And for example Google gives me: 

[http://www.geekpage.jp/en/programming/linux-network/get-ipaddr.php](http://www.geekpage.jp/en/programming/linux-network/get-ipaddr.php)

However, what you might do is enumerate all interfaces and then print all of its IPs. But the easiest way is maybe by simply processing the output of ifconfig.

---

### Post by dwhitney67 on 2007-11-08
> **raul_ said:**
> Thank you for your response. That's not my question though. I want the server to print it's address so I know with which value I should call my client with :) it works fine with localhost, but I want to run my server on a remote machine. for example:

```

ssh user@some.machine.net
Password:

bashwhatever@somemachine: /.myserver
This machine's IP is 123.456.789

```

:)

Here's a kludge that I wrote recently for a project that I am supporting.  The use of ioctl() was too complicated to figure out in the time I had to complete the assignment, so I relied on system commands and file parsing.  Here's the code that you can snip-n-cut for your own purposes:

[PHP]...
      // to get the kernel version and architecture type
      utsname info;
      uname( &info );

      // to get the video chip-set and ifconfig information
      system( "/bin/grep -A 1 -i card0 /etc/X11/xorg.conf | /bin/grep Driver"
              "| /usr/bin/cut -d '\"' -f2 > /tmp/sysinfo" );

      system( "/sbin/ifconfig eth0 2> /dev/null"
              "| /bin/grep -m 1 addr: | /usr/bin/cut -d : -f2"
              "| /usr/bin/cut -d ' ' -f1 >> /tmp/sysinfo" );

      system( "/sbin/ifconfig eth0 2> /dev/null"
              "| /bin/grep -m 1 Bcast: | /usr/bin/cut -d : -f3"
              "| /usr/bin/cut -d ' ' -f1 >> /tmp/sysinfo" );

      system( "/sbin/ifconfig eth0 2> /dev/null"
              "| /bin/grep -m 1 Mask: | /usr/bin/cut -d : -f4 >> /tmp/sysinfo" );

      // read video chip set and ifconfig information from flat-file
      const std::string TBD( "unknown" );
      std::string video( TBD );
      std::string ipAddr( TBD );
      std::string broadcast( TBD );
      std::string netmask( TBD );
      std::string boardType( TBD );

      ifstream sysinfo( "/tmp/sysinfo" );

      if ( sysinfo )
      {
         if ( sysinfo.peek() != '\0' )
         {
            sysinfo >> video;
         }
         if ( sysinfo.peek() != '\0' )
         {
            sysinfo >> ipAddr;
         }
         if ( sysinfo.peek() != '\0' )
         {
            sysinfo >> broadcast;
         }
         if ( sysinfo.peek() != '\0' )
         {
            sysinfo >> netmask;
         }

         sysinfo.close();

         unlink( "/tmp/sysinfo" );
      }
[/PHP]

---

### Post by raul_ on 2007-11-08
Thanks :)

---

