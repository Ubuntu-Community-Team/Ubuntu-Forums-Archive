---
title: "firestarter"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by DarinB on 2008-06-13
i never bothered to look at the boot process, but i just noticed a Fail for firewall start up.
i installed firestarter from the repos.
it is enabled...so now what do i do?????
it shows received 25.4MB sent .7 MB Activity 0
????? i have had this thing installed and enabled for months????

---

### Post by _sphinx_ on 2008-06-13
I was just wondering how do you know for sure that your firewall has failed to start up.

---

### Post by DarinB on 2008-06-13
i am running hardy and at boot up the list that goes by has a red Fail next to starting firewall.
i never saw that before but maybe i never looked.
i simply installed firestarter and enabled it then closed it

---

### Post by hyper_ch on 2008-06-13
> **DarinB said:**
> i never bothered to look at the boot process, but i just noticed a Fail for firewall start up.
i installed firestarter from the repos.
it is enabled...so now what do i do?????
it shows received 25.4MB sent .7 MB Activity 0
????? i have had this thing installed and enabled for months????

What do you need a firewall for?

Firestarter IS NOT a firewall.

The firewall is integrated in the kernel and runs all the time - by default just not with any rules.

---

### Post by DarinB on 2008-06-13
so what is firestarter

---

### Post by hyper_ch on 2008-06-13
> **DarinB said:**
> so what is firestarter

Did you search the net, wikipedia, .... already for it as to what it could be?

---

### Post by TrackTrack on 2008-06-13
> **hyper_ch said:**
> What do you need a firewall for?

Firestarter IS NOT a firewall.

The firewall is integrated in the kernel and runs all the time - by default just not with any rules.
Ture....................
But if you want a simple simple FireWall, AVG had a free on, and easy to install, But i mean you don't have to go with AVG, i just think it's good and about the best "Don't bash me for the word best" it is to me so yeah


hope this is help's i know some other's if you need Links just ask

---

### Post by brdokoky on 2008-06-13
When you need firewall just write in terminal

**sudo ufw status**

You'll see if si loaded and than just write

**sudo ufw enable**

If you need to know more just write

**ufw man**

---

