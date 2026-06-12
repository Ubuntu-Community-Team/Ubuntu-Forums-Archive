---
title: "Grabbing Text Off of a Server"
date: 2021-08-17
forum: Programming Talk
---

### Post by Complete on 2021-08-17
For the first time in my life as a software developer I am tasked to remote in by VPN (sort of) to a server where ASP code resides.  I want to copy and paste the text locally so I can do things like searches for function names and such.  I can do it on the server perhaps but there is an issue with lag time.  Also, the screen I remote into with is small.

I would like very much to cut and paste the ASCII text.

I can cut and paste via screen shots and piece it together and then use OCR software to convert into text.  But that does not work.

---

### Post by QIII on 2021-08-17
Is this a Windows server?

---

### Post by TheFu on 2021-08-17
Use ssh to remote into the system. If that works, then you can use scp or sftp to copy files from the remote system to your local system. No images used.
ssh is how computer.

Or with ssh, you can just have a terminal into the remote system and local terminals, then use X/Windows select/paste if you only want a few characters, words, lines at a time. But for more than 1 page of text, use scp or sftp instead.  There was a question in the last few days about how to copy/paste in Linux.  I responded with a very detailed answer with all the mouse buttons.

Also, if you want all the output from a command, simply redirect the output to a file.  Redirection is a standard thing in all computers, including Windows.  A software developer should already be able to do that on all the OSes. They work the same.

```
cat /etc/hosts > /tmp/my-local-copy-hosts
```
or
```
inxi -Fxxxz >  /tmp/my-system-info
```
If you want to both see the output AND redirect it into a file, use 'tee'
```
inxi -Fxxxz |tee  /tmp/my-system-info
```
That will overright the output file every time.  If you want to append new stuff, use the -a option:
```
inxi -Fxxxz |tee **-a**  /tmp/my-system-info
```

I think all this works the same on MacOS and Windows.
For more, [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) ... find the section on "redirection".

---

### Post by Complete on 2021-08-18
Yes, it is a Windows server

---

### Post by Complete on 2021-08-18
> **TheFu said:**
> Use ssh to remote into the system. If that works, then you can use scp or sftp to copy files from the remote system to your local system. No images used.
ssh is how computer.

Or with ssh, you can just have a terminal into the remote system and local terminals, then use X/Windows select/paste if you only want a few characters, words, lines at a time. But for more than 1 page of text, use scp or sftp instead.  There was a question in the last few days about how to copy/paste in Linux.  I responded with a very detailed answer with all the mouse buttons.

Also, if you want all the output from a command, simply redirect the output to a file.  Redirection is a standard thing in all computers, including Windows.  A software developer should already be able to do that on all the OSes. They work the same.

```
cat /etc/hosts > /tmp/my-local-copy-hosts
```
or
```
inxi -Fxxxz >  /tmp/my-system-info
```
If you want to both see the output AND redirect it into a file, use 'tee'
```
inxi -Fxxxz |tee  /tmp/my-system-info
```
That will overright the output file every time.  If you want to append new stuff, use the -a option:
```
inxi -Fxxxz |tee **-a**  /tmp/my-system-info
```

I think all this works the same on MacOS and Windows.
For more, [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) ... find the section on "redirection".

I have been told that the server is behind a firewall.  Does that render your solution unworkable?

---

### Post by TheFu on 2021-08-18
> **Complete said:**
> I have been told that the server is behind a firewall.  Does that render your solution unworkable?

Just try it.  Once connected to the VPN, of course.

---

