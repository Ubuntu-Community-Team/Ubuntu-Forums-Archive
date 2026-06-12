---
title: "How do you verify if your system has internet connectivity"
date: 2017-12-20
forum: New to Ubuntu
---

### Post by sanko50 on 2017-12-20
[COLOR=#000000][FONT=Verdana]What is the proper command to confirm that system has internet connectivity ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]wget[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ping[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]curl[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]or what ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]How do you test to verify  Ubuntu system has internet connectivity ?[/FONT][/COLOR]

---

### Post by again? on 2017-12-20
ping google servers (ctrl+c to stop)
```
ping 8.8.8.8
```

Also check DNS resolution is working.
```
ping google.com
```

---

