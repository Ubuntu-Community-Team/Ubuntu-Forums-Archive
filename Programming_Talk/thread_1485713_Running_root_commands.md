---
title: "Running root commands"
date: 2010-05-17
forum: Programming Talk
---

### Post by ja660k on 2010-05-17
Hey all. 

Just for fun, im writing a twitter client in perl, that will apply changes to my server,
eg: I post
START ssh;
STOP apache2
HALT;

and the client will then call the appropriate commands in bash.
but, i dont have permission to run those as a normal user.
so how would i get around that?

can i change the owner of my script to root?
then can i?
or what should i do?

---

### Post by Some Penguin on 2010-05-17
Traditionally the SUID flag on scripts (for 'set user id' -- run program as owner, regardless of invoker) is ignored for security reasons.  A binary executable compiled from C (for instance) would not have that limitation.

You could also have an ordinary user-level program function as a twitter client, pulling down updates and writing them somewhere, and having a program running as root that would validate and execute, if you wanted to avoid granting root permissions to somebody else's Twitter client code.

---

### Post by ja660k on 2010-05-17
i dont understand.

i tried this?
```

-rwxr-xr-x 1 root   ja660k  18 2010-05-17 19:41 haltSystem
...
ja660k@server:~/bin$ ./haltSystem 
halt: Need to be root


```

---

### Post by nvteighen on 2010-05-17
Wait... why would a normal user be allowed to stop the server? There's a reason why this is protected to be altered just by root... mainly that not even a remote account can knock your server down with no single obstacle to avoid it.

If you need to stop the server, then your application is not for normal users... Like Some Penguin said, split it up into a configuration facility and the application... or maybe you're just doing something wrong.

---

### Post by ja660k on 2010-05-17
yeah i realize that, but its not a server that gets any kind of hits,
its a box i got for $20 that out in the garage.

and i'd like to not have to ssh in when i need something... i can be on the train to university realize i forgot something and mobile text my twitter, telling my server to open ftp ... or something.

i dont know, i was wondering if it was possible, i was quite bored 3 hours ago and got stuck on it... so i thought i'd consult :P

---

