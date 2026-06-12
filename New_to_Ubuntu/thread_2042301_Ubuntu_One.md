---
title: "Ubuntu One ?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by Greg Mueller on 2012-08-14
For about the last week when I go to shut down my computer is says Ubuntu One is running and not done doing whatever it is that it does. I don't recall having installed or told Ubuntu One to do anything. I don't even know what it really does. Can I just delete it under Synaptic?

How can I get it to just go away?

---

### Post by cryptotheslow on 2012-08-14
Ubuntu One is a Canonical supplied personal cloud storage facility. I think the basic option on sign up is 5GB for free. It allows you to synchronise files or folders between machines and mobile devices (Android and Apple iThingies).

By default it will keep /home/your-username/Ubuntu One synchronised but you can add any other folders you like to the list to be synch'd.

On Ubuntu 12.04 it is accessed either via the Dash or on the messaging menu (click the envelope) - not sure if that is the same on 11.04. If you start it up and have a look at the Settings menu you can disable the "Connect automatically when computer starts" option.

Otherwise, just search in Synaptic for ubuntuone and remove all the packages associated with it (there are quite a few) - just make sure to carefully check the complete list of packages it intends to remove in case it tries to take out things like the ubuntu-desktop meta package, that would be troublesome. If that happens cancel out and post back here if unsure how to proceed.

You can find out a bit more about Ubuntu One here: [https://one.ubuntu.com/](https://one.ubuntu.com/)

---

### Post by Frogs Hair on 2012-08-14
If you have synced folders all changes are uploaded to Ubuntu One if the content is modified. This is not done automatically unless you have set up sync so it weird _if_ it is doing this by its self. 

To stop syncing folders , right click the folder, and select stop syncing under the Ubuntu One selection in the context menu. As suggested you can remove the application. A synced folder will have a square box with a check in it.

---

