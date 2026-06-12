---
title: "backwards IP addresses?"
date: 2012-03-07
forum: Programming Talk
---

### Post by conradin on 2012-03-07
hi all,
Im looking for a program I can integrate into a bash script that returns both host-name, and IP, with the IP NOT listed backwards. Is there any program part of the core-utilities which can achieve this? I would like to have a script I can use on any machine, without having to have something else also installed. 


by contrast, nslookup will return a nice string where I can grep out the parts I need, but the IP is allways listed backwards... ?

```

$nslookup 130.111.192.243

Server:		130.111.32.11
Address:	130.111.32.11#53

243.192.111.130.in-addr.arpa	name = icn2.umeche.maine.edu.


```

Ive tried some other commands like dig, and host which all do the same thing, but also return backward listing of IP. Alternatively, if I could get the IP out in the correct forward order, that would be acceptable as well. This backward listing of IP is useless to me, and Im not sure how to get around it.

---

### Post by lykwydchykyn on 2012-03-07
The "backwards" IP is the way reverse DNS records look.  Why do you need the program to output the IP forward?  If it's part of a script, what's your script look like?

---

### Post by lisati on 2012-03-07
In PHP you can do something like this:
[php]
$parts = explode('.',$ip);
$reverse_ip = implode('.', array_reverse($parts));
[/php]

---

### Post by lykwydchykyn on 2012-03-07
Here's a bash one-liner:
```

IP="192.168.1.1"; echo $IP    `host $IP |grep pointer | awk '{ print $NF }'` 

```

---

### Post by papibe on 2012-03-07
'dig' can do that, but only with domain names. For example:
```
dig ubuntu.com

; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21099
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
**ubuntu.com.**		427	IN	A	**91.189.94.156**

;; Query time: 45 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Wed Mar  7 14:26:24 2012
;; MSG SIZE  rcvd: 44

```
Regards.

---

### Post by lensman3 on 2012-03-07
I don't have an ubuntu machine handy, but under Fedora there is program called ipcalc that has a lot of ip6 and ip4 capability.  This program is used in the Fedora startup and returns some data as bash variables.

Sorry it is slightly off topic, but it might be useful.

---

### Post by conradin on 2012-03-11
> **lensman3 said:**
> I don't have an ubuntu machine handy, but under Fedora there is program called ipcalc that has a lot of ip6 and ip4 capability.  This program is used in the Fedora startup and returns some data as bash variables.

Sorry it is slightly off topic, but it might be useful.

I appreciate the input and will certainly have a look at ipcalc.

I am at a bit of an impass for what Im trying to do, in locating network resources. Where the name server will tell me what is assigned, versus using a tool like nmap which will tell me about alive hosts. (*assuming the resource will allow me to find it, and isn't dropping the nmap request via a firewall or something)

nmap returns nice results with the ip in forward order, but it comes with the risk of not returning everything. Ive got a few printers set up like that. polling the name-server with nslookup will tell me where my devices are (I know their nmes), where nmap may fail...
having the ip return from the DNS in forward order would be handy, but maybe this is something that I should just program in C... 
one thought for the script Im working on is to forward the IP addresses to a browser where I can get supply statuses, and possibly have notes about how supplies are... blah blah blah. 

since the ip addresses return in reverse order is there some way to do something useful with that? Is there a program which takes IPs as input in reverse? In that case, my point would be moot. I'm just trying to utilize the results from the name server.

---

### Post by lykwydchykyn on 2012-03-12
As I mentioned earlier, if you're querying the name server for an IP, then you already have the IP; why do you need the name server to return it?  Save it in a variable, and insert it into the output wherever you need it.

Am I missing something here?

---

### Post by conradin on 2012-03-12
I was hoping this would be something simple. What I want is the host name on the same line as the IP. If I send $masq$i to the output file, even if I have it on the same line as the host I would then have 2 (potentially) ip type addresses on the same line. 

```
#!/bin/bash
masq=130.111.226.

for i in `seq 0 255`;
do 
	nslookup  $masq$k.$i | grep -E 'hp.*maine|cam.*maine' >> prNcamsUMO
done

```

So the first problem would be I dont know how to put the forward going ip ($masq$i) on the same line as the nslookup result. Then even if I do figure that out I would also probably need to use grep and awk ... maybe there is a return host name only function... hmmm.

---

### Post by conradin on 2012-03-12
So then I found some help full code here:
[http://linux.die.net/man/3/getnameinfo](http://linux.die.net/man/3/getnameinfo)
[http://cboard.cprogramming.com/linux-programming/94179-getnameinfo.html](http://cboard.cprogramming.com/linux-programming/94179-getnameinfo.html)
and modified an example to meet my needs.
```

#include <netdb.h>
#include <stdio.h>
#include <arpa/inet.h>
 
int main(int argc, char ** argv){
    if (argc < 2) {
        printf("Usage: %s <IP Address> \n", argv[0]);
        return(-1);
    }

  struct sockaddr_in sa;
  sa.sin_family = AF_INET;
  inet_pton(AF_INET, argv[1], &sa.sin_addr);
  
  char node[NI_MAXHOST];
  int res = getnameinfo((struct sockaddr*)&sa, sizeof(sa), node, sizeof(node), NULL, 0, 0);
	  if (res) {
		printf("&#37;%s\n", gai_strerror(res));
		return(1);
	  }
  printf("%s\t = ", argv[1]);
  printf("%s\n", node);
  return 0;
}

```

I'll call this little program with a bash script.
Thanks everyone!

---

