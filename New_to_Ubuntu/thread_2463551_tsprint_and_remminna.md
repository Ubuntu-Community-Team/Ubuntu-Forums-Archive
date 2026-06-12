---
title: "tsprint and remminna"
date: 2021-06-14
forum: New to Ubuntu
---

### Post by mithileshgrandhi on 2021-06-14
Hi,
I have installed ubuuntu yesteerday latest version. I have 2 problems.
1.I have problem in using  tsprint. After I install the package, it says "SystemTray is not supported" and "TSPrintClient started..."
2.How to copy files from windows RDP and paste themm in ubuntu desktop while using Remminna?

I have checked lots of videos in youtube and searched the internet for solutions. I am unable to find one.

Would be of great help if anyone could address the issue as it is creating loots of breaks in my work. Each time i want to print or copy, I am booting to  windows and using a pendrive to save them and then accessing them in ubuntu.

Regards,
Mithilesh

---

### Post by ActionParsnip on 2021-06-14
```

sudo apt-get install libfreerdp-plugins-standard

```
Source: [https://askubuntu.com/questions/601204/copy-and-paste-between-remote-sessions-using-remmina#604257](https://askubuntu.com/questions/601204/copy-and-paste-between-remote-sessions-using-remmina#604257)

---

### Post by ActionParsnip on 2021-06-14
Strange that people are RDPing to servers. Don't we use PowerShell now?

---

### Post by mithileshgrandhi on 2021-06-14
> **ActionParsnip said:**
> ```

sudo apt-get install libfreerdp-plugins-standard

```
Source: [https://askubuntu.com/questions/601204/copy-and-paste-between-remote-sessions-using-remmina#604257](https://askubuntu.com/questions/601204/copy-and-paste-between-remote-sessions-using-remmina#604257)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libfreerdp-plugins-standard

this is what i get after executing the command

---

### Post by dddman on 2021-06-14
Your leaving out a step I think.
[https://askubuntu.com/a/604257](https://askubuntu.com/a/604257)
Then update and install

Myself, I just run them concurrently.  I can copy and paste; drag and drop.
[ATTACH=CONFIG]288658[/ATTACH]
[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by deadflowr on 2021-06-14
libfreerdp-plugins-standard was removed from the archives for newer versions of Ubuntu (Ubuntu 20.04 and newer)
Only Ubuntu 18.04 still supports it.

---

### Post by mithileshgrandhi on 2021-06-18
> **dddman said:**
> Your leaving out a step I think.
[https://askubuntu.com/a/604257](https://askubuntu.com/a/604257)
Then update and install

Myself, I just run them concurrently.  I can copy and paste; drag and drop.
[ATTACH=CONFIG]288658[/ATTACH]
[https://www.virtualbox.org/](https://www.virtualbox.org/)

have done the process again...........not successful......still cant copy and paste

---

### Post by mithileshgrandhi on 2021-06-18
> **deadflowr said:**
> libfreerdp-plugins-standard was removed from the archives for newer versions of Ubuntu (Ubuntu 20.04 and newer)
Only Ubuntu 18.04 still supports it.

Thank you for the information....how do i proceed now to get this functionality available?

---

