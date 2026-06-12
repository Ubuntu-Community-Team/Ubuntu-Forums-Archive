---
title: "User sessions running outdated binaries:  maketopsite @ session #2: brave"
date: 2023-07-12
forum: New to Ubuntu
---

### Post by maketopsite on 2023-07-12
Ubuntu 20.04, after firefox language pack upgrade:

```
# needrestart 
Scanning processes...                                                                                                                        
Scanning candidates...                                                                                                                       
Scanning processor microcode...                                                                                                              
Scanning linux images...                                                                                                                     

Running kernel seems to be up-to-date.

The processor microcode seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

User sessions running outdated binaries:
 maketopsite @ session #2: brave[53157,53182]
```

after closing brave-browser:
```
# needrestart 
Scanning processes...                                                                                                                        
Scanning candidates...                                                                                                                       
Scanning processor microcode...                                                                                                              
Scanning linux images...                                                                                                                     

Running kernel seems to be up-to-date.

The processor microcode seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.
```

after starting brave-browser:

```
# needrestart 
Scanning processes...                                                                                                                        
Scanning candidates...                                                                                                                       
Scanning processor microcode...                                                                                                              
Scanning linux images...                                                                                                                     

Running kernel seems to be up-to-date.

The processor microcode seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

User sessions running outdated binaries:
 maketopsite @ session #2: brave[53157,53182]
```

 Is please something other needed to close ?

---

### Post by ActionParsnip on 2023-07-12
When you close the browser, make sure no processes are hanging around with:
```

ps -ef | grep -i brave | grep -v grep

```
If there are processes, then kill them and restart the browser. You can do this via the PID (the left most number). Alternatively, you can simply reboot

---

### Post by maketopsite on 2023-07-12
> **ActionParsnip said:**
> When you close the browser, make sure no processes are hanging around with:
```

ps -ef | grep -i brave | grep -v grep

```
If there are processes, then kill them and restart the browser. You can do this via the PID (the left most number). Alternatively, you can simply reboot

```
# ps -ef | grep -i brave | grep -v grep
#

```

Same problem happens with firefox and happens **not** with palemoon. Reboot would surely solve it but I'm trying to understand what happened.

---

### Post by ActionParsnip on 2023-07-12
> **maketopsite said:**
> ```
# ps -ef | grep -i brave | grep -v grep
#

```

Same problem happens with firefox and happens **not** with palemoon. Reboot would surely solve it but I'm trying to understand what happened.

Are there any brave files or folders open still in the output of
```

lsof

```

You can grep the output to filter as you need

---

### Post by maketopsite on 2023-07-12
> **ActionParsnip said:**
> Are there any brave files or folders open still in the output of
```

lsof

```

You can grep the output to filter as you need

```
# lsof | grep -i brave
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse file system /run/user/1000/doc
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /home/maketopsite/.cache/gvfs
      Output information may be incomplete.
# 
```

---

