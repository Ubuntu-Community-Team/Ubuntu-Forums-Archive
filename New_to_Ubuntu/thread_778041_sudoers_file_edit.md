---
title: "sudoers file edit"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by gaby PR on 2008-05-01
What commando I can use to edit the sudoers file?

I tried as root but open as read only.

Thanks

---

### Post by Joeb454 on 2008-05-01
Take GREAT care when editing the sudoers file. You need to know how to use Vi really. The command is ```
sudo visudo
```

Credit to Oldsoldier for pointing out my mistake :)

---

### Post by gaby PR on 2008-05-01
I trying to edit the sudoers for make firestarter start without enter root password.

If really necesary have firestarter?

---

### Post by Oldsoldier2003 on 2008-05-01
> **Joeb454 said:**
> Take GREAT care when editing the sudoers file. You need to know how to use Vi really. The command is ```
visudo
```

ironically its 
```
sudo visudo
```

---

### Post by Joeb454 on 2008-05-01
Not really, firestarter is a graphical application for editing the iptables firewall. However I've never found any real need to edit it. If you want to be extra secure with your connections then go ahead and use it :)

Edit: My mistake - corrected the post above

---

### Post by noynac on 2008-05-01
> **gaby PR said:**
> ...If really necesary have firestarter?

You may want to try Ubuntu Firewall:

[http://doc.ubuntu.com/ubuntu/serverguide/C/firewall.html](http://doc.ubuntu.com/ubuntu/serverguide/C/firewall.html)

To activate it, open a terminal window and type:

```
sudo ufw enable
```

---

### Post by Anduu on 2008-05-01
As Joeb said Firestarter doesn't need to be running.If you need to open ports etc for certain apps you would use Firestarter to do that.

Take my advice...leave your sudoers file alone.

---

