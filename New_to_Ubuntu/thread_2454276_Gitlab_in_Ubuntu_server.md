---
title: "Gitlab in Ubuntu server"
date: 2020-11-26
forum: New to Ubuntu
---

### Post by algavs on 2020-11-26
Hi guys, I have a gitlab hosted on Ubuntu.

I just rebooted the server, no change has been made and  Gitlab page is not showing up after reboot.

Any ideas?

Before the reboot the [https://192.168.0.20](https://192.168.0.20) was still online.

I run this:

[COLOR=#000000][FONT=Verdana]ss -ntlp nginx[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]shows that nginx is bind and listening to port 80


gitlab-ctl status shows this:

[/FONT][/COLOR]ok: run: gitaly: (pid 5392) 1s
ok: run: gitlab-monitor: (pid 5416) 0s
ok: run: gitlab-workhorse: (pid 5421) 1s
ok: run: logrotate: (pid 5431) 0s
ok: run: nginx: (pid 5512) 0s
ok: run: node-exporter: (pid 5520) 1s
ok: run: postgres-exporter: (pid 5530) 0s
ok: run: postgresql: (pid 5539) 1s
ok: run: prometheus: (pid 5544) 0s
ok: run: redis: (pid 5559) 0s
ok: run: redis-exporter: (pid 5565) 0s
ok: run: sidekiq: (pid 5572) 1s
ok: run: unicorn: (pid 5582) 0s

Any help is greatly appreciated. Thanks.
[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by TheFu on 2020-11-26
Check the system and nginx log files.

Always start any troubleshooting by looking at the log files. Always.

If you don't know how, search "ubuntu log file" and there is an article on help.ubuntu.com with an explanation.

---

### Post by algavs on 2020-11-26
Hi TheFu, thanks for the update.

It's a bit weird the error.log file is zero bytes. So, I really don't know where to start.

Any other ideas?

Thanks.

---

### Post by TheFu on 2020-11-26
There are multiple log files. Check them all.

---

### Post by ActionParsnip on 2020-11-26
If you SSH to the server can you telnet to localhost on port 443?

---

### Post by algavs on 2020-11-27
> **ActionParsnip said:**
> If you SSH to the server can you telnet to localhost on port 443?

i got connection refused, how to rectify? sorry doesn't know how to fix this. Thanks.

---

### Post by ActionParsnip on 2020-11-27
If you restart the git lab service, does it help?

---

### Post by algavs on 2020-11-27
nope i did gitlab-ctl reconfigure also did not help but it did reconfigured successfully

---

### Post by ActionParsnip on 2020-11-27
[https://gitlab.com/gitlab-org/gitlab-runner/-/issues/4112](https://gitlab.com/gitlab-org/gitlab-runner/-/issues/4112)

Does that help?

---

### Post by algavs on 2020-12-04
Hi @TheFy, @ActionParsnip,

Thanks for your help guys, i compared the settings of the problematic Gitlab with a machine that has a working Gitlab and I was able to solve the issue.

I compared the Gitlab.rb with the working one, and commented the settings that shouldn't be there.

Thanks all. Cheers!

---

