---
title: "unable to resolve host ,when im trying to chown -R (php server configuration)"
date: 2015-06-25
forum: New to Ubuntu
---

### Post by jonnytobaios on 2015-06-25
hello after i changed  my username (a long time ago) now i m trying to set php server in order to run joomla ,and when iam trying to chown -R i m getting unble to resolve host with out asking for my password . The usually thing when i sudo is that i m getting the (unable to resolve host) but it then ask for the password im giving it away and its all done but now this is not happening just stop in messsage (unable to resolve hot) and isn't  asking me for the password so i cant gain prviledge. can someone hepl me to fix this ??? 


thanks!

---

### Post by cariboo on 2015-06-25
Can you let us see what your /etc/hosts file looks like. Open a terminal and type the following command:

```
cat /etc/hosts
```

highlight the output, and paste it into your next post.

---

### Post by jonnytobaios on 2015-06-26
127.0.0.1	localhost.localdomain localhost
127.0.1.1	jony13


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
192.168.1.2 localhost

---

### Post by sandyd on 2015-06-26
Hi, can you post the output of
```

hostname
cat /etc/hostname
``` as well

Thanks!

---

### Post by cariboo on 2015-06-26
What commands did you run to try and solve your problem?

---

### Post by jonnytobaios on 2015-06-27
when i run hostname i get 
X501A

and i get the same when i run cat /etc/hostname
X501A

---

### Post by matt_symes on 2015-06-27
Hi

You need to change the file

/etc/hostname

to contain

jony13

Remove the other text in that file as the name in the file hostname has to match the name in the file hosts.

You may have to boot into a root shell to do this.

Can you boot into a root shell ?

Yo can also use the hostname command with a flag, I forget which one, to change the hostname to jony13.

Kind regards

---

