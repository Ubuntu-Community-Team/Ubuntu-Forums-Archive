---
title: "cpu problem on 16.10"
date: 2017-03-13
forum: New to Ubuntu
---

### Post by yassatoubab on 2017-03-13
Hi

I've recently installed Ubuntu 16.10 on a new Thinkpad. Everything was working fine until yesterday night.
Although I had no programs running the fans were working like crazy.
I switched off the laptop and let it be for the night. When I started up this morning the fans immediately started up as well.

I checked the cpu usage and apparently there is one processes that is using 100% op the cpu. It's a process called fwupd
I've tried rebooting but that doesn't change anything.

I read something about killing the processes but I think that requires using a root terminal. As I have no experience at all and am very likely to mess things up I'd rather not try that yet.

Is there any way safe way to stop this fwupd?

---

### Post by howefield on 2017-03-13
Could be this bug : [https://bugs.launchpad.net/ubuntu/+source/appstream-glib/+bug/1591868](https://bugs.launchpad.net/ubuntu/+source/appstream-glib/+bug/1591868)

Are you fully updated ?

You can kill the process from your terminal running top. Press K > enter the relevant pid number and press enter. Alternatively the command..

```
sudo killall fwupd
```

should do it.

---

