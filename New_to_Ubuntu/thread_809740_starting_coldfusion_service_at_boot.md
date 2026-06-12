---
title: "starting coldfusion service at boot"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by bistro on 2008-05-27
Hi

is there a way to start my coldfusion service when system starts, please? I thought it might appear in the services list once installed (as it does with a couple of other linux distros) but no such luck on this occasion.

Many thanks

Dave S

---

### Post by sayakb on 2008-05-27
What does this service do? Can you provide more details?

---

### Post by bistro on 2008-05-27
Hi 

it starts up the coldfusion server. To start from the command line I do:
cd /opt/coldfusion8/bin
./coldfusion start

Best wishes

Dave S

---

### Post by sayakb on 2008-05-27
Goto system->preferences->sessions
Press Add and add this to the command text area:
```
cd /opt/coldfusion8/bin;./coldfusion start
```

---

### Post by bistro on 2008-05-27
Hi

that's up and running, thank you very much for help!

Best wishes

Dave S

---

