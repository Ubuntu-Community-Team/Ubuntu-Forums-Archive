---
title: "unable to connect ubuntu server with ubuntu clients in LAN"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by brook on 2008-05-29
i have been unable to connect my ubuntu server with ubuntu clients in a lan. the server is running ubuntu server 7.10 and the clients are ubuntu studio installed. all the pc's are connected via a hub with a physical connection, but they are not yet connected to the internet. 

My question is i have installed Samba on the server, i can login the server with the users i created, i also created a workgroup on the server, however i can not log in the client machines with the accounts created on the server. i have static ip on all the computers, but even dhcp configuration did not help the clients getting the server, though they are connected physically.

---

### Post by superprash2003 on 2008-05-29
are the clients able to ping the server successfully?

---

### Post by brook on 2008-05-29
no, the clients are not able to ping the server

---

### Post by unutbu on 2008-05-29
I am not very good at networking, but perhaps I can further you along a little. 

Please post

```
you@server:~% ifconfig
you@server:~% route

you@client:~% ifconfig
you@client:~% route
```

Let's work on one server and one client. Once you know how to configure that, the other clients can be connected similarly.

---

### Post by brook on 2008-05-29
thats a good reminder though i gave the client static ip, and ifconfig would show me just that. what i want to know now is that  because i have no windows clients (only ubuntu), is installing samba needy? i mean i think i can install ldap or other for authenticating clients on the server, isn't it?

---

### Post by superprash2003 on 2008-05-29
are you planning to use it to share files or as a domain controller?

---

### Post by brook on 2008-05-29
latest news-> ping works, it was me the dummy who didnt restart the pc and see the changes, well now i tried to login the clients with the account created on the server, and it doesnt work. what more should i add to this server to enable account authentication of the client machine on the server? i think this is some directory service kind of question isn't it?

---

### Post by brook on 2008-05-29
as for the choice of the server action, i think i might consider making the server a domain controller first, and be able to give directory service

---

### Post by superprash2003 on 2008-05-29
then try LDAP [http://www.debuntu.org/ldap-server-and-linux-ldap-clients](http://www.debuntu.org/ldap-server-and-linux-ldap-clients)

---

### Post by brook on 2008-05-30
ok, well i tried installing LDAP and this server, after getting the slapd and ldap-utils, says that it cant find the package *migrationtools* from the cd server 7.10. therefore, i cant pass beyond
 *#apt-get install slapd ldap-utils migrationtools*
what to do...

---

