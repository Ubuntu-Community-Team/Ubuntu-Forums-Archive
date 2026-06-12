---
title: "perl, automated password handling?"
date: 2006-01-16
forum: Programming Talk
---

### Post by vasdee on 2006-01-16
Hi, 

I hope someone can help me with this:

Basically i'm writing a script to handle backing up data across a couple servers using the scp command. I've looked at using ssh 'authorized_keys' to prevent password prompting between the servers however the ssh config has dissallowed this.

when i run 'scp' ( with the correct command line args ) it will prompt me for a password in order to connect to the other server, what i need to know from all you perl gurus out there is can i open the command and then 'echo/print/pipe' the password to the command issued?

I'm thinking something like:

```

# open the command to ftp
open (CMD, "| scp <args here etc>");

# command issued will prompt for password

# print the password
print CMD, $password;


```

I hope this makes sense :)

Thanks!

---

