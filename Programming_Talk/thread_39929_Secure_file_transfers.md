---
title: "Secure file transfers"
date: 2005-06-07
forum: Programming Talk
---

### Post by nocturn on 2005-06-07
I'm building a web based application that has to share files (https) between different servers (accross countries).

The problem I'm having is how to let all servers easily get access to the others files without making the files publicly available or hardcoding some kind of password.

Any ideas on this one (I need coffee)?

Thanks

---

### Post by vague- on 2005-06-07
Since you obviously don't want some kind of shared secret (passwords, keys, etc.), how about using the servers configuration or TCP wrappers to limit who may view the page?  The worst case then is that you are open to spoofing to anybody sitting on the route between the systems (well, anybody can spoof you but most would never get to see the traffic) - unless there is some attack I am blatantly missing.

I do not think it would be that hard for you to include some authentication scheme, provided your web servers have modules or code available to authenticate with external resources.  It's your prerogative, though...

Note, this still involves hard coding, just a list of site addresses that can access.  Anyway, as I said, it's up to you.

---

### Post by DarkKnight on 2005-06-07
[QUOTE=vague-]Since you obviously don't want some kind of shared secret (passwords, keys, etc.), how about using the servers configuration or TCP wrappers to limit who may view the page?  The worst case then is that you are open to spoofing to anybody sitting on the route between the systems (well, anybody can spoof you but most would never get to see the traffic) - unless there is some attack I am blatantly missing.

I do not think it would be that hard for you to include some authentication scheme, provided your web servers have modules or code available to authenticate with external resources.  It's your prerogative, though...

Note, this still involves hard coding, just a list of site addresses that can access.  Anyway, as I said, it's up to you.[/QUOTE]
 You could always implement a public key system :) 

If you used PHP you could keep them in a file above /var/www and then just stream them to the server requesting it. 
Or, if you don't have access to above /var/www. how about a apache file (I forget the name...) which dissalows all but local connections. 
(I'm not sure this can be done in .jsp, since I've not coded them, but it should be...)

You'd still have to code the public key system, but some languages come with built-in support. :)

---

### Post by LordHunter317 on 2005-06-07
Just password protect the site (even using just plain HTTP auth) and make sure the password is well protected on the client machines.  That's the quick, easy, and simple solution.

The elegant one would be to generate SSL certificaties for the clients and put them on the web server.  You can then deny/allow access based on those certificates.

---

### Post by nocturn on 2005-06-08
[QUOTE=LordHunter317]Just password protect the site (even using just plain HTTP auth) and make sure the password is well protected on the client machines.  That's the quick, easy, and simple solution.
[/quote]

Thanks for the tip, but unfortunately, the machines are peers (with some probably being ultrapeers), they are outside of my control (in different countries, some without a real admin).  Their number is currently at 10 or so, but it over time it can run over 130.

> 
The elegant one would be to generate SSL certificaties for the clients and put them on the web server.  You can then deny/allow access based on those certificates.

Now, that's a very good idea!  This would solve a lot of my problems.  
Thanks.

---

### Post by LordHunter317 on 2005-06-08
FWIW, you still need client (or peer) security to use the SSL certs.    If the private key of the cert is stolen, you're still in trouble, like it or not.  

Neither solution will work if all the machines in the network aren't secured.

When I said client/server above, client meant whatever machine was talking to Apache at that moment, and server meaning the one serving the files at that moment.  The fact that different machines can be a server doesn't really change anything in either solution, just makes it a little more complicated, as you have to send the right certificate to the right place.

---

### Post by nocturn on 2005-06-08
[QUOTE=LordHunter317]FWIW, you still need client (or peer) security to use the SSL certs.    If the private key of the cert is stolen, you're still in trouble, like it or not.  

Neither solution will work if all the machines in the network aren't secured.
[/QUOTE]

That's a big drawback, I know...
But it is better then providing a hardcoded password.  Some machines will be superservers, so I can have them keep a list of certificates that are known to be compromised.  Not optimal, but better then nothing.

---

