---
title: "Chrome failed to launch"
date: 2017-08-16
forum: New to Ubuntu
---

### Post by suhailid on 2017-08-16
This is a first time for me to ubuntu... I have been installing chrome successfully but unfortunately, it failed to launch or can't be opened. I checked in terminal there was kind of notification "[2993:3027:0817/014731.474056:ERROR:browser_gpu_channel_host_factory.cc(103)] Failed to launch GPU process.
Created new window in existing browser session."

I have no idea what does it mean. Help me please !!!

---

### Post by Andreyshel on 2017-08-16
> [COLOR=#000000]Created new window in existing browser session."[/COLOR]
Looks like you have one instance already running.
what shows ```
ps -ax | grep chrome
```

---

