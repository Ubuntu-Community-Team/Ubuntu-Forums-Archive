---
title: "Whois Help!"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Swenghk on 2008-08-31
I send: "whois [email]website.net@whois.netw[/email]orksolutions" and it replies with a blinking cursor! Any help? 


P.S. Does anyone know how to do a CORRECT Domain Query using whois?

Edit: That's not a link...don't know why that happened...

---

### Post by aloshbennett on 2008-08-31
eg.

> whois google.com

---

### Post by Swenghk on 2008-09-01
? That wasn't very helpful...

---

### Post by Bachstelze on 2008-09-01
Just type

```
whois domain.tld
```

No at sign.

---

### Post by perlluver on 2008-09-01
it is simply ```
whois www.name.com
```

---

### Post by tommynz1975 on 2008-09-01
**whois**

 The whois command will get domain registration information about a Web site.  Usage:
 whois example.com


[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=w/whois](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=w/whois)

from the link above.


  ```
 whois[options]  query[@server[:port] ]  jwhois [options]  query[@server[:port] ]  
```
 Search a **whois** database for a domain name, IP address, or NIC name. The information returned varies, but usually contains administrative and technical contacts so that you can find a person to handle problems at that domain. By default, the command returns information on *.com*, *.net*, and *.edu* domains, but other hosts can be queried for other domains using *host* or the **-h** option.


 **Options**

  **--** [INDENT]Indicate the end of options. A subsequent string that begins with a hyphen on the command line is taken as a query string.
[/INDENT] **-a**, **--raw** [INDENT]Do not rewrite query according to configuration before sending to server.
[/INDENT] **-c** *file*, **--config***=file* [INDENT]Specify a configuration file to use instead of the default /etc/jwhois.conf.
[/INDENT] **-d**, **--disable-cache** [INDENT]Disable reading and writing to the cache.
[/INDENT] **-f**, **--force-lookup** [INDENT]Force the lookup query to go to the host, even if it is available from the cache.
[/INDENT] **-h** *host,* **--host***=host* [INDENT]Query the **whois** server on the specified host. Same as *host* on the command line. By default, queries the server in the environment variable NICNAMESERVER or WHOISSERVER if either is set; otherwise queries whois.internic.net.
[/INDENT] **--help** [INDENT]Print help message and exit.
[/INDENT] **-i**, **--display-redirections** [INDENT]Display every step in a redirection. The default is to display only the last step.
[/INDENT] **-n**, **--no-redirect** [INDENT]Disable redirection from one server to the next.
[/INDENT] **-p** *port*, **--port***=port* [INDENT]Connect to the specified port. Same as *port* on the command line. Default is 43.
[/INDENT] **-r**, **--rwhois** [INDENT]Force use of the **rwhois** protocol, instead of HTTP or **whois**.
[/INDENT] **--rwhois-display***=display* [INDENT]Request receiving **rwhois** servers to display the results in the specified display instead of the default.
[/INDENT] **--rwhois-limit***=limit* [INDENT]Request receiving **rwhois** servers to limit the number of matches to the specified limit.
[/INDENT] **-s**, **--no-whoisservers** [INDENT]Disable built-in support for whois-servers.net.
[/INDENT] **-v** [INDENT]Verbose. Display the query before sending it to the server.
[/INDENT] **--version** [INDENT]Print version information and exit.
[/INDENT]

---

### Post by nisaky on 2008-09-01
Have you tried typing:

```
man whois
```

man is manual, it says all about every command in terminal.

---

