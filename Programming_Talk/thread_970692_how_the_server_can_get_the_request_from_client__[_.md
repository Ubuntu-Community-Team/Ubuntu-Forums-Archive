---
title: "how the server can get the request from client?  [ perl ]"
date: 2008-11-04
forum: Programming Talk
---

### Post by shafi on 2008-11-04
Dear all,
I have a problem in my code, I am able to get the reply from server and print it into the client, but I can not do vice versa.
in my case the client send a request to the server and the server should check the request and according to that request reply for the client.
This is the server code:
[HTML]


    for ( ; $paddr = accept(Client,Server); close Client) {
        my($port,$iaddr) = sockaddr_in($paddr);
        my $name = gethostbyaddr($iaddr,AF_INET);

        print Client "Hello Client\n";
    }
[/HTML]
This is the Client code for getting reply;
[HTML]
while (defined($line = <SOCK>)) {
        print $line;
    }

    close (SOCK)  || die "close: $!";
    exit;

[/HTML]
now how can i check the client request in the server file?
I used the same code into the server but that doesnt worked for me.

---

### Post by shafi on 2008-11-04
any one??

---

### Post by slavik on 2008-11-04
have you tried reading from the client? you are not even doing that ...

---

### Post by shafi on 2008-11-05
> **slavik said:**
> have you tried reading from the client? you are not even doing that ...

I dont have the idea how to do that,
I have used the same way as I used in client by I am getting null value.

---

