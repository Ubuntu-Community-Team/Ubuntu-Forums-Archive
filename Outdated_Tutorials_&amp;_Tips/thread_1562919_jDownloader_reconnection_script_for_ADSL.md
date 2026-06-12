---
title: "jDownloader reconnection script for ADSL"
date: 2010-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jtarin on 2010-08-28
First you have to put pon and poff in: /etc/sudoers (change username to your username)


```
sudo
echo "username ALL=(ALL) NOPASSWD: /usr/bin/pon">>/etc/sudoers
echo "username ALL=(ALL) NOPASSWD: /usr/bin/poff">>/etc/sudoers
```


Then create a bash file with the following content (change dsl_provider to your dsl connection name if dsl-provider does not work.)


```
#!/bin/bash
sudo poff dsl-provider
sudo pon dsl-provider
```

Save as "reconnect" and place it in your jDownloader folder which is usually hidden in your /home/username directory 
Then make the script executeable

```
cd
chmod 755 reconnect
```


Then in jDownloader go to  settings -> reconnection -> change method to external tab -> select your bashscript ->  save

Mine takes about 13 seconds to reconnect. Hasn't failed once.

---

