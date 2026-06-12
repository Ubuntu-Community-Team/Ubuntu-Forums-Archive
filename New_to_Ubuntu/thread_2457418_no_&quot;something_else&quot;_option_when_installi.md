---
title: "no &quot;something else&quot; option when installing linux"
date: 2021-02-01
forum: New to Ubuntu
---

### Post by archimedes-tf2 on 2021-02-01
hi there, im new to ubuntu and linux and i was installing because i got fed up of windows bloated-ness and annoying watermark that got buggy in fullscreen.
im dualbooting linux as i play a few vr games using windows and i still want to be able to use windows for other windows exclusive things, the thing is, i cant dualboot as there's no something else option so i can't partition my ssd

i'd also like to know a few of the basic shortcuts as i am so used to windows after using it for most of my life

---

### Post by tea for one on 2021-02-01
Are you looking for this?
[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-allocate-drive-space](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-allocate-drive-space)

Which version/flavour are you trying to install?

It is better to create free space with Windows tools and then allow the Ubuntu installer to create the file system.

Also, please digest the information here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by guiverc on 2021-02-01
We don't know what release or ISO you're asking about.

ISOs are available that use the
- ubiquity
- subiquity
- calamares
- *debian installer*

and "*Something else*" is an option in `ubiquity`, but is called "*Manual Partitioning*" in `calamares`.  Release also matters, as for example, Lubuntu used `ubiquity` & `debian installer` (selected by the ISO you used to install) for 18.04, but all releases since used `calamares`.

As you provided no release details, nor what ISO you're asking about - we cannot know what installer is used, thus what options you have available. In effect the options are there anyway, just may appear different (eg. the *Something else" *being called *"Manual*" (Kubuntu using `ubiquity` and skin), "*Manual Parititioning*") etc.

Did you verify your downloaded ISO as being perfect?
- [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

Did you verify your write to your installation media?
- [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) (*assuming 18.04 or before, it's automatic in recent releases*)

---

### Post by archimedes-tf2 on 2021-02-01
the version i am trying to install is 20.10 
i haven't verified my iso but i dont have access to it right now as in not at my desktop and I'm going to go to bed soon. i will verify it asap, ty for your help.

---

### Post by SeijiSensei on 2021-02-01
20.10 has only nine months of support.  20.04 is a "long-term support" release and will be supported for five years.  You should use that.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

ISO here: [http://cdimage.ubuntu.com/focal/daily-live/current/](http://cdimage.ubuntu.com/focal/daily-live/current/)

---

