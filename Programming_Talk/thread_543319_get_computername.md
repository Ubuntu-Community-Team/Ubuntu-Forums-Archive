---
title: "get computername"
date: 2007-09-05
forum: Programming Talk
---

### Post by md5hash on 2007-09-05
how can i get the username of a computer?

---

### Post by ewankho on 2007-09-05
try 'hostname' in the terminal

---

### Post by nanotube on 2007-09-05
> **md5hash said:**
> how can i get the username of a computer?

well, the username and computer name are different things, so, to cover all bases, i'll give you both... :) to get the name of the computer:
```
hostname
```

to get the name of current user:
```
whoami
```

---

### Post by lloyd_b on 2007-09-05
> **md5hash said:**
> how can i get the username of a computer?

Your question isn't entirely clear, but:

To get the name of the current user, you can generally just check the LOGNAME environment variable, or capture the output of the "whoami" command.

To get the host name of the computer a program is running on, you can capture the output of the "hostname" command.

If neither of these is what you're looking for, then please post some more details on what you are trying to do.

Lloyd B.

---

### Post by md5hash on 2007-09-05
im sorry but my question is incomplete...

how can i get the username/ip address of a current logged user windows or linux or mac using php script?

i need this to trace if the user is using other peoples account. iam behind a proxy server using this code **gethostbyaddr($_SERVER['REMOTE_ADDR']);** only returns the proxy server ip address..

thanks

---

### Post by nanotube on 2007-09-05
> **md5hash said:**
> im sorry but my question is incomplete...

how can i get the username/ip address of a current logged user windows or linux or mac using php script?

i need this to trace if the user is using other peoples account. iam behind a proxy server using this code **gethostbyaddr($_SERVER['REMOTE_ADDR']);** only returns the proxy server ip address..

thanks

if i understand correctly, the users are connecting to your webserver through a proxy server? if so, there's no way you can get the remote user's ip address from your webserver. that's what a proxy server is for (among other things) - to mask the ip addresses. if you want to get the ips, you have to look at the proxy server's logs.

---

### Post by md5hash on 2007-09-05
i see.. how about the computer name /  or the user name he used to log

---

### Post by nanotube on 2007-09-05
> **md5hash said:**
> i see.. how about the computer name /  or the user name he used to log

well, if he's actually logging into the website (either through the standard http auth method, or through whatever web app you are running), then that should just be in the appropriate webserver logs.

---

### Post by md5hash on 2007-09-05
is this possible with other scripts?

---

### Post by KCPokes on 2007-09-05
You can't get the actual user they are logged into their machine with using PHP scripts.  If you were writing C code, let's say, and tying into the core operating system, then yes, but not remotely over the net.

---

### Post by md5hash on 2007-09-05
how is it in C?

---

### Post by slavik on 2007-09-05
the only info you can get about a user is where the connection is coming from (could be a proxy), and by whatever user agent string he gives you if it's even accurate.

Another way to discern users is by using cookies, but you would have to put stuff in them yourself which goes back to the previous paragraph.

If the user agent string is faked and the connection is through a proxy, then you cannot find out ANYTHING about the person/user/computer that connects to your web server, unless you have some kind of an exploit on your site. :)

---

