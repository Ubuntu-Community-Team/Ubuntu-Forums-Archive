---
title: "Problem with /etc/ssh/sshd_config, only after reboot."
date: 2014-05-23
forum: New to Ubuntu
---

### Post by Simon_Rousseau on 2014-05-23
Hello everyone,

I recently reinstalled a SolusVM container running Ubuntu Server LTS version 12 to LTS 14. to hide my port 22 i went to edit the port on _/etc/ssh/sshd_config_ to a different port, i used vi for the file edit because it's a virtual private server.

I have been using this tutorial : [https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04](https://www.digitalocean.com/community/articles/initial-server-setup-with-ubuntu-12-04)

What could be different with LTS 14? 

Remote access with different port after editing file, and restarting SSH, but rebooting the server itself and i get connection refused on all ports.. I have reinstalled my VPS container 3 times to end up with the same result every time...

Thanks for the time you are taking to help me.

Regards,
Simon
CompTIA A+, Server+
HP APS on All PC lines (Laptop/Desktop/WS/Thin Clients, Servers, Blades)
Same for IBM :)

---

### Post by papibe on 2014-05-23
Hi Simon_Rousseau. Welcome to the forum ):P

Are you trying to ssh as root? The tutoria specifically disable ssh root login. You should use the other user.

If you are not comfortable using 'vi', I'd recommend using 'nano' instead.

Remember that you have access to the console through the Digital Ocean site (droplet > Access > Console Access), so you don't really need to reinstall it, but just undo the changes to the files.

As a general rule, I recommend making a backup copy of the file you are about to modify. For example:
```
cp -v /etc/ssh/sshd_config /etc/ssh/sshd_config.old
```
If something goes wrong, you don't need to remember the changes you made, but just reset all changes by recovering the backup file:
```
cp -v /etc/ssh/sshd_config.old /etc/ssh/sshd_config
```
Hope it helps. Let us know if you need more help with that.

Come here often and have fun.
Regards.

---

### Post by Simon_Rousseau on 2014-05-24
Sshd was not loading on boot, after some searching this is what i found : 
```
sudo update-rc.d ssh defaults
Default-Stop values (none)
 Adding system startup for /etc/init.d/ssh ...
   /etc/rc0.d/K20ssh -> ../init.d/ssh
   /etc/rc1.d/K20ssh -> ../init.d/ssh
   /etc/rc6.d/K20ssh -> ../init.d/ssh
   /etc/rc2.d/S20ssh -> ../init.d/ssh
   /etc/rc3.d/S20ssh -> ../init.d/ssh
   /etc/rc4.d/S20ssh -> ../init.d/ssh
   /etc/rc5.d/S20ssh -> ../init.d/ssh

```

i'm going to try again now!

---

