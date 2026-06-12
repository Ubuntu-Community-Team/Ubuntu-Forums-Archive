---
title: "Digg  API tiny problem Phyton"
date: 2011-07-18
forum: Programming Talk
---

### Post by mikedemon on 2011-07-18
Can you please help with the following code
 
 
```

from digg.api 
import Diggdigg = Digg()
 
li=["usq1111"] 
 
for user in li: user= digg.user.getDugg(username="usq1111",count=1) 
    print user['users']['usq1111']['title']
 

```
Getting error: KeyError: 'users' , Want to see the latest items myfollower dugg. From version 1.
 
Can you mix version 1 and 2 in a single program.

---

