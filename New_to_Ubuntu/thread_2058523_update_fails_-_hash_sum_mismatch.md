---
title: "update fails - hash sum mismatch"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by thaitang on 2012-09-15
having a real beast of a problem updating my main pc (xubu 12.04). Unfortunately it only connects via dial-up to the internet. Yeah I know archic but it is what it is. Anyways, after checking for updates I generally use synaptic package manager to mark upgrades, save the download script and d/load using another compueter with high speed access. This has worked out alright, until recently when I keep getting a b2z hash sum error or some such and that not all updates could be processed.

I have tried running these commands recommended in another post:

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

But still no dice, I keep getting a package failing to download, and it remains in the /var/lib/apt/lists/partial dir.

I do not know if this is related to my other prob or not, but now in synaptic package manager I notice there are 11 broken packages, all libre office apps and vlc, and so the package manager refuses to mark any upgrades until the broken packages are fixed.

Any ideas what else I might try?

By-the-by, just a curious question, the sudo apt-get update, or checking for updates takes brutally long and now I can see there are some rather large files in /var/lib/apt/lists being d/loaded, brutally long and rather large for a dial up connection. Why are the update files so large? I have used dial up for a long time for at least one computer and never remember updates taking so long as they do in 12.04.

---

### Post by critin on 2012-09-15
What I would try if I was using dial-up, though it may not work in your case.
Do a little at a time.  Fix broken packages first in the terminal if you use the term.  On the update notification, uncheck everything, then go back and check a few at a time.  Try to get all that are for the same app.  For instance, libra.  They will be grouped together.  Let them download and install.  Then go for the next batch.  Of course that requires that they must refresh again.  not good.  

You might try setting it to download automatically, and then just install a few at a time.  That way everything doesn't have to be done in the same session.

Take the computer to a friend who has faster internet and update there.
> 
Anyways, after checking for updates I generally use synaptic package manager to mark upgrades, What about checking for upgrades on synaptic and mark for install only a few at a time until you're all caught up?  Marking one will also mark its dependencies, so you're sure to get it all.  

I can't answer the final question.

---

### Post by critin on 2012-09-15
> in synaptic package manager I notice there are 11 broken packages, all  libre office apps and vlc, and so the package manager refuses to mark  any upgrades until the broken packages are fixed.

Any ideas what else I might try?

Have you tried fixing them through synaptic?  In synaptic go to EDIT at the top menu and choose Fix Broken Packages.

---

