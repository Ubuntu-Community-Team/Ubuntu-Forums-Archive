---
title: "newbie with ubuntu 8.04 - Novell server problem."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by jr1957 on 2008-08-01
Need help please, a newbie to Ubuntu. I believe I was successful in mounting my Novell volume, but I don't see any files or folders in Novell. I followed the instructions in this link: [http://useopensource.blogspot.com/2007/01/how-to-mount-novell-network-drives.html](http://useopensource.blogspot.com/2007/01/how-to-mount-novell-network-drives.html). Your reply & assistance will be appreciated! (P.S. I've researched enough to realize there is no easy or supported Novell Client to use with Ubuntu. Too bad for me.) Thanks! :frown:

---

### Post by LowSky on 2008-08-01
you need to include your Novell user name in the command
```
ncpmount -S [yourservername] -A [serveraddress] -U $USERNAME -V [volume] -u $USERNAME [mount directory]

```

Also have you installed SAMBA?

---

### Post by jr1957 on 2008-08-01
> **LowSky said:**
> you need to include your Novell user name in the command
```
ncpmount -S [yourservername] -A [serveraddress] -U $USERNAME -V [volume] -u $USERNAME [mount directory]

```

Also have you installed SAMBA?
Hi LowSky, thanks for your reply. My Novell Tree is REINDERS_SOHO, my server name is SOHO and my volume name is SOHO_SYS. My apology but I'm inexperienced in Ubuntu command line strings so I do not fully comprehend the code example you provided. Does this look correct? ncpmount -S soho -A reinders_soho -U $joer -V soho_sys -u $joer soho_sys.

And yes SAMBA is installed.

Thanks again and I look forward to your reply.

---

### Post by Augsburg on 2009-05-05
have you tried ncplogin?

ncplogin -S REINDERS_SOHO -A REINDERS_SOHO -U .joer.REINDERS_SOHO -P <passwd>

I'm don't know if this will mount your specific volume, though.  When i used it, it mounted the actual server stuff and not my folder.  Then i used curlftpfs instead.

---

