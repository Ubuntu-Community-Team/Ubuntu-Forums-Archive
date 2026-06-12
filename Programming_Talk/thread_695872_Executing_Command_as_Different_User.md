---
title: "Executing Command as Different User"
date: 2008-02-13
forum: Programming Talk
---

### Post by nlbs on 2008-02-13
Hi! Geeks
I wanna execute a Command on terminal as a different User
I know I can use su or sudo But What I want is different
su userName -c 'Command'
asks to enter password
What I want is NONINTERACTIVE
su userName -c 'command'  -p Password
or something like this
is it posiible ??
I know that there is no option called -p for password I used that just to make you understand what my question really is
Thanks

---

### Post by lnostdal on 2008-02-13
maybe you want something like:

```

lars@ibmr52:~/programming/lisp$ echo "mysecretpassword" | sudo -S whoami
root
lars@ibmr52:~/programming/lisp$ 

```

*-S* causes sudo to read from *STDIN* =) .. edit: check the man-page for sudo for more info: *man 8 sudo*

---

### Post by nlbs on 2008-02-14
Thanks It works But needs the Issuing user to stay in /etc/sudoers and belong to sudo Group

---

### Post by stroyan on 2008-02-14
A setuid program is another common way to let one user run 'a command' as another user.
You create a program and set its permissions so it always runs as the other user.
```
sudo chmod otheruser a.out
sudo chmod u+s a.out
```
That requires care in creating the program so that it is not misused to do something that was not intended.
But it does avoid having a cleartext password in a script.
The program can check the original user id to see if that user is allowed to run it.
See [http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

---

