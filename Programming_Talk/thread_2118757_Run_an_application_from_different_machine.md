---
title: "Run an application from different machine"
date: 2013-02-22
forum: Programming Talk
---

### Post by cotoman on 2013-02-22
so here it is guys, i have machine A and machine B. they are not on the same network so far. (maybe i cna manage a VPN or something not the problem here) what i need to do is open a console shell in machine A and run a software i wrote in machine B BUT i want it to run on machine B and get the results on the console on machine A.
so how can i manage to do this? it is extremely important that machine B run the command/compiled-code so it can use the libraries at machine B but not A, and A must get the results to treat them. (and no i cannot install the same libraries on machine A)
both have ubuntu 12.04

---

### Post by albandy on 2013-02-22
you can use ssh and get the result.
For example:

ssh user@machine command

---

### Post by cotoman on 2013-02-22
is it possible to replace a command with something like this: /home/cotoman/Project/some_compiled_binary ?

---

### Post by schragge on 2013-02-22
Yes, provided that the user you're logging in as has the execute permissions on this file.

---

### Post by greenpeace on 2013-02-22
...EDIT: Sorry, just noticed the post above.  Will drink more coffee.

Hi, 

ssh allows you to pass a command at the end of the statement; this command will be run on the remote server, and the results returned to the terminal on your local machine.

Try this on machine A:

```
ssh user@machine.b "ls"
```

ls can be replaced by any valid command from machine B, and you can use pipes ("|") etc.

for more details have a look at
```
man ssh
```

---

