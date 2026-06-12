---
title: "Transmission permission denied with mounted samba directory"
date: 2019-05-04
forum: New to Ubuntu
---

### Post by sirbob77 on 2019-05-04
I have 2 Proxmox VMs on the same server (for learning purposes) - primary docker server (ubuntu 18.04 server) 192.168.1.108 and samba/storage 192.168.1.109


On the primary server, I have Transmission setup as a docker container. I am able to download when I have the volumes (in the docker-compose.yml) point to a local directory for complete and incomplete:
```
volumes:
      - /etc/localtime:/etc/localtime:ro
      - ${USERDIR}/docker/transmission-vpn:/data
      - ${USERDIR}/docker/shared:/shared
      - ${USERDIR}Downloads/completed:/data/completed
      - ${USERDIR}Downloads/incomplete:/data/incomplete
```
The above works just fine and Transmission can download just fine.


When I change the download location to a mounted samba share directory, it ceases to work and transmission just says "Permission Denied".
```
volumes:
      - /etc/localtime:/etc/localtime:ro
      - ${USERDIR}/docker/transmission-vpn:/data
      - ${USERDIR}/docker/shared:/shared
      - /mnt/smbmount/dls/complete:/data/completed
      - /mnt/smbmount/dls/dling:/data/incomplete
```


For samba, I've followed [this guide]("https://linuxize.com/post/how-to-install-and-configure-samba-on-ubuntu-18-04/") for setting up just the sadmin and users share on my samba/storage server.


Here is my smb.conf on the samba/storage server:
```
[users]
        path = /samba/users
        browseable = yes
        writable = yes
        guest ok = yes
        read only = no
        force create mode = 0660
        force directory mode = 2770
        valid users = @sambashare @sadmin
        force user = sadmin
        directory mask = 0775
        create mask = 664
```


Here is my fstab on my primary docker server:
```
UUID=2bd84936-de66-46f1-bdb5-8cc00c57cde0 / ext4 defaults 0 0
    /swap.img       none    swap    sw      0       0
    //192.168.1.109/users /mnt/smbmount cifs credentials=/home/cbody/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```


My .smbcredentials file has the username and password setup when making the samba stuff.


I've unmounted and remounted the share at each major point and troubleshooting step using both (not at the same time):
```
sudo mount -a
    sudo mount -t cifs -o username=sadmin //192.168.1.109/users /mnt/smbmount
```


I've looked around and have been banging my head for almost 3 days trying to get this to work, but have no had any success.


  [1]: [https://linuxize.com/post/how-to-install-and-configure-samba-on-ubuntu-18-04/](https://linuxize.com/post/how-to-install-and-configure-samba-on-ubuntu-18-04/)

---

### Post by TheFu on 2019-05-04
What do the samba logs show?  They are in /var/log/samba/ ...
Also, your direct mount command isn't using the same options as the fstab shown.  I'd make those the same and definitely specify the uid/gid as options in both.
 
I wouldn't assume that eth0 is correct.  Since systemd was introduced, all the ethernet device names have changed, sometimes they are forced to be unique by appending some of the MAC for the NIC.
That how-to guide seems overly complex for a simple share.  Do you need all the extra stuff - users, admin, all that other stuff?

---

### Post by sirbob77 on 2019-05-05
Seems to be working now...I shut my server down to move it after posting the question. Upon starting everything up a few hours later (primary server: started both VMs, ran docker-compose, sudo mount -a) (samba server: testparm) I tested it once more and transmission started to download things from ombi > sonarr. The transmission docker-compose.yml file is using
```
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - ${USERDIR}/docker/transmission-vpn:/data
      - ${USERDIR}/docker/shared:/shared
      - /mnt/smbmount/dls/complete:/data/completed
      - /mnt/smbmount/dls/dling:/data/incomplete

```
 The only change that I have noticed is on my primary server (with docker) is everything in /mnt/ is now other-writable (green background with blue text) according to some quick googling. If memory serves correct, they were not highlighted prior to moving the server.


Regardless, thanks for your help. In case there's something helpful to explain the cause prior in the samba logs from the samba server:

In log. there is this repeated for hours:
```
[2019/05/04 18:53:24.200929,  0] ../source3/param/loadparm.c:3350(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/sambashare failed. No such file or directory
[2019/05/04 18:53:26.216203,  0] ../source3/param/loadparm.c:3350(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/sambashare failed. No such file or directory
[2019/05/04 18:53:28.237241,  0] ../source3/param/loadparm.c:3350(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/sambashare failed. No such file or directory

```

In log.nmbd this:
```



[2019/05/04 18:53:22.542765,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'nmbd' finished starting up and ready to serve connections
[2019/05/04 19:06:17.007804,  0] ../source3/nmbd/nmbd.c:58(terminate)
  Got SIGTERM: going down...
[2019/05/04 19:06:17.052438,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'nmbd' finished starting up and ready to serve connections
[2019/05/04 19:43:36.268418,  0] ../source3/nmbd/nmbd.c:58(terminate)
  Got SIGTERM: going down...
[2019/05/04 19:43:36.346490,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'nmbd' finished starting up and ready to serve connections
[2019/05/04 20:59:52.498656,  0] ../source3/nmbd/nmbd_namequery.c:109(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.1.109 for name WORKGROUP<1d>.
  This response was from IP 192.168.1.105, reporting an IP address of 192.168.1.105.
[2019/05/04 21:02:27.358132,  0] ../source3/nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****


  Samba name server CBSTORAGE is now a local master browser for workgroup WORKGROUP on subnet 192.168.1.109


  *****
[2019/05/05 01:50:50.978902,  0] ../source3/nmbd/nmbd.c:58(terminate)
  Got SIGTERM: going down...
[2019/05/05 04:57:15.828267,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'nmbd' finished starting up and ready to serve connections

```

In log.smbd this:
```



[2019/05/04 18:53:21.969701,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections
[2019/05/05 04:57:18.365352,  0] ../lib/util/become_daemon.c:124(daemon_ready)
  STATUS=daemon 'smbd' finished starting up and ready to serve connections

```

The rest of the logs were empty.

As for the direct mount command I was running not being the same as my fstab, I'm not familiar enough with each to see how they are different unless the fstab content at the end can be added somehow to the command.
Also, was eth0 referenced in the info I gave - apologies, I've just started with this and linux not but two weeks ago.
Lastly, I'm not sure if I need all the users, admin, and the other stuff - I've gone over several samba tutorials, but most are just commands with vague descriptions that are already references contexts and other aspects I'm not really familiar with/aware of.

---

