---
title: "Terminal problem?"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by dapps2 on 2014-04-01
Please could someone help me?

I have been trying to install Adobe Flash Player in a terminal using: sudo apt-get flashplugin-installer
 but all i get back is:

 dapps@dapps-Ubuntu:~$ sudo apt-get install flashplugin-installer
[sudo] password for dapps: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dapps@dapps-Ubuntu:~$

---

### Post by leclerc65 on 2014-04-01
Do you have another program like Synaptic opened ?
I would reboot the computer and start from fresh.

---

### Post by deadflowr on 2014-04-01
I agree, you might have either synaptic, software center, or update manager open.
Or the updater program is running a quick refresh in the background, to keep your package lists current.

Sometimes all it takes is a couple of minutes to let it run then it will be open for your use.

Otherwise a restart might help, as already stated.

Edit: I will also say that if this is a new install, perhaps see if any updates are available to install, and install them first.

---

### Post by dapps2 on 2014-04-01
Big thanks for the advice guys.
Have done as you suggested and everything is now going great!

---

### Post by oldos2er on 2014-04-01
Could you please mark the thread as 'Solved' under Thread Tools at the top of the page? Thanks.

---

