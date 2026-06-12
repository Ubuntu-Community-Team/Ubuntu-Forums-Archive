---
title: "[SOLVED] Could not open lock file /var/cache/apt/archives/lock"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Madwida on 2008-10-20
Hi 

When running the following command in terminal: 

"apt-get autoremove && apt-get clean && apt-get autoclean" in order to remove unused packages (such as an obsolete kernel) I get the following output:  

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)

E: Unable to lock the download directory


I am running it as root

Thanks a lot!

---

### Post by tuxxy on 2008-10-20
Try giving the command root privs

```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```

---

### Post by a0u on 2008-10-20
> **Madwida said:**
> Hi 

When running the following command in terminal: 

"apt-get autoremove && apt-get clean && apt-get autoclean" in order to remove unused packages (such as an obsolete kernel) I get the following output:  

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)

E: Unable to lock the download directory


I am running it as root

Thanks a lot!

If sudoing doesn't work...
Only one package manager can be running at any moment; that "lock" error ensures that there are no conflicts between two programs for the same resource.
Make sure that you don't have the Update Manager, Synaptic, etc. running.

---

### Post by jken146 on 2008-10-20
Check that you have no other instances of apt running (apt-get, aptitude, synaptic, Add/Remove...)

---

### Post by arkara on 2008-10-20
If you do this like that
```
command && other command
```
you will need more than one sudos, like that
```
**sudo** apt-get autoremove && **sudo** apt-get clean && **sudo** apt-get autoclean
```

---

### Post by Madwida on 2008-10-20
I must have had synaptic open; I think that was exactly it.  And I even know that, too--but completely spaced it!  Thanks a lot

---

### Post by kim062 on 2010-02-22
why i cant login to my other acount in gyache???lately i can login but now i cant i dont know what happn...can u help me how to login and other acount in gyache on yahoo:confused::confused::confused::confused:

---

### Post by abhijeetkulkarni on 2012-01-12
> **tuxxy said:**
> Try giving the command root privs

```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```

This worked for me. Thanks.

---

