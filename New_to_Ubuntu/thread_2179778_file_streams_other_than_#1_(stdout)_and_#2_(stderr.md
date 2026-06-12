---
title: "file streams other than #1 (stdout) and #2 (stderr)"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-09
Hello guys,

Is it possible for a command to output data on filestreams other than #1 (stdout) and #2 (stderr)?

---

### Post by heir4c on 2013-10-10
Look to the man-pages of command: tee
```
man tee
```
For the compleet documentation use the command:
```
info coreutils 'tee invocation'
```

example:
```
sudo apt-get update | tee update.log
```
That command create a file with the name update.log and put there every output in that file.

---

### Post by sha1sum on 2013-10-10
Thank you for your reply.

If i understand correctly, tee simply takes the stdout #1 from the command that is pipelined into it, and outputs it again as stdout #1, but also copies it into a text file.

But that does not completely answer my question. My question is, can a shell command output text on filestreams other than #1 and #2. So that you have something like this:

```

command 1> /dev/null 2> /dev/null

```
or simply
```

command &> /dev/null

```
 but where text is still printed on your terminal.

---

### Post by steeldriver on 2013-10-10
something like this maybe?

```

$ cat file
stuff
$ cat file >/dev/null
$
$ exec 3>&1                    # open file descriptor 3 and attach current 'value' of file descriptor 1 to it
$ cat file >/dev/null >&3      # redirect output to file descriptor 3
stuff
$ 
$ exec 3>&-                    # close file descriptor 3
$ cat file >/dev/null >&3      # redirected output doesn't appear (stream is closed)
-bash: 3: Bad file descriptor

```

see [http://www.tldp.org/LDP/abs/html/io-redirection.html](http://www.tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by heir4c on 2013-10-10
And if you use a double >>  than you can add output at the end of a file that already have data inside. 
I don't know many about this, but I remember that of a little Linux-course I followed.

---

