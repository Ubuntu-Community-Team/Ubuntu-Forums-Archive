---
title: "Socket Programming/Ftp client"
date: 2007-07-19
forum: Programming Talk
---

### Post by Iceberg79 on 2007-07-19
Hellow,
i am a newbie in C programming..I am trying to create a standard FTP client..So far i am having trouble with the list command that i tried to create..It sends the port command and returns the succesfull port command as a results. But the main problem is that the server cannot create the data connection and so i cannot view the directory file listing.Please any ideas will be positivelly appreciated
..am also directly available at [email]giusseppe28@hotmail.com[/email].....

---

### Post by leibowitz on 2007-07-19
How dear... that is old for me.

If I remember correctly, the port connection is in one direction, and passive in the other.

Which is which... with port the server should connect the data pipe with the client. In Passive mode it's inverted, the client do the connection.

That's why you can't use Port-like connection if you have a firewall. I know port does not work for everyone. Anyway you must wait for a new connection on your client. That's all I can remember.

---

### Post by slavik on 2007-07-20
port 21 for commands, port 20 for data.

---

### Post by Mr. C. on 2007-07-20
The data connection using PORT in FTP connections are oft-blocked by NATing firewalls, because the incoming connection to the server does not appear as an established connection.  Either use PASV, or test with a local (non-blocked) FTP server.

MrC

---

### Post by Iceberg79 on 2007-07-21
Hi all,

I decided to switch to the passive mode of connectivity for the ftp. When i send the passive command to the server i get the reply which contains the server's IP address and the two integers which are supposed to be the port number parameters.
The string looks like this  # 227 Entering Passive Mode (157,24,53,31,11,135)..
for which the port number becomes 2951...
Now i need to extract the port number so that i can create another socket that will cater for the data transmission for the ftp client..This is because the server keeps on sending the varying port numbers that a client can use to establish a data...My question is how can i extract the two integers from this string so i can calculate the port number..?

---

### Post by Mr. C. on 2007-07-21
These two integers are in network order, and are both sized 8 bits.  Let's see how the math works.  Lets look at their binary equivalents:

```
$ bc
obase=2
11
[COLOR="Blue"]1011[/COLOR]
135
[COLOR="Blue"]10000111[/COLOR]

```

Now, lets combine the two chars (ignoring leading zero's):
```

$ bc
ibase=2
101110000111
[COLOR="Blue"]2951[/COLOR]
```

So we see where 2951 comes from.  To obtain the 2951 value programmatically, you need to left shift p1 and combine it with p2.  Compile and run the following:

```
#include <stdio.h>
#include <netinet/in.h>

unsigned char p1 = 11;
unsigned char p2 = 135;

main ( ) {
    printf ("P1 is %d\n", p1);
    printf ("P2 is %d\n", p2);
    printf ("%d\n", (p1 << 8) | p2);
}
```

When doing network programming, one has to take into consideration that some platforms are little endian, and some are big endian.  But the bytes transferred in a network stream must be standardized so that each host on the net knows the order.  Each host must then translate according to its architecture's endianness.

There are functions called **htons**, etc. which help out with this translation.  See **man htons**.  These functions will come in handy.

MrC

---

### Post by Iceberg79 on 2007-07-21
Hellow Mr C

Thanks very much for the reply i gained something from there.

So for example i have this string h1,h2,h3,h4,p1,p2....

How can i extract the p2 and p2, and proceed as adviced...?


I highly appreciate for your time...


:confused:

being novice sucks....

---

### Post by Mr. C. on 2007-07-21
Being a novice is the most exciting time!  So much to discover.  I relish that period of time.

Anyway, see:

```
man sscanf
```

for extracting a string into constituent parts.

MrC

---

### Post by Iceberg79 on 2007-07-24
Hellow Mr C..and the other members,

I tried to work out some stuffs with the code and this time realized that i cannot connect to the standard ftp server..Prior to working out with the pasv command n then created a new socket that i can use as the data connection,but when i try to connect to the server through this new socket i get this message "Connection refused"...

Any help and ideas on the matter will highly be appreciated...

Novice boy trying to walk...

---

### Post by Mr. C. on 2007-07-24
Its not possible to provide help with such a generic description, and no specific details.

Remove any firewalls from the equation (eg. run the ftp server on your development platform, or somewhere on your LAN). Make sure you can connect with a standard FTP client. Examine your logs.

MrC

---

### Post by Iceberg79 on 2007-07-25
Hi Mr C, and other members,

Am back again,This time i would like to appeal for your guidance,

My problem is that when i send the passive command, i receive the reply Entering the passive mode, and then followed by the IP address and the two parameters that can be used to calculate the port number...If i send the "LIST" command to the server i get the responce message as detailed below..
"150 Opening Ascii mode data connection for /bin/ls"

and after a second there comes another message but this time erroneous, as detaile below..
"425 Cant open data connection"

My question is what to do from here...

Any ideas will be highly appreciated.
.................................................................
"Hate them dedlines"

---

### Post by Mr. C. on 2007-07-26
Anyone doing network programming needs to become *very* familiar with 

a) the relevant RFCs for the protocol/application
b) packet tracing with tcpdump

Here's the RFC index:  [http://tools.ietf.org/rfc/](http://tools.ietf.org/rfc/)

Start with RFC 959.  Note the Obsoletes and Updates in the upper left corner.  RFCs are update as necessary, and the online RFCs give reference to the newer versions.

MrC

---

