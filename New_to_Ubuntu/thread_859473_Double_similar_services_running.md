---
title: "Double similar services running"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-14
Under Services, I see double entry for Actions Scheduler, Logging, and Power Management. I would like to know whether I have to keep them ticked as they are or I am free to choose between the two. I already disable both logging service but I'm not sure about Action Scheduler and Power Management. Which one should I disable? No wonder I see a few weird process entry in System Monitors.

---

### Post by bumanie on 2008-07-14
I believe unchecking the 'doubled up' entries won't cause any problems. If it does, you can always go and check them again - remember, unchecking is not uninstalling.

---

### Post by cariboo on 2008-07-14
If you look again you will see that what you think are the same services running twice,  are in fact different processes:

```
Power manaement acpid 
Power management apmd
Action Scheduler anacron
Action  Scheduler atd

```

Jim

---

### Post by wariskampar on 2008-07-14
I notice the different but don't they do the same things? I'm just curious if they peraform redundant jobs

---

### Post by iaculallad on 2008-07-14
Some processes are executed by the root command and at the same time can be executed by the authorized user. You could use the **top** terminal command to view who are using those active processes threads.

```
top
```

---

