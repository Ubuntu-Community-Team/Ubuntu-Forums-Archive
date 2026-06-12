---
title: "XAMPP not allowing Ubuntu to shutdown"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by 1grouchy on 2012-12-25
> I have a problem with shutdown/reboot machine. It freeze on LOGOUT  screen, almost every time, so for past few months I was doing that from  terminal and I MUST stop networking:

[SIZE=2][COLOR=DimGray]sudo /etc/init.d/networking stop
sudo shutdown -h now[/COLOR][/SIZE]The problem with freezing Ubuntu on Reboot/Shutdown is XAMPP .

If I try to Reboot/Shutdown while XAMPP server is still running problem occurs, when I stop XAMPP server first everything goes well. I tried on old and fresh installed system (old HDD is full of bad sectors because of many cold shutdowns so I replace it with a new one) and results are the same.

So idea now is to add script for auto stopping lampp when I choose to Reboot/Shutdown. I tried with following but no result:

```
$ sudo gedit /etc/init.d/lampp-stop.sh

And I added this command into the script
# Stop XAMPP
sudo /opt/lampp/lampp stop

$ sudo chmod +x /etc/init.d/lampp-stop.sh
$ sudo ln -s /etc/init.d/lampp-stop.sh /etc/rc0.d/
$ sudo ln -s /etc/init.d/lampp-stop.sh /etc/rc6.d/

$ sudo visudo       // added privileges for my username to execute command without sudo

# User privilege specification
root    ALL=(ALL:ALL) ALL
grouchy ALL=(ALL) NOPASSWD: /opt/lampp/lampp stop
```When I type** sudo -l**:
[COLOR=DimGray]User grouchy may run the following commands on this host:
    (ALL) NOPASSWD: /opt/lampp/lampp stop
    (ALL) ALL[/COLOR]

but something (maybe all, I don't know) in this steps is not right because this is not working. Anyone with the idea how to do this on right way?

---

