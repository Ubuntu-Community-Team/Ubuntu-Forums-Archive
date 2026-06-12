---
title: "How to disable authentication required popups"
date: 2024-02-08
forum: New to Ubuntu
---

### Post by jfevans331 on 2024-02-08
So I have a machine running 23.10 that I am trying to use as both a local NAS and a dedicated machine for Hamachi access from remote locations (Basic idea, free personal cloud service) It works great in testing, but every few minutes I get an authentication popup for SU access

"Authentication is needed to run `/usr/bin/systemctl/ restart logmein-hamachi.service"

There would be no way for me to input this password remotely, so I want to completely disable this feature. How do I go about doing this?

 THIS IS NOT POSTED IN THE RIGHT SECTION OF THE FORUM PLEASE PROVIDE GUIDANCE ON HOW THO GET IT THERE.

---

### Post by yancek on 2024-02-10
I'm not familiar with the software you are using but the solution lies in why the service needs to restart constantly.  Have you read the Getting Started Guide for Hamachi at the site from the below link?

[https://vpn.net/](https://vpn.net/)

You might edit the /etc/sudoers file to allow a normal user to run that specific program but I don't know that is the best solution nor if it is a secure solution.  Kind of doubt it.

---

