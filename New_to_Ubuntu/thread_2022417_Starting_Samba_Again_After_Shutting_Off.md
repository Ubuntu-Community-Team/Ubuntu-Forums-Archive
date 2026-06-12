---
title: "Starting Samba Again After Shutting Off"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by Nariborn on 2012-07-10
I went threw a video tutorial, setting up a guest share folder through samba, with guest permissions and such, and once I was done, by typing \\ubuntuserver (My hostname) I was able to view the folder.  

Now, after powering down and powering back up the machine, I can't access the folder anymore!  

I tried "sudo service smbd start" and it told me the job was already running.  I tried "sudo service smbd restart" and it still doesn't work.

Thanks!

---

### Post by Nariborn on 2012-07-10
I went threw a video tutorial, setting up a guest share folder through samba, with guest permissions and such, and once I was done, by typing \\ubuntuserver (My hostname) I was able to view the folder.  

Now, after powering down and powering back up the machine, I can't access the folder anymore!  

I tried "sudo service smbd start" and it told me the job was already running.  I tried "sudo service smbd restart" and it still doesn't work.

Thanks!

---

### Post by Nariborn on 2012-07-10
I went threw a video tutorial, setting up a guest share folder through samba, with guest permissions and such, and once I was done, by typing \\ubuntuserver (My hostname) I was able to view the folder. 

Now, after powering down and powering back up the machine, I can't access the folder anymore! 

I tried "sudo service smbd start" and it told me the job was already running. I tried "sudo service smbd restart" and it still doesn't work.

Thanks!

---

### Post by darksidedude on 2012-07-10
Hi, have you by chance tried 
```
sudo service smbd kill && sudo service smbd start
```

Samba can some times be a little picky about just using the restart command

---

### Post by critin on 2012-07-10
Post 6, step 5

[http://ubuntuforums.org/showthread.php?t=1972989](http://ubuntuforums.org/showthread.php?t=1972989)

Take note there are 2 separate commands.

(5) Restart samba
 	Code:
 	sudo service **nmbd** restart sudo service **smbd** restart 


hope it's relevant to your issue.

---

### Post by lykwydchykyn on 2012-07-10
Samba's clearly running, so the problem is elsewhere.

- If you run smbtree on the server, does it list your shares?
- If you try to access the shares using the server's IP address instead of name, does it work?
- Are you running a firewall?

---

### Post by Nariborn on 2012-07-10
I installed Samba, configured it and such, and it worked fine, my other computer running windows could access the folder.  

I then shut down my ubuntu server, and powered it back up.  Now I cannot access the folder.  

This is a home server, so I believe I am running dynamic ips. 

Is this the problem or is it something else?

---

### Post by papibe on 2012-07-10
Hi Nariborn.

Did you have success using the server's name or its IP address?

Regards.

---

### Post by CharlesA on 2012-07-10
If DNS is working correctly, IP to hostname resolution should be fine even with a dynamic IP.

That being said, I set servers to use a static IP or use DHCP reservations to get them the same IP via DHCP.

---

### Post by lisati on 2012-07-11
Threads merged.
Please do not start multiple threads for the same issue, it dilutes the community's ability to help.

---

