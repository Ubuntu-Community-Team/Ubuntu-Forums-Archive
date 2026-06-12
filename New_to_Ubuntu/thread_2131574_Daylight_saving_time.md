---
title: "Daylight saving time"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by orangecsky on 2013-04-02
I am using Ubunto 12.04, and unable to get the clock to display the correct time after the clock changed on Sunday. I have ntp installed and have tried 

```

sudo ntpdate ntp.ubuntu.com
```

The current time is 10:33.

```
~$ date
Tue Apr  2 09:32:59 BST 2013
~$ sudo dpkg-reconfigure tzdata

Current default time zone: 'Europe/London'
Local time is now:      Tue Apr  2 09:33:10 BST 2013.
Universal Time is now:  Tue Apr  2 08:33:10 UTC 2013.


```

Please advise.

Thank you in advance.

---

### Post by slickymaster on 2013-04-02
Try to manually sync your clock. Run the following:
```
sudo service ntp stop
sudo ntp.ubuntu.com
sudo service ntp start
```

---

### Post by orangecsky on 2013-04-02
I have tried 

```


sudo service ntp stop 
sudo ntpdate ntp.ubuntu.com 
sudo service ntp start
```

and got the following message

```


no server suitable for synchronization found
```

Please advise.

Thank you.

---

### Post by slickymaster on 2013-04-02
[Here]("http://www.pool.ntp.org/zone/europe"), there's a the list of time servers for Europe region. From your original post I'm assuming that your time zone is Europe/London, so just replace the server in your commands:
```
sudo service ntp stop 
sudo ntpdate uk.pool.ntp.org
sudo service ntp start
```

---

### Post by SlugSlug on 2013-04-02
Have you checked your time zone?
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by orangecsky on 2013-04-02
> **slickymaster said:**
> [Here]("http://www.pool.ntp.org/zone/europe"), there's a the list of time servers for Europe region. From your original post I'm assuming that your time zone is Europe/London, so just replace the server in your commands:
```
sudo service ntp stop 
sudo ntpdate uk.pool.ntp.org
sudo service ntp start
```

I am still getting

```
no server suitable for synchronization found
```

Thank you.

---

### Post by Nutster on 2013-04-02
Try using another time server in your area instead of [font=Courier New]ntp.ubuntu.com[/font].  There are a few publicly available times servers in the London, England area.  Try using [FONT=Courier New]ntp.exnet.com [/FONT] (a company in London) or even one of the [FONT=Courier New]pool.ntp.org[/FONT] servers, like [font=Courier New]0.uk.pool.ntp.org[/font].

Which command is giving you the error message?  Is it ntpdate or when you restart the ntp service?  If it is when you restart the ntp service, then your ntp daemon is misconfigured.  Look in [font=Courier New]/etc/ntp.conf[/Font] and look for lines that begin with [font=Courier New]server[/font].

---

### Post by slickymaster on 2013-04-02
> **orangecsky said:**
> I am still getting

```
no server suitable for synchronization found
```

Thank you.

You have to replace the server. In the link I provided you, and for the UK alone, you have 4 servers:
```
0.uk.pool.ntp.org
1.uk.pool.ntp.org
2.uk.pool.ntp.org
3.uk.pool.ntp.org
```

---

### Post by orangecsky on 2013-04-05
Thank you all for your helps.

I could not connect to any server that day, but Ubuntu displays correct time today.

---

