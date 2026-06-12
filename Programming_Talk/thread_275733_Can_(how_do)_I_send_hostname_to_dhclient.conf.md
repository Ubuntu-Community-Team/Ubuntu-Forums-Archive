---
title: "Can (how do) I send hostname to dhclient.conf"
date: 2006-10-11
forum: Programming Talk
---

### Post by Iowan on 2006-10-11
```
send host-name "myhostname";
```
Rather than hardcode in the name of my hostname:
I'd rather use the environment variable $HOSTNAME.

```
send host-name $HOSTNAME;
```
This doesn't work - apparently needs the quotes to indicate text.

```
send host-name "$HOSTNAME";
```
This works, but names the machine $HOSTNAME.

Is it even possible to do what I'm attempting?

---

### Post by skymt on 2006-10-11
> **Iowan said:**
> Is it even possible to do what I'm attempting?

A quick look throught `man dhclient.conf` suggests that the answer is no. dhclient.conf isn't a shell script, so the $ syntax won't work. I couldn't find any way to use an environment variable in the file.

Doesn't dhclient send the contents of /etc/hostname by default?

---

### Post by JonahRowley on 2006-10-11
If it doesn't automatically pick up on /etc/hostname, you can alter the startup script to fill it in for you.  Make a template file (called dhclient.conf.sh or something) that when run, creates your dhclient.conf file with the correct hostname.  Hackish, but it would work.  Seems like there should be a solution to this already though.

---

### Post by Iowan on 2006-10-12
> **skymt said:**
> Doesn't dhclient send the contents /etc/hostname by default?
Not quite sure what you mean...
```
send host-name ;
```
I tried this - just to see if it'd take the default hostname...
This is the same as leaving the line commented out.

Thanks for all (both) the input!

---

### Post by skymt on 2006-10-12
> **Iowan said:**
> Not quite sure what you mean...
```
send host-name ;
```
I tried this - just to see if it'd take the default hostname...
This is the same as leaving the line commented out.

Thanks for all (both) the input!

Yeah. I left out "of". :oops: I meant it sends the contents *of* /etc/hostname. For example, if the file /etc/hostname contains "foo.bar.net", dhclient *should* send foo.bar.net as the hostname.

---

### Post by Malstrond on 2012-04-19
Update for anyone finding this via Google etc.: On dhclient versions >= 4.2.x you can now do
```
send host-name = gethostname();
```

---

