---
title: "Count opened http connections"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Blagomir on 2008-05-05
Hi,

I have ubuntu server and i`m making a monitoring system right now. Can you tell me how can i get the number of opened http connections to the server. Actually i want to see how many users are online on the server and not just on one website located there.

---

### Post by gsmanners on 2008-05-05
There are a number of ways to do that, but probably the best thing is to set up a Wireshark capture filter.

[http://wiki.wireshark.org/CaptureFilters](http://wiki.wireshark.org/CaptureFilters)

---

### Post by aos101 on 2008-05-05
If you're using Apache, mod_status might be useful:

[http://httpd.apache.org/docs/2.0/mod/mod_status.html](http://httpd.apache.org/docs/2.0/mod/mod_status.html)

---

### Post by cwgatling on 2008-05-05
And isn't there something like that in /proc/net/snmp?

---

### Post by Oldsoldier2003 on 2008-05-05
> **Blagomir said:**
> Hi,

I have ubuntu server and i`m making a monitoring system right now. Can you tell me how can i get the number of opened http connections to the server. Actually i want to see how many users are online on the server and not just on one website located there.


this snippet will print the number off connections on port 80. It can easily be incorporated in a php page
```
<?php

$cmd = 'netstat -t | grep -c 80';
$userpopulation = shell_exec($cmd);
echo "$userpopulation";
?>
```

---

### Post by gsmanners on 2008-05-05
In that snippet, you might want to do this:

$cmd = 'netstat -t -n | grep -c :80'

That'll go a bit quicker.

---

### Post by Blagomir on 2008-05-06
Thank you all!

Oldsoldier2003 thank you too. Your script works 100% :)

---

