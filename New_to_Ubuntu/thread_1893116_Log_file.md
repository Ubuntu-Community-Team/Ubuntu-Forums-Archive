---
title: "Log file"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by nickyflavian on 2011-12-09
How can I create a new log file that will show informations about opening or closing the network interfaces , in the following format :
 - UP [01 -12 -10 / 12:00:00 ] 
-  DOWN [20-12-10 / 18:58:34]

where  "01 -12 -10 / 12:00:00" represents : DD- MM- YY / HH:MM:SS (D - day , M- month ,Y- year, H -hour, M- minute ,S -second). Thanks.

---

### Post by MG&amp;TL on 2011-12-09
> **nickyflavian said:**
> How can I create a new log file that will show informations about opening or closing the network interfaces , in the following format :
 - UP [01 -12 -10 / 12:00:00 ] 
-  DOWN [20-12-10 / 18:58:34]

where  "01 -12 -10 / 12:00:00" represents : DD- MM- YY / HH:MM:SS (D - day , M- month ,Y- year, H -hour, M- minute ,S -second). Thanks.

I imagine there is one already, although probably not in that format. Try here: [https://help.ubuntu.com/community/LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles")


If not, this is a big project. I imagine you can probably use something like redirecting syslog to a file with awk and grep.

---

### Post by nickyflavian on 2011-12-10
After I edited my /etc/network/interfaces file I want to add a last line that will redirect messages to  a /var/log/my_logfile  every time when the network interface is down or up, like in the example above. It is possible to do this?  I tried what you said with grep, but no luck ( or  I'm not using it properly). Thanks.

---

### Post by JKyleOKC on 2011-12-10
Check out the pre-up, post-up, pre-down, and post-down options within the /etc/network/interfaces stanzas. You can Google "etc network interfaces pre-up" for a start toward learning what they can do and how to use them, but the names are pretty much self-explanatory. Each of these options should be followed by a command, that will be executed as "root" at the specified time as the interface is brought up or down, so you can have something like ```
post-up echo "eth0 up at $(date)" >> /home/me/eth0.log
```to add a note to your log when the interface comes up, and a similar line to log when it goes down. Note that this is an **untested** example and you may have to twiddle with it a lot to get it working as you desire, but it may give you a lead...

---

### Post by MG&amp;TL on 2011-12-10
I don't think so; but you could have a cron script that would redirect dmesg output to a file; something like this:

```

dmesg | grep interface1 | tee /path/to/my/log/file
dmesg | grep interface2 | tee /path/to/my/log/file
```

---

