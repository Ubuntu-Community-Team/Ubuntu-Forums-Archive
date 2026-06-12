---
title: "Can't update Ubuntu and install app at the same time"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by magedsoft on 2011-09-11
hay every body : 

it's longtime since i posted here ... i miss all of you 

now 
some time i was updating ubuntu , and i want to install another program like vlc for example but i can't or i don't want to cancel the update and i want to install the other program .......


there is anyway brothers and friends to install two program at the same time in ubuntu 



thank you ......................

---

### Post by saltmarshlamb on 2011-09-11
No.

Once you've started one type of package management you need to wait for it to finish before the next can start.

You could though run a command to do it concurrently _for example_

sudo apt-get update &&sudo apt-get upgrade &&sudo apt-get install vlc

---

### Post by kvarley on 2011-09-11
When you are installing updates or an application Ubuntu locks access to dpkg.

So the simple answer is no, you can't install two applications at the same time.

However, applications let you make a queue of applications to install.

For example with apt-get:
> sudo apt-get install vlc flashplugin-nonfree chromium-browser

In synaptic you can "Mark" multiple packages.

In the Ubuntu Software Centre you can find an application and click the install button, then find another one and hit install and in the "Installing Software" option in the left column it will show you the queue.

Hope this answers your question!

---

### Post by The Cog on 2011-09-11
I don't think there is. I think you need to allow the update to finish before installing anything else. This is because two programs are not allowed to be doing package management at the same time. The authors have gone to some length to prevent it, so I guess there is good reason. Probably to avoid database corruption or conflicts between installer scripts.

---

### Post by magedsoft on 2011-09-11
thank you my friends ,for the answer, we love linux or ubuntu in egypt because the support we find it here ,ubuntu forum the sites that make us use ubuntu

---

### Post by oldos2er on 2011-09-11
I've given your thread a more descriptive title. If you feel the issue has been solved, please mark the thread 'Solved' under Thread Tools. Thanks!

---

