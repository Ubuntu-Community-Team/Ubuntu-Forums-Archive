---
title: "Can System IP be obtained in C++ code?"
date: 2007-10-24
forum: Programming Talk
---

### Post by dwhitney67 on 2007-10-24
I've been trying to obtain a system's IP address, netmask, and broadcast IP programatically using a combination of C++ and shell scripting.

I am limited to using basic shell scripting constructs because I am using the ash-shell.  It is similar to bash, but does not support the full set of features.

Here's what I got so far:

[PHP]
#include <string>
#include <fstream>
#include <iostream>
#include <unistd.h>   // for unlink()

...
         // attempt to obtain ifconfig information
         system( "echo -n 'IP ' > /tmp/sysinfo" );

         system( "/sbin/ifconfig eth0 2> /dev/null"
                 "| /bin/grep -m 1 addr: | /usr/bin/cut -d : -f2"
                 "| /usr/bin/cut -d ' ' -f1 >> /tmp/sysinfo;" );

         system( "echo -n 'BCAST ' >> /tmp/sysinfo" );

         system( "/sbin/ifconfig eth0 2> /dev/null"
                 "| /bin/grep -m 1 Bcast: | /usr/bin/cut -d : -f3"
                 "| /usr/bin/cut -d ' ' -f1 >> /tmp/sysinfo;" );

         system( "echo -n 'MASK ' >> /tmp/sysinfo" );

         system( "/sbin/ifconfig eth0 2> /dev/null"
                 "| /bin/grep -m 1 Mask: | /usr/bin/cut -d : -f4 >> /tmp/sysinfo;" );

         // read ifconfig information from flat-file
         std::string ipAddr;
         std::string broadcast;
         std::string netmask;
         std::string fieldID;

         std::ifstream sysinfo( "/tmp/sysinfo" );

         if ( sysinfo )
         {
            sysinfo >> fieldID >> ipAddr;
            sysinfo >> fieldID >> broadcast;
            sysinfo >> fieldID >> netmask;

            sysinfo.close();

            unlink( "/tmp/sysinfo" );
         }

         std::cout << "IP     = " << ipAddr    << std::endl;
         std::cout << "BCAST  = " << broadcast << std::endl;
         std::cout << "MASK   = " << netmask   << std::endl;
...[/PHP]

I've looked for a C-library function that can mimic or provides similar features as *ifconfig*, however I have come up empty.  Is there an easier way to get the system's ethernet information?

Btw, the code above works (under Linux), however only when the system is connected to the LAN.  If it is not connected, then *ifconfig* still reports eth0 info, but not the data I require, thus the contents in the flat-file is not built correctly --- and hence the reason I am seeking help!

P.S.  My system does not have Python, Perl, Bash, or even sed.  I am limited to C++, C, and Ash-shell script.

---

### Post by dwhitney67 on 2007-10-24
Ok, I got it work!  :)

However, is there and alternate way to get the system's IP info?

Here's the updated code:
[PHP]
#include <string>
#include <fstream>    // for ifstream
#include <iostream>   // for cout and endl
#include <unistd.h>   // for unlink()

int main()
{
         // attempt to obtain ifconfig information
         system( "/sbin/ifconfig eth0 2> /dev/null"
                 "| /bin/grep -m 1 addr: | /usr/bin/cut -d : -f2"
                 "| /usr/bin/cut -d ' ' -f1 > /tmp/sysinfo;" );

         system( "/sbin/ifconfig eth0 2> /dev/null"
                 "| /bin/grep -m 1 Bcast: | /usr/bin/cut -d : -f3"
                 "| /usr/bin/cut -d ' ' -f1 >> /tmp/sysinfo;" );

         system( "/sbin/ifconfig eth0 2> /dev/null"
                 "| /bin/grep -m 1 Mask: | /usr/bin/cut -d : -f4 >> /tmp/sysinfo;" );

         // read ifconfig information from flat-file
         const std::string TBD( "unknown" );
         std::string ipAddr( TBD );
         std::string broadcast( TBD );
         std::string netmask( TBD );

         std::ifstream sysinfo( "/tmp/sysinfo" );

         if ( sysinfo )
         {
            if ( sysinfo.peek() != '\0' ) sysinfo >> ipAddr;
            if ( sysinfo.peek() != '\0' ) sysinfo >> broadcast;
            if ( sysinfo.peek() != '\0' ) sysinfo >> netmask;

            sysinfo.close();

            unlink( "/tmp/sysinfo" );
         }

         std::cout << "IP     = " << ipAddr    << std::endl;
         std::cout << "BCAST  = " << broadcast << std::endl;
         std::cout << "MASK   = " << netmask   << std::endl;
}[/PHP]

---

### Post by AZzKikR on 2007-10-24
Can't you just create an Ash script (or whatever) to do all that...? And what 'features' do you mean which are missing from that shell?

---

### Post by dwhitney67 on 2007-10-24
I am using Ash-scripting with the system() calls, and although I could use an external script, the most I could do with it is stuff the temporary file with the values that I need.  I would still need to call this script from within my C++ application.

As for the "solution" I posted earlier, this was merely a test program.  The real program I am working with is a Qt GUI application in which I need to set text-label fields with the appropriate values as registered by the system.  Not only am I displaying the ifconfig-related values, I am also displaying the kernel version, the architecture type, and the video chip-set type of the system.

I was just wondering if there was a Linux kernel- or C-library call that I could use in lieu of the scripting.

Btw, the Ash shell I am using is provided by BusyBox-1.2.2.1.  BB is a multi-binary application that provides many services, including the Ash shell, ifconfig, grep, echo, and many others.  Do to its limitations, BB does not support all of the command options that these utilities normally offer.

---

### Post by rgeddes on 2007-10-24
If you're adventurous enough, you could also try the source code for ifconfig found at :

[http://www.tazenda.demon.co.uk/phil/net-tools/]("http://www.tazenda.demon.co.uk/phil/net-tools/")

I'm not certain, but 'lib/interface.c' has a section commented with  'IPV4 address?'  that looks like part of the code to get interface info.

you could probably find a the method for interrogating the kernel for this info... and more... of course, you should abide by the appropriate license requirements.

---

### Post by DMills on 2007-10-24
According to an strace of ifconfig, you may find the following ioctls useful:
SIOCGIFCONF
SIOCGIFHWADDR
SIOCGIFMETRIC
SIOCGIFMTU
SIOCGIFMAP
SIOCGIFTXQLEN
SIOCGIFADDR
SIOCGIFDSTADDR
SIOCGIFBRDADDR
SIOCGIFNETMASK

And indeed the whole output of strace ifconfig may be very helpful. 

Regards, Dan.

---

### Post by rgeddes on 2007-10-25
> **DMills said:**
> According to an strace of ifconfig, you may find the following ioctls useful:
SIOCGIFCONF
SIOCGIFHWADDR
SIOCGIFMETRIC
SIOCGIFMTU
SIOCGIFMAP
SIOCGIFTXQLEN
SIOCGIFADDR
SIOCGIFDSTADDR
SIOCGIFBRDADDR
SIOCGIFNETMASK

And indeed the whole output of strace ifconfig may be very helpful. 

Regards, Dan.

Haven't used strace before... from the man page, strace intercepts and records system calls which are issued by a process and signals that are sent to the process.  

I assume the 'system calls' are kernel functions being executed by the kernel in the name of the process.. sound correct?  I would assume that the 'signals' are the way the kernel returns info back to the process... yes?

Any hints for using this tool would be greatly appreciated

Thanks

---

### Post by DMills on 2007-10-26
> **rgeddes said:**
> 
I assume the 'system calls' are kernel functions being executed by the kernel in the name of the process.. sound correct?  I would assume that the 'signals' are the way the kernel returns info back to the process... yes?
Thanks

Yes for the first, no for the second...
running 
strace ifconfig
in a terminal will dump all system calls into the kernel (together with their arguments) and return values to the terminal which is very useful to see how things work. 

Signals are an asynchronous notification mechanism, and can be sent to a process with the kill command, as well as automatically for things like memory access violations (SIGSEGV - by default aborts the process with a segmentation fault), and async IO completion.  

man kill gives a list.

You may also want to look into ltrace. 

Regards, Dan.

---

