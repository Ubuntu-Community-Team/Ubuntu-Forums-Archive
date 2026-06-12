---
title: "Doubt about updates, what shall be installed?? ."
date: 2008-08-13
forum: New to Ubuntu
---

### Post by student21 on 2008-08-13
Hi 

I have a doubt and hope somebody can clarify for me.  My synaptic shows updates in 3 categories.  1) Recommended updates 2) Backports 3)Distribution updates.

I think I've enabled backports repository recently and that's why its showing updates from backports.  My question is should I stop with recommended updates or should I also make use of backports and distribution updates??  What is best for my system??

(I have 64 bit wubi installation ubuntu on hp laptop.)

---

### Post by viciouslime on 2008-08-13
Backports pose no danger, they're just newer versions of some software. if for some reason you find that the newer version is no good for you, you can always revert to the older version using synaptic too :)

Proposed updates are the only ones you want to avoid as a new user.

---

### Post by student21 on 2008-08-14
Hi 

Thanks for replying.  I suppose from your answer backports updates are safe.  Though you haven't mentioned about distribution update explicitly, I consider them safe also from your answer.

Can you let me know how will my synaptic manager show 'proposed updates' ---in what category or what name??

You've also mentioned that I can revert back to older version using synaptic manager.  Can you please give me one simple example to understand this-- how it'll be done?

---

### Post by JoshuaRL on 2008-08-14
> **student21 said:**
> Hi 

Thanks for replying.  I suppose from your answer backports updates are safe.  Though you haven't mentioned about distribution update explicitly, I consider them safe also from your answer.

Can you let me know how will my synaptic manager show 'proposed updates' ---in what category or what name??

You've also mentioned that I can revert back to older version using synaptic manager.  Can you please give me one simple example to understand this-- how it'll be done?

Distribution updates are that.  They update the whole distribution.  I'm guessing you're on Gutsy, and it's saying that Hardy Heron is available for upgrade.

To worry about proposed updates, you would first need to enable them in your software settings.  But it's probably better that you dont.

As far as reverting, you should see the older uninstalled packages showing up in Synaptic.  Mark the newer ones for removal, and install the older.  After you Apply that, you should be reverted back.  Pretty easy.  For instance, I have several kernels that are outdated.  But if I had any problems from a new kernel, I can just go back to an older one.

---

### Post by viciouslime on 2008-08-14
> **JoshuaRL said:**
> Distribution updates are that.  They update the whole distribution.  I'm guessing you're on Gutsy, and it's saying that Hardy Heron is available for upgrade.

To worry about proposed updates, you would first need to enable them in your software settings.  But it's probably better that you dont.

As far as reverting, you should see the older uninstalled packages showing up in Synaptic.  Mark the newer ones for removal, and install the older.  After you Apply that, you should be reverted back.  Pretty easy.  For instance, I have several kernels that are outdated.  But if I had any problems from a new kernel, I can just go back to an older one.

Exactly as JoshuaRL says, you only need worry abou proposed updates if you enable them from System/Administration/Software Sources. Unless you do this, synaptic won't know they exist :)

---

### Post by student21 on 2008-08-14
Hi Joshua and viciouslime

To clarify I've Ubuntu Hardy heron updated till this moment (I'm trying to put this version info. and configuration info. as a sticky signature with little success---I also don't know where I would find config. details regarding my system in hardy:().  Though I have latest version of hardy, my synaptic showed some 'rhino' as distribution update.  That's why I asked about it.

If the older packages were cleaned up, would still my synaptic show older versions?  If not then what would be the next step?

As an addition I should say that one problem has been solved regarding Kopete after I've enabled and installed the updates from backports today.  Before this update from backports, my Kopete used to show me all contacts offline despite some contacts being online.  So for now, backports updates have served me well:).

---

