---
title: "connection problem for the update manager"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by rakesh343 on 2013-09-01
when I visited another university this summer, the internet services were provided through intranet, and connection settings were accordingly modofied. When I came back, i changed the connection settings for the system and I am able to browse. But update manager is still trying to connect through the old connection setting and failing to connect to the internet. Where to change it?

---

### Post by Jonathan Precise on 2013-09-01
Try:

```
software-properties-gtk
```

Change the server to:

> Server of United states

That should fix the problem.

---

### Post by bapoumba on 2013-09-01
> **rakesh343 said:**
> when I visited another university this summer, the internet services were provided through intranet, and connection settings were accordingly modofied. When I came back, i changed the connection settings for the system and I am able to browse. But update manager is still trying to connect through the old connection setting and failing to connect to the internet. Where to change it?

Did you use a proxy configuration at this univ ?
[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

### Post by rakesh343 on 2013-10-04
Dear bapoumba,

Yeah, It was using a proxy setting when it was temporarily set up there. Now I am back to my home where no proxy is required. I am able to browse the web now, by shifting to "No proxy" option in the Firefox preferences. But the update manager seems to got stuck with the old proxy. That's my guess. What to do?

---

### Post by bapoumba on 2013-10-04
In the above link, there is a section for apt permanent proxy configuration : [https://help.ubuntu.com/community/AptGet/Howto#APT_configuration_file_method](https://help.ubuntu.com/community/AptGet/Howto#APT_configuration_file_method)

Please have a look at the files and see if the proxy has been set up there :
```
cat /etc/apt/apt.conf
cat ~/.bashrc
```

---

### Post by rakesh343 on 2013-10-05
Yeah, it's there. How to remove that?

---

### Post by bapoumba on 2013-10-05
Which one ?
Please paste the outputs here.
If you are familiar with the steps, backup the file first, then edit it to comment out the line (place a # at the beginning). You'll need admin rights to do so. If you are not, paste both outputs and we'll walk you through.

---

