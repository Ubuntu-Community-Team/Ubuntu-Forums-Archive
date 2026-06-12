---
title: "Block adult sites?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by brandoncolorado on 2008-10-26
How can I block adult sites in Ubuntu without having to manually add each site's URL?

---

### Post by forger on 2008-10-26
Stop them using opendns nameservers: [https://www.opendns.com/smb/start](https://www.opendns.com/smb/start)

If you have a router, the setup will be very easy :)

Then you login to dashboard and customize it: [https://www.opendns.com/dashboard/](https://www.opendns.com/dashboard/)

---

### Post by brandoncolorado on 2008-10-26
> **forger said:**
> Stop them using opendns nameservers: [https://www.opendns.com/smb/start](https://www.opendns.com/smb/start)

If you have a router, the setup will be very easy :)

Then you login to dashboard and customize it: [https://www.opendns.com/dashboard/](https://www.opendns.com/dashboard/)

Great!  Thanks for the info.  Do you use this?  Do you feel it is safe?

---

### Post by mfmbcpman on 2008-10-26
> **brandoncolorado said:**
> Great!  Thanks for the info.  Do you use this?  Do you feel it is safe?

Yeah, I use it and it blocks most sites I could think of. And, it blocks most proxies. The nice thing is being able to selectively block so many categories.

---

### Post by forger on 2008-10-26
You can't get safer than opendns :)
I use it for malware/phishing/spam link protection, but I suppose it does a great job for adult sites

---

### Post by brandoncolorado on 2008-10-26
According to the directions, I am supposed to type this in terminal:

gksudo network-admin

I typed this command and nothing happened.  I am using Ubuntu 8.10.  Is there a different command?

---

### Post by handydan918 on 2008-10-26
> **brandoncolorado said:**
> According to the directions, I am supposed to type this in terminal:

gksudo network-admin

I typed this command and nothing happened.  I am using Ubuntu 8.10.  Is there a different command?

Not familiar with this specific issue, but a lot of the info you find on the net about Linux is geared toward RedHat and/or Suse. Just because they are the commercial ones that most of the enterprises are deploying.

---

### Post by forger on 2008-10-26
> **brandoncolorado said:**
> 
gksudo network-admin

Usually typing 'network-admin' shows which package to install in order to get that command:
```
sudo apt-get install gnome-network-admin
network-admin

```

Edit: do **[COLOR="Red"]NOT[/COLOR]** use gksu or gksudo with network-admin anymore, the unlock button will be greyed out
Just type 'network-admin' or head to System > Administration > Network

---

### Post by brandoncolorado on 2008-10-26
Got it working guys!  Thanks, I love it.

---

