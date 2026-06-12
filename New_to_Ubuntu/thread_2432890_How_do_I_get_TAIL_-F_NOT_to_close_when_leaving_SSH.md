---
title: "How do I get TAIL -F NOT to close when leaving SSH (PUTTY)?"
date: 2019-12-10
forum: New to Ubuntu
---

### Post by victorftp on 2019-12-10
Good afternoon friends...
I need help.
I am using this command:


```
tail -f -n +1 linux.log | grep ".com.br/ceo" | goaccess -p /usr/local/etc/goaccess/goaccesscontrole.conf -o /var/www/dashboard.com.br/ceo.html --real-time-html --fifo-in=/tmp/ceo.in --fifo-out=/tmp/ceo.out --port=7895 --daemon
```


this command tail in a file that tells grep filter that tells goaccess to generate the dashboard it works while I have the putty window open, if I close putty only the last pipe command is still active ... precisely because of "--daemon" which is a command that makes goaccess run in the background.


It is still active but not updated because tail and grep are not active.
How do I make tail -f active even if I close ssh and keep sending it to goaccess?
already tried:
nohup in front of the tail
and "> / dev / null &" at the end of the entire command



sorry for the english im brazillian

---

### Post by SeijiSensei on 2019-12-10
You could run it in the background sending the output to a file.

```
tail -f /path/to/file >> /home/me/tail.log 2>&1 &
```

I included the "2>&1" just in case this process generates output sent to syserr.

Although in this case, it would be just as easy to tail the file the next time you log in.  Use "-n NNNN" to have it include the last NNNN lines of the file.

---

### Post by victorftp on 2019-12-11
thank you very much friend ... I ended up solving using the screen command ... what do you think of the solution?

---

### Post by TheFu on 2019-12-11
screen, tmux, file ... whatever you like. Personal preference.

Why use putty and not one of the  normal Linux terminals?   Or are you stuck using MS-Windows?

---

