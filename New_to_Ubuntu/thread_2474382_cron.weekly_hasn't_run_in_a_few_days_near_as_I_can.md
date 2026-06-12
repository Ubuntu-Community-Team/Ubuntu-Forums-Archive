---
title: "cron.weekly hasn't run in a few days near as I can tell. [problem was my own fail]"
date: 2022-04-27
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2022-04-27
Jammy. I rewrote my lvm tarball script to run under anacron (so I thought). This is the script.

[https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/lvmtar.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/shell/lvmtar.sh)

I've removed the extension in the filename. I've left the machine running for a couple days now without it running it's backup. I'm unsure of why it hasn't done it yet? I've always done manual crontabs but I'd prefer one where it will pickup if it missed it's runtime.

```
grep cron.weekly /var/log/syslogApr 24 06:47:01 homewrecker CRON[42165]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
```

The only line referencing that thus far in my syslog.

*EDIT* Marking solved. My own stupidity. Never bothered to make sure my rewrite worked. Fixed, running the run-parts manually now. It's running.... Gracias.

---

