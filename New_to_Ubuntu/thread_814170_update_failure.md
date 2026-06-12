---
title: "update failure"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by PatronSaint on 2008-05-31
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.



Is everyone getting that message when they do an update!? I can't figure out why I would get that, or worse...why my machine won't install any updates.

---

### Post by shifty_powers on 2008-05-31
it's happned to me. just wait a few hours, and then try to update again

---

### Post by PatronSaint on 2008-05-31
Thanks shifty, I didn't know if I downloaded something crazy, installed something I shouldn't have or what. 

I'll wait, thanks again! :)

PatronSaint

---

### Post by shifty_powers on 2008-05-31
what happens when you try

```
sudo apt-get update && sudo apt-get upgrade
```

in a terminal?

please post the treminal output ;)

---

### Post by PatronSaint on 2008-05-31
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by Joeb454 on 2008-05-31
Are you in the US by any chance? I know some US users are having issues with the sources.list today

---

### Post by PatronSaint on 2008-05-31
Yeah, I'm in the US. Do you think that's it? I hope I didn't install something that is preventing this from working. 

When I click on the update manager, it tells me:

NOT ALL UPDATES CAN BE INSTALLED

Run a partial upgrade, to install as many update as possible. 

This can be caused by:
A previous upgrade that didn't complete (that's never happened)
problems with some of the installed software (i hope not)
unofficial software packages not provided by Ubuntu (i hope not)
normal changes of a pre-release

I click on partial upgrade and get what I first posted.

---

### Post by Joeb454 on 2008-05-31
oooohh...

Does it leave the OpenOffice updates?

---

### Post by PatronSaint on 2008-05-31
Yeah...all the open office ones are not checked. It's all jacked up.

---

### Post by Joeb454 on 2008-05-31
I think that the packaging of the OOo updates must have failed or not synched correctly then, a lot of people are getting this issue.

Just leave it for now, and if it isn't resolved in a couple of days, then bump your thread back up :)

---

### Post by PatronSaint on 2008-05-31
Alright mate, thanks. 

I hope it's straightened out in a few days. 

Thanks again for the replies!

---

### Post by PatronSaint on 2008-06-02
BUMP...

Still have the same problem. Anyone have any ideas?

---

