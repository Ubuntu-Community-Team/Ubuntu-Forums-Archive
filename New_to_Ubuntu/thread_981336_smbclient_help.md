---
title: "smbclient help"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by 65bit on 2008-11-13
Hi,

I have a legacy system running SCO 5.0.6 with samba / smbclient 2.2.6.  Our sys admin guy recently left and this task is defaulting to me - a definite non admin guy  :confused:

Files are being auto-dropped onto a windows machine to a share that I can see from the SCO box using smbclient.  I plan to setup an hourly cron job with an smbclient connect script and command to  (1) log in (2) mget the files and (3) delete the files from the share.

The complicating factor is that while I'm mgetting the files and before I process the delete, another file could arrive.  In that case, it's possible I could delete it without ever "mget'ing" it.

I'm looking for the best way to handle the above.  It seems if I could pipe a list of the directory contents back to the SCO server, I could then walk thru each file - one by one - get it and delete it.  This would ensure I only deleted a file after I had copied it over.

Is it possible to pipe / redirect the shared directory's contents to a file on the SCO box.  Or do it on the share through smbclient and then "get" that directory listing file to use to walk through?

If that's doable, is there a way to use smbclient to connect once to the share, then process multiple commands automatically, then disconnect?  Or is smbclient a connect / process one command / disconnect .... repeat .... repeat approach?  It seems I heard someone talking a few years back about a tool that maybe worked with smbclient to send multiple commands?

Any insight would be appreciated.

Thanks

---

### Post by handydan918 on 2008-11-13
Wow. Baptism by fire.

Not sure I grasp the full implications of your situation, but are you familiar with rsync? You could set up a cron job for off-hours and do incremental backups...

---

