---
title: "How to Pass Password to sudo?"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by graphicpower on 2012-06-29
How can I run this command without get prompted to enter the sudo password ?
[COLOR=red]$ sudo chmod -x  /usr/bin/file[/COLOR]
 
 
*I have tried in a script file he command as follows, but it did not work  :icon_frown: *
[COLOR=blue]$ echo MyPassword  |  sudo - S[/COLOR]
[COLOR=blue]$ chmod  -x  /usr/bin/file    [/COLOR]
[COLOR=blue][/COLOR] 
 
Thank You

---

### Post by codemaniac on 2012-06-29
> **graphicpower said:**
> How can I run this command without get prompted to enter the sudo password ?
[COLOR=red]$ sudo chmod -x  /usr/bin/file[/COLOR]
 
 
*I have tried in a script file he command as follows, but it did not work  :icon_frown: *
[COLOR=blue]$ echo MyPassword  |  sudo - S[/COLOR]
[COLOR=blue]$ chmod  -x  /usr/bin/file    [/COLOR]
[COLOR=blue][/COLOR] 
 
Thank You

For sudo there is a -S option for accepting the password from standard input.
You can try the below .

```
echo "$password" | sudo -S chmod -x /usr/bin/file
```

---

### Post by graphicpower on 2012-06-29
I believe you mean doing it in this way, however, it did not work with me, and I got some errors when I passed the password as you can see
 
 
$ cat do-change
echo "$password" | sudo -S  chmod -x /usr/bin/file
 
 
$ ./do-change *MyPassword*
[sudo] password for titan5: Sorry, try again.
[sudo] password for titan5: Sorry, try again.
[sudo] password for titan5: Sorry, try again.
sudo: 3 incorrect password attempts

 
Thanks,

---

### Post by TheFu on 2012-06-29
Other options include:
* a setting the sudo config file NOPASSWD /etc/sudoers
* use 'expect' [http://stackoverflow.com/questions/7990952/sudo-cmd-via-ssh-with-expect-twice-consecutively](http://stackoverflow.com/questions/7990952/sudo-cmd-via-ssh-with-expect-twice-consecutively)
* sudo -A .... it has lots of options to get a password into sudo - external programs

I'd use codemaniac's method, but with an environment variable so you can lock down the script easier.

The man pages for sudo and sudoers are really fantastic. Some of the best man pages ever.

---

### Post by NikTh on 2012-06-29
Yes , that works for me too.. thanks codemaniac.
I think its  a good idea if remove read access from group and others..
```
chmod go-r script.sh
```cause sensitive info its in there.. ;)

---

### Post by NikTh on 2012-06-29
> **graphicpower said:**
> I believe you mean doing it in this way, however, it did not work with me, and I got some errors when I passed the password as you can see
 
 
$ cat do-change
echo "$password" | sudo -S  chmod -x /usr/bin/file
 
 
$ ./do-change *MyPassword*
[sudo] password for titan5: Sorry, try again.
[sudo] password for titan5: Sorry, try again.
[sudo] password for titan5: Sorry, try again.
sudo: 3 incorrect password attempts


 
Thanks,

"$password" = your real password :)

and remove read access from group and others.. 
```
chmod go-r do-change
```

---

### Post by graphicpower on 2012-06-29
THANK YOU ALL, 
 
it works like a charm now  ):P
 
Good Night

---

