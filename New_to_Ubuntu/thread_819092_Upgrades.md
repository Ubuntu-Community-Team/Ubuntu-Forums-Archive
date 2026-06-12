---
title: "Upgrades"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Terry S on 2008-06-05
Hi

I have upgraded to Hardy Heron which went flawlessly. However TWICE now the system informed me I needed upgrades which I accept and I click UPGRADE after the upgrade process I find my Open Office has vanished. What is happening does it not like me anymore:) 

After the first time I reinstalled Open Office now for the second time it has been removed. The upgrade does say "this is just a partial upgrade" and gives a list of possible reasons.

Seriously, any help would be gratefully received.

Terry S

---

### Post by Xiong Chiamiov on 2008-06-05
Does OpenOffice.org actually get uninstalled, or just fail to launch for some reason?  Do you get any warnings if you install it via
```

sudo aptitude install openoffice.org

```
?
Next time you are asked to update, try running
```

sudo aptitude safe-upgrade

```
and see if it gives you any notices about package dependencies.

---

### Post by Bubba64 on 2008-06-05
> **Terry S said:**
> Hi

I have upgraded to Hardy Heron which went flawlessly. However TWICE now the system informed me I needed upgrades which I accept and I click UPGRADE after the upgrade process I find my Open Office has vanished. What is happening does it not like me anymore:) 

After the first time I reinstalled Open Office now for the second time it has been removed. The upgrade does say "this is just a partial upgrade" and gives a list of possible reasons.

Seriously, any help would be gratefully received.

Terry S

hold down alt and hit f2 and see if it is in the list and will run from there it may have somehow been removed from the menu. You an reinstall in synaptic if it is gone.

---

### Post by Xiong Chiamiov on 2008-06-05
> **Bubba64 said:**
> hold down alt and hit f2 and see if it is in the list and will run from there it may have somehow been removed from the menu. You an reinstall in synaptic if it is gone.
Running from a terminal window will actually give some messages (useful or not) if it is indeed installed, as opposed to a run command.

---

### Post by Bubba64 on 2008-06-05
> **Xiong Chiamiov said:**
> Running from a terminal window will actually give some messages (useful or not) if it is indeed installed, as opposed to a run command.

Since your willing to give help here what is the command option running open office does nothing on my set up even with sudo or any apt install.

---

### Post by Bubba64 on 2008-06-05
Sorry fellow poster we posted at the same moment and I didn't see your post.

---

### Post by Xiong Chiamiov on 2008-06-05
> **Bubba64 said:**
> Sorry fellow poster we posted at the same moment and I didn't see your post.
No fears.  Happens all the time to me.

---

### Post by Archmage on 2008-06-05
> **Terry S said:**
> The upgrade does say "this is just a partial upgrade" and gives a list of possible reasons.

I think there is the mistake. It seems that you are not getting all packages that you should get. Maybe there is something wrong with your sources.list.

---

### Post by Terry S on 2008-06-05
Hi 

Thanks for answering my post. Yes all Open Office has been uninstalled except Draw and Impress. I think there was some text after the upgrade but I just ASSUMED it was OK and agreed.

---

### Post by Terry S on 2008-06-05
Again thank you for answering my post I did as you asked ALT F2 and yes all of Open Office has been deleted except Draw and Impress. As you say I could reinstall from Synaptic as I did last time but I am curious to know why it got deleted.

---

### Post by Terry S on 2008-06-05
> **Archmage said:**
> I think there is the mistake. It seems that you are not getting all packages that you should get. Maybe there is something wrong with your sources.list.
Hi 

Once again thank you for answereing my post, your idea may be valid how do I check/update my source.list

---

