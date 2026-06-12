---
title: "samba and web server confilct"
date: 2019-12-29
forum: New to Ubuntu
---

### Post by clu55ter on 2019-12-29
Hi all I have a fresh installation of Ubuntu 18.04.3 server edition on my home server, I installed samba an tested on my network and was able to see the shared folders from my windows and Android devices however I also needed to setup a local web server for which I installed Vesta control panel.

As soon as I installed and configured vestacp I lose the samba connection on the network.
 
I can see that both services are running but don't know why I can't access samba shared folder.

I've installed a fresh
1. copy of Ubuntu 18.04.3 server.

2. Installed and setup Samba using this guide: [https://linuxize.com/post/how-to-instal](https://linuxize.com/post/how-to-instal) ... ntu-18-04/
On step two I tested the samba connection on my local network windows 10 and android all samba files are visible.

3. Install and setup Vestacp [URL]https://vestacp.com/install/ , added a WordPress site. sites working well.
After the third step, I lose all connections to my folders set up on step two.

below is the log of my samba status:
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2019-12-28 23:56:01 UTC; 11h ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
 Main PID: 2529 (smbd)
   Status: "smbd: ready to serve connections..."
    Tasks: 4 (limit: 4915)
   CGroup: /system.slice/smbd.service
           &#9500;&#9472;2529 /usr/sbin/smbd --foreground --no-process-group
           &#9500;&#9472;2531 /usr/sbin/smbd --foreground --no-process-group
           &#9500;&#9472;2532 /usr/sbin/smbd --foreground --no-process-group
           &#9492;&#9472;2534 /usr/sbin/smbd --foreground --no-process-group


Dec 28 23:56:01 192.168.1.164.example.com systemd[1]: Starting Samba SMB Daemon...
Dec 28 23:56:01 192.168.1.164.example.com systemd[1]: Started Samba SMB Daemon.



Does anyone know how I can find the issue, please?

Thanks
Tony

---

### Post by SeijiSensei on 2019-12-29
Looks like vestacp might add a firewall? Have to allow connections to ports 137-139 and maybe port 445.

---

### Post by clu55ter on 2019-12-30
There were no conflicts it was just the Firewall ports were closed after adding samba to allowed ufw with the following command $ sudo ufw allow samba the shared folder appeared back on the local network.

---

