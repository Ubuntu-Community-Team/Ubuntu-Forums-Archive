---
title: "Sharing Apache Config and Website files via NFS"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by freematrix on 2013-07-10
Hi, First post thanks! I hope you can assist.

I have an environment whereby I share files on an Ubuntu 12.04 Server. Folder that are shared are apache config files, website files  and  web access log files. There are 3 separate NFS shares 

exports
/Apache2/	172.31.249.0/24(rw,sync,no_root_squash,async)
/Sites/	172.31.249.0/24(rw,sync,no_root_squash,async)
/Awstats	172.31.249.0/24(rw,sync,no_root_squash,async)



I have then installed 2 separate Ubuntu Web Servers (12.04 Server) and have linked the apache folder and website locations to the NFS server. So /etc/apache is a soft link to the NFS share Apache and the same goes for Sites and Logs. So both web server would read the same config and site files and write logs to the logs share.

fstab
172.31.249.74:Sites   /Sites   nfs    rw   0       0
172.31.249.74:Apache2   /Apache2   nfs    rw        0       0
172.31.249.74:Awstats   /Awstats   nfs    rw        0       0



I then have a load balancer which then shares the requests between the 2 web servers and allows for even load on the web servers. Initially all seemed to work fine but I think the problem comes in with locks via NFS and I am hoping you can assist.

1) I find that more often and not now, when I boot both servers, the NFS maps after a few seconds but apache has stopped starting automatically. I am thinking to put the NFS into rc.local instead of fstab.
2.) I then start apache one by one on each server but when starting apache on the seconds web server I notice , the CPU load shoots up on all the web servers and the NFS server and the web pages stop loading until I shut down apache on 1 of the web servers. Then all turns to normal but obviously only one web server is running then. 

Not sure if the design is the best or I have an error with NFS sync or async but advice would be appreciated or it is just something obvious.

Thanks

---

