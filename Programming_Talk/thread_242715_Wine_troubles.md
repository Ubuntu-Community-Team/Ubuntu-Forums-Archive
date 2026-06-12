---
title: "Wine troubles"
date: 2006-08-24
forum: Programming Talk
---

### Post by penguinchrissy on 2006-08-24
When ever I try and run wine I always get these

Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\program.exe": Module not found
what is wrong and how can I fix it. ](*,)

---

### Post by ifokkema on 2006-08-26
Are you using a fake windows directory, or a existing Win install? Possibly, it can't access the path to the windows directory?

---

### Post by penguinchrissy on 2006-08-27
I do have windows installed on the computer so I'm assuming that its not a fake directory. If it can't access it how can I tell it to.

---

### Post by ifokkema on 2006-08-28
I assume then, you haven't gone through the configuration steps for Wine. Start up /usr/bin/winecfg and set the directory of the windows folder.

---

### Post by skymt on 2006-08-28
I've had the OP's problem even after running winecfg. The solution was to upgrade to the latest version of Wine, rm -r ~/.wine, and run winecfg again.

---

### Post by Anonii on 2006-08-28
> I've had the OP's problem even after running winecfg. The solution was to upgrade to the latest version of Wine, rm -r ~/.wine, and run winecfg again.

"sudo rm -r /home/<user>/.wine && wineprefixcreate" would update your ~/.wine perfectly, too ^_^

Well, upgrading was fine, but if the problem was in the ~/.wine you could have just fixed it with that command.

---

### Post by skymt on 2006-08-29
> **Anonii said:**
> "sudo rm -r /home/<user>/.wine && wineprefixcreate" would update your ~/.wine perfectly, too ^_^

Well, upgrading was fine, but if the problem was in the ~/.wine you could have just fixed it with that command.

I didn't communicate properly. The older version of Wine I had would hang when generating ~/.wine, even if I deleted it and started from scratch. After upgrading, it would hang trying to load my broken .wine, so I deleted it, ran winecfg to regenerate it, and it worked fine.

Clear as mud now?

---

