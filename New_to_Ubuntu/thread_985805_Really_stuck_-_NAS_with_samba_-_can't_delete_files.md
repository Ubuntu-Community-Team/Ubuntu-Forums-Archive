---
title: "Really stuck - NAS with samba - can't delete files"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Cereus on 2008-11-18
I'm really stuck and can't figure this out.

I have a NAS (DNA-323) that I am accessing from my ubuntu machine. I am currently accessing it as admin until I setup user accounts (smbmount //192.168.0.100/Volume_1 /home/MyShare).

The NAS has a bittorrent feature that I used to download some files.

The owner and group for these files is root root.

I can't delete them and I would like to.

I've read about (and tried) commands like sudo rm -r /home/MyShare/downloadfolder
or chown, or chmod and these won't work (and the reason is samba does permissions different) 

The next idea I have to try is to modify smb.conf  *ouff*

My questions are:

1) (desperate question) How do I delete these root owned files! How would I assign them the correct owner?

2) (any tips/links are welcome) Suggestions for how to set up my smb.conf, or how to mount so I don't have permission problems in the future.

Thanks,
Cereus

---

### Post by Cereus on 2008-11-18
So I asked the tech at work and got some more info.

I'm going to write this out in full so I can understand it and maybe help out someone else in the same position as me.

The NAS is a computer with a linux file system. Your computer is a linux computer too. Both computers have their own user accounts and their own roots etc.

Samba, as I have it set up, doesn't give me permission to manipulate the files as root on the NAS.

I need to access the NAS in such a way that I would have root permissions and then I can chown/chmod the root owned bittorrent related files/folders.

The problem lies with the DNS-323.

There is a hacker forum devoted to DNS-323:
[http://forum.dsmg600.info/index.php](http://forum.dsmg600.info/index.php)

The BitTorrent problem is a bug that DNS is aware of:
[http://forum.dsmg600.info/t2933-DLink-confirms-firmware-error-BitTorrent-data-cannot-deleted.html](http://forum.dsmg600.info/t2933-DLink-confirms-firmware-error-BitTorrent-data-cannot-deleted.html)

There are several work-arounds that have been discussed:
[http://forum.dsmg600.info/t2214-can%27t-write-to-delete-from-share.html](http://forum.dsmg600.info/t2214-can%27t-write-to-delete-from-share.html)

I'll update this post one more time with details of a solution once I find it.

Update: I found a page describing what to do about problems with cifs and shutdowns with the NAS and I thought I would link it here because it was a bit tricky to track down.

[http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

---

