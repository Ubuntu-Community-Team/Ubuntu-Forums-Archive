---
title: "Updates"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Tek-Noir on 2008-10-17
If I am set up as an admin on an ubuntu system and everyone else is just a desktop user do I have to log in before any system updates are applied and if so is there anyway around this so i wouldnt have to.

---

### Post by greg@localhost on 2008-10-17
You should provide some further clarification if you would like an answer to this.

For what it's worth at the moment, you would need to be logged in as *a* user to download updates.

---

### Post by Tek-Noir on 2008-10-17
Sorry about that, I'll try again.

Ok, if I am the administrator of an ubuntu system whereby I have full access to sudo etc, and everyone else on that system is just a Desktop user and dont have access to sudo, add/remove and synaptic. If a Desktop user logs in and there are updated that need to be downloaded and installed will that happen. If not is there anyway that I can make it happen without having to log in and apply the updates myself. I know you can set them to do download and install automatically but do I still need to be logged in to do this?

Does that help?


Thanks

---

### Post by greg@localhost on 2008-10-17
Thanks for the clarification - I'm not entirely sure what the state of play is with Ubuntu in particular, but in my experence with other distros, you need to be root or at least sudo to download updates.

---

### Post by Tek-Noir on 2008-10-17
Brilliant! 

Thanks for the help!

---

### Post by greg@localhost on 2008-10-17
No probs - don't hesitate to click on 'Thanks' at the bottom right corner ;)

Greg

---

### Post by stephanvaningen on 2008-10-17
I think that you can configure Ubuntu to install security-updates automatically. I'm not sure but:

isn't it a cron-job that sits in the background to do a (daily) check: frequency to be set up in System -> Administration -> Software Sources: tab Updates 

Also in that screen you see a radio-button group where you can let Ubuntu 'Install security updates without confirmation'

---

### Post by Dougie187 on 2008-10-17
Yeah, you should be able to set cron up to do "sudo apt-get update && sudo apt-get upgrade", also, if there are other people that you want to be able to install updates you can always add them to the sudoers or admin group.

But, if you just add a user to your computer and don't specifiy any usergroups then they will not be able to install any updates on that computer.

---

