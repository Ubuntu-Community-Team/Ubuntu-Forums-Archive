---
title: "Syslog via NC or Java doesn't work"
date: 2010-05-26
forum: Programming Talk
---

### Post by Seine on 2010-05-26
I've been trying to get syslogging to work from Java. The log4j syslogappender doesn't seem to work. I checked the implementation and it looked OK. So, I opened up [RFC3164]("http://www.ietf.org/rfc/rfc3164.txt") and re-implemented it in Java. It still didn't work.

So then I tried to use /bin/nc and it still doesn't work. Perhaps I've misread the RFC. Here's what I'm trying.

/usr/bin/logger 
```

# this works
logger -p user.info hello world

```

/bin/nc   
```

# this doesn't work
echo "<14>May 26 15:23:83 Hello world" > nc -u localhost 514

```

JVM
```

// this doesn't work either
// (language is scala)
import java.net._
import java.io._

val ds = new DatagramSocket()
val fullMsg = "<11>May 26 14:47:22 Hello World"
val packet = new DatagramPacket(fullMsg.getBytes("UTF-8"), fullMsg.length, InetAddress.getLocalHost, 514)
ds send packet

```

Can anyone see what I'm doing wrong?

---

### Post by The Cog on 2010-05-26
The syslog server rsyslogd doesn't listen on the network by default. You must configure this and restart rsyslogd. There is a configuration file /etc/default/rsyslogd that suggests that adding -r might do the trick, but then goes on to say that -r is deprecated. I suspect you may have to change the -c4 to -c3. 

See man **rsyslog.conf** for the v4 configuration options. I haven't read the details but that's probably a better way than using v3 compatibility mode.

Edit:
For all their crowing about how clever and flexible their latest version is, I couldn't find any mention of it being capable of listening on a socket for syslog messages. So I guess that /etc/syslog.conf is useless and you'll have to use the v3 compatibility mode after all.

---

### Post by Seine on 2010-05-27
Thanks for your help. I'm still struggling through this, but I appreciate your info.

---

