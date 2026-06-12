---
title: "Shell script to ping/see if port 80 is open?"
date: 2011-04-28
forum: Programming Talk
---

### Post by Johnsie on 2011-04-28
Hi,  I'm looking to write a shell script that will ping port 80 of localhost 

If port 80 is closed then the script should send an email to email warning that apache has crashed.

Can anyone help point me in the right direction?

---

### Post by roccivic on 2011-04-28
```
echo -n "GET / HTTP/1.0\r\n\r\n" | nc 127.0.0.1 80 || /path/to/emailing/script

```

This will try to send a GET request to 127.0.0.1 at port 80, if there is no reply it will run the script found at "/path/to/emailing/script"

Schedule it as a cron job.

Hope this helps...

---

### Post by bashologist on 2011-04-28
Great solution very nice and simple. But wouldn't you want echo to interprate the escapes? If I'm right then this might be the correct way.
```
echo -e "GET / HTTP/1.0\r\n\r" | nc 127.0.0.1 80 || /path/to/emailing/script

```I could be wrong.

Edit:
Another possibility...
```
echo GET / | nc 127.0.0.1 80
```

---

### Post by Cheesehead on 2011-04-29
```
netstat -tupln | grep :80
```

---

