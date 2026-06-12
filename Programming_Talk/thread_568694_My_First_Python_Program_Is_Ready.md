---
title: "My First Python Program Is Ready"
date: 2007-10-06
forum: Programming Talk
---

### Post by bobbocanfly on 2007-10-06
Been teaching myself Python through the link in one of the people here's sig and made my first useful program, a port scanner.

```

#Tiny-Scan
#Version 0.2.0
#A tiny Python port scanner with basic port use info
#Copyright (C) Bobbocanfly

import socket,sys
i = raw_input("IP? ")
a = int(raw_input("Start Port? "))
b = int(raw_input("End Port? "))
c = {'20': 'FTP Data', '21': 'FTP', '22': 'SSH', '23' : 'Telnet', '25' : 'SMTP', '53' : 'DNS', '66' : 'SQL*NET', '79' : 'Finger', '80' : 'HTTP', '110' : 'Pop3' }
for p in range(a, b + 1):
   try:
      s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
      s.connect((i, p))
      print p," Open"
      if c.has_key(str(p)):
            print p, " Normally ", c[str(p)]
   except socket.error:
      print p," Closed"

```

The only thing i could think of doing to it would be to get options from the command line and extend the "port-dictionary".

---

### Post by Compyx on 2007-10-06
Well, if you want to look at parsing command line options, I would recommend looking into optparse: [http://docs.python.org/lib/module-optparse.html]("http://docs.python.org/lib/module-optparse.html"),  it's a pretty nice module for scanning the command line for options and arguments.

It's quite powerful and flexible and follows the standard GNU/POSIX syntax for specifying options and arguments.

---

### Post by zanglang on 2007-10-06
> **bobbocanfly said:**
> 
The only thing i could think of doing to it would be to get options from the command line and extend the "port-dictionary".

Just a thought, you can probably try and parse /etc/services and read the port mappings and comments from there.

---

### Post by bobbocanfly on 2007-10-06
> **zanglang said:**
> Just a thought, you can probably try and parse /etc/services and read the port mappings and comments from there.

Thanks for the suggestion but im trying to keep it as cross platform as possible (Tested working on Windows about 10 minutes ago).

Compyx, thanks for the link ill try and work that in later. :)

---

### Post by slavik on 2007-10-06
if you want something fun, take a look at nmap source code ;)

---

### Post by Billy the Kid on 2007-10-06
If you want something simple, try replacing the values of variables i, a and b with:
```

i = sys.argv[1]
a = int(sys.argv[2])
b = int(sys.argv[3])
```

You would then be able to specify the options from the command line, for example:
python tiny-scan.py 127.0.0.1 80 120
Where "127.0.0.1" would be the host to scan, 80 would be the start port and 120 would be the end port

---

### Post by slavik on 2007-10-06
> **Billy the Kid said:**
> If you want something simple, try replacing the values of variables i, a and b with:
```

i = sys.argv[1]
a = int(sys.argv[2])
b = int(sys.argv[3])
```

You would then be able to specify the options from the command line, for example:
python tiny-scan.py 127.0.0.1 80 120
Where "127.0.0.1" would be the host to scan, 80 would be the start port and 120 would be the end port
I would suggest using a getopt library.

---

### Post by cwaldbieser on 2007-10-07
> **bobbocanfly said:**
> Thanks for the suggestion but im trying to keep it as cross platform as possible (Tested working on Windows about 10 minutes ago).

Compyx, thanks for the link ill try and work that in later. :)

I think Windows has an /etc/services file buried in Windows/system32/drivers (or something similar depending on the version of Windows).

---

