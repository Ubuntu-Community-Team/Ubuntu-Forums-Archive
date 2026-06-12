---
title: "New ip"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by cristo-father on 2008-06-25
How can i get a diferent ip from my router?

---

### Post by iaculallad on 2008-06-25
Release your IP address first:

```
sudo dhclient -r
```

Obtain new IP from DHCP:

```
sudo dhclient
```

And, try to restart the network daemon:

```
sudo /etc/init.d/networking restart
```

---

### Post by cristo-father on 2008-06-25
> **iaculallad said:**
> Release your IP address first:

```
sudo dhclient -r
```

Obtain new IP from DHCP:

```
sudo dhclient
```

And, try to restart the network daemon:

```
sudo /etc/init.d/networking restart
```

How do i can i see my ip?

---

### Post by cdtech on 2008-06-25
ifconfig will give you a listing. IP and interfaces.

---

### Post by cristo-father on 2008-06-25
> **cdtech said:**
> ifconfig will give you a listing. IP and interfaces.

Does it appear after "inet addr:"?

---

### Post by perlluver on 2008-06-25
> **cristo-father said:**
> Does it appear after "inet addr:"?

Yes it does.

---

### Post by cristo-father on 2008-06-25
> **perlluver said:**
> Yes it does.

If it does appear imediatly after that...then it doesn't change by the steps mentioned earlier...

---

### Post by iaculallad on 2008-06-25
> **cristo-father said:**
> If it does appear imediatly after then it doesn't change by the steps mentioned earlier...

It will change since you released your old IP then obtained a new IP from your DHCP server (you're Router).

Obtaining IP upon releasing will not take a(n) hour to initialize after your restart your network daemon.

---

### Post by cristo-father on 2008-06-25
> **iaculallad said:**
> It will change since you released your old IP then obtained a new IP from your DHCP server (you're Router).

Obtaining IP upon releasing will not take a(n) hour to initialize after your restart your network daemon.

Doesn't work tryed several times...although  switching the power of my router than restarting my pc does.
Are there an apps that can do this automaticly(change my ip)?

---

### Post by Dr Small on 2008-06-25
Why do you need to change your network IP?
Also, you could try setting it to a static one, if you wanted.

---

### Post by cristo-father on 2008-06-25
> **Dr Small said:**
> Why do you need to change your network IP?
Also, you could try setting it to a static one, if you wanted.

Rapidshare downloading.

---

### Post by Dr Small on 2008-06-25
Changing your internal (LAN) IP won't help that then, unless I am mistaken.

---

### Post by Joeb454 on 2008-06-25
No Dr Small, you're correct, you would need to unplug you're router for a while to get a different IP address from your service provider (unless they give you a static IP address of course.

---

### Post by iaculallad on 2008-06-25
> **cristo-father said:**
> Doesn't work tryed several times...although  switching the power of my router than restarting my pc does.
Are there an apps that can do this automaticly(change my ip)?

Caution: I haven't tried this myself, so I don't know if it would work

I don't know if this is the application you're trying to say. What about installing ddclient to update your IP address.

```
sudo apt-get install ddclient
```

Try to edit the configuration file /etc/ddclient.conf

```
gksu gedit /etc/ddclient.conf
```

Save your changes and close the file. Restart your ddclient daemon.

```
sudo /etc/init.d/ddclient restart
```

---

