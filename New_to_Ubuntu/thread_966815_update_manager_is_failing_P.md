---
title: "update manager is failing :P"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Samueltehg33k on 2008-11-01
My update manager is being retarded. it hasnt gotten any updates since 19 days ago which is a shame because i really want intrepid. please help

heres a video to show what im talking about
[http://www.youtube.com/watch?v=oUqlQrR3wxw](http://www.youtube.com/watch?v=oUqlQrR3wxw)

---

### Post by oldos2er on 2008-11-01
What does it say under 'Could not download all repository indexes'? Have you tried changing servers?

---

### Post by taurus on 2008-11-01
Are you planning to upgrade from 8.04 to 8.10?

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by por100pre1 on 2008-11-01
Copy, paste and ENTER this command in Terminal (Applications> Accesories> Terminal):

```
sudo aptitude update && sudo aptitude safe-upgrade
```

and post the results...

---

### Post by Samueltehg33k on 2008-11-01
> **por100pre1 said:**
> Copy, paste and ENTER this command in Terminal (Applications> Accesories> Terminal):

```
sudo aptitude update && sudo aptitude safe-upgrade
```

and post the results...
this fixed it thanks

---

