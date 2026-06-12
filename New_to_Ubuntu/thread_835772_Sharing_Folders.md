---
title: "Sharing Folders"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-06-20
Hello

I want to share a folder on my Windows network.  However, when I right click on the folder and click folder sharing I get the message:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

How do I overcome this?

Thanks

---

### Post by Hospadar on 2008-06-20
I think you might need to add yourself to the samba group.  Not totally sure that that's what is required, but give it a try.  System->Administration->Users and Groups

Also group adding can be done from the command line if you prefer, but I forget the command.

---

### Post by hellodoggie on 2008-06-22
Hello.

The method suggested does not work.:confused:

Is it possible to share a folder from the command line?

---

### Post by azurepancake on 2008-06-22
Try the following command in a terminal session..

```
sudo smbpasswd -a <yourUsername>
```

This is the other method of doing this. Hope it helps!

Edit: 

You CAN set shares manually from the 'smb.conf' file, located at '/etc/samba/smb.conf'..

```
sudo nano /etc/samba/smb.conf
```

Here you can add share definitions. I really recommend following this guide if you are going to get into Samba [http://samba.netfirms.com/](http://samba.netfirms.com/). I followed it to setup my Ubuntu file server and it worked great.

---

### Post by Flynsarmy on 2008-06-22
Open nautilus in root mode "gksudo nautilus". Then it'll work.

---

### Post by hellodoggie on 2008-06-22
gksudo nautilus = works great

THANK YOU!!!:KS

---

### Post by azurepancake on 2008-06-22
So 'gksudo nautilus' I suppose just opens up nautilus with root rights until you close it?

---

### Post by billgoldberg on 2008-06-22
> **azurepancake said:**
> So 'gksudo nautilus' I suppose just opens up nautilus with root rights until you close it?

Yes.

So don't go changing/deleting files you don't know.

---

