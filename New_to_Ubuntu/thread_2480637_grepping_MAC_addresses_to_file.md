---
title: "grepping MAC addresses to file"
date: 2022-11-04
forum: New to Ubuntu
---

### Post by sniper8752 on 2022-11-04
I am trying to extract all MAC addresses in this format: AA:AA:AA:AA:AA:AA.  I tried the following, but it did not work:
```
grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}' <file-name>

```

---

### Post by Holger_Gehrke on 2022-11-04
I don't know what's wrong, but the regular expression is correct. Feeding the output of 'ip address' through a pipe to grep outputs the lines containing MACs and highlights them. Unless you actually had the '<' and '>' around your file name and aren't just using them to denote redacted content. Those are redirection operators in the shell and having just a '>' at the end of the line would get you "bash: syntax error near unexpected token `newline'" since bash expects the name of a file to redirect output to.

Holger

---

### Post by TheFu on 2022-11-04
Seems to be working here ...

```
$ arp | grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}'
```

If want to keep just the MACs, then use ... what's the option?  -o?   That will only output the matched patterns.

```
$ arp | grep -io '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}'
```

Obviously, 
```
$ grep -io '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}' /path/to/file
```
will work too.

Perhaps if you show the exact data file and the exact command run?

---

### Post by MAFoElffen on 2022-11-05
It works for me, if I exclude "00:00:00:00:00:00", which would be an invalid MAC address, except if you were referring only to 127.0.0.1
```

ip addr | grep -i '[0-9A-F]\{2\}\(:[0-9A-F]\{2\}\)\{5\}'  | grep -v '00:00:00:00:00:00'

```
I couldn't think of any other uses cases where that failed.

---

### Post by sniper8752 on 2022-11-05
If it helps, I am using csv output from Advanced IP Scanner.
Here is the format of the log file:
Status    Name    IP    Radmin    Http    Https    Ftp    Rdp    Shared folders    Shared printers    NetBIOS group    Manufacturer    MAC address    User    Date    Comments

---

### Post by TheFu on 2022-11-05
> **sniper8752 said:**
> If it helps, I am using csv output from Advanced IP Scanner.
Here is the format of the log file:
Status    Name    IP    Radmin    Http    Https    Ftp    Rdp    Shared folders    Shared printers    NetBIOS group    Manufacturer    MAC address    User    Date    Comments

It depends on the CSV contents.  Perhaps it is using unicode characters, not ASCII?

---

