---
title: "Every time I stop Transmission Daemon it starts again"
date: 2014-05-24
forum: New to Ubuntu
---

### Post by dan107 on 2014-05-24
Hi All,

I am running Ubuntu 14.04 server.

Pretty much as the title says. I run the following command

```
sudo /etc/init.d/transmission-daemon stop
```

I get the response [OK] and instantly there is another process running from this daemon. Short version of the issue, I cannot update the settings file if it is running.

Any ideas?

---

### Post by tgalati4 on 2014-05-24
What happens with:

```
sudo service transmission stop
```

---

### Post by dan107 on 2014-05-24
I get this

transmission: unrecognized service

---

### Post by dan107 on 2014-05-24
I just did this though

```
sudo service transmission-daemon stop
```

And it works!

Thanks for the help, thanks very much.

---

### Post by tgalati4 on 2014-05-24
```
man upstart
man service
```

There are subtle differences between using the *service* command and running the control script directly.  I don't know what those differences are, all I know is they behave differently.

After reading some documentation, there must be some events that need to take place for the transmission server to properly shut down.  There is probably a case statement that is not satisfied when you try to close it directly.

[https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto)

---

