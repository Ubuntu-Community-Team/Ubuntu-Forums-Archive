---
title: "Unable to fix 'python3-pip' and python-psutil"
date: 2020-08-10
forum: New to Ubuntu
---

### Post by suryakrishnan1990 on 2020-08-10
[COLOR=#242729][FONT=Arial]Good Day,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have been tyring to work on an installation package.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]However, I came across two error which is not resolved, did some findings, but wasn't able to fix it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]May I seek some expertise to assist me in this.

[ATTACH=CONFIG]286665[/ATTACH]

Thank you.[/FONT][/COLOR]

---

### Post by deadflowr on 2020-08-10
Try
```
sudo add-apt-repository universe
sudo apt update
sudo apt install python3-pip python-psutil
```

---

