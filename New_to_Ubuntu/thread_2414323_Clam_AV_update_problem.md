---
title: "Clam AV update problem"
date: 2019-03-08
forum: New to Ubuntu
---

### Post by redpoppet on 2019-03-08
Hi everybody
I have installed ClamAV successfully but I am unable to get it to update.  I am using this command:

 sudo freshclam

but I keep getting this response:

ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

Obviously I have no idea what this is or I wouldn't be posting.  I have restarted the pc etc with no joy.

Can anybody help me with how I can get the latest virus database by getting past this?

Thanks for any help that is offered.

---

### Post by TechnoJunky on 2019-03-08
rename your log file.  It'll work after that.

sudo mv /var/log/clamav/freshclam.log /var/log/clamav/freshclam.log_old

---

### Post by oldrocker99 on 2019-03-09
Unless you're running a server that handles .exe files, you do **NOT** need ClamAV. Your system is far more secure than any version of Windows. I've never used ClamAV , and I have had **ZERO** malware incidents in 10 1/2 years. Relax.

---

### Post by redpoppet on 2019-03-09
Thanks for the replies.  I will take the advice of not needing it.  I did try the command line above, thank you for that, but it didn't work as I suspect it was supposed to.  But, yes, I will remove it.

---

### Post by vinayakmadiwalar9 on 2019-03-11
Hello Everyone,
 
[B]update virus database manually, you have to stop daemon by typing in CLI:
 First:

sudo /etc/init.d/clamav-freshclam stop

Now you can update virus signatures:
sudo freshclam -v

Finally, restart daemon with
sudo /etc/init.d/clamav-freshclam start






[/B]

---

