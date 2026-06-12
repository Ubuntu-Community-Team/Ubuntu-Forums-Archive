---
title: "UFW and Mount Command Delays when SSSD is running"
date: 2018-09-18
forum: New to Ubuntu
---

### Post by gstump on 2018-09-18
Hello,

My very first post to the Ubuntu Forums. Please advise if anything is amiss.

I've run into a question recently on Ubuntu 18.04 LTS related to a couple commands such as "ufw" and "mount" exhibiting delays of 30-40 seconds before completing successfully.  I've narrowed this down to occurring only when SSSD is running.  Before SSSD is installed or when the service is stopped, the commands such as ufw and mount, run and complete normally in a second or less.  When SSSD is started again, the delays return.  Perhaps other commands are also affected but I've not seen them yet.

Example commands are: 
sudo ufw status
sudo mount -a

Other sudo operations complete normally, without delays.

I'm curious if anyone has seen or heard of something like this, what may be some key areas to investigate further, and maybe how to resolve this situation.  Please let me know of any additional information that may be helpful.

Thank you
gstump

---

