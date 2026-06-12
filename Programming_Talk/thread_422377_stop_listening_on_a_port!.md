---
title: "stop listening on a port!"
date: 2007-04-25
forum: Programming Talk
---

### Post by Elisei on 2007-04-25
hi everybody :

i am writing a php script that opens a tcp connection on port lets say 15000; the problem is that i can only run the script once, afterward it fails to bind anything on that port because the socket remain opened after the program exits & the needed port is still "listening";

is there a way or command to close the port down? i am able to kill the listening process when netstat -tap reports it with process id , but most of the time the process id field is blank;

thanks;

---

### Post by amo-ej1 on 2007-04-25
Try to set the socketoptions see [http://be.php.net/manual/en/function.socket-set-option.php](http://be.php.net/manual/en/function.socket-set-option.php)

Using this fuction you can set the following:

```

socket_set_option($socket,SOL_SOCKET,SO_REUSEADDR,1);

```

This will try to reuse addresses. Another alternative would be to properly close the sockets ;-)

(btw this is the same solution as in C ;-) )

---

