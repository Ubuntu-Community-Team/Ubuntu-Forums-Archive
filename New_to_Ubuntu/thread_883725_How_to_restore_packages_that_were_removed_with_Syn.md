---
title: "How to restore packages that were removed with Synaptic &quot;Mark for Complete Removal&quot;"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by mickeythecat on 2008-08-08
In Synaptic Package Manager, I accidently selected "Mark for Complete Removal" instead of "Mark for Removal".

Now I want to reinstall the package; however in Synaptic, that package is no longer even listed so there is no way for me to select it.  I can see from the Synaptic history window that I had deleted it, but other than that I do not see an option for getting it back.

From internet searching, I tried:
sudo apt-get install ubuntu-desktop

but this did not help.

Question is:
How do I recover/restore the list of all Packages in Synaptic that I have "completely removed"?

---

### Post by coffeecat on 2008-08-08
Something not right there. Completely removing packages instead of just removing them uninstalls the package **and** removes the .deb file from the apt cache. It might get rid of a bit of cruft as well, but it shouldn't remove the package name from Synaptic. I just tried this with zzuf (not an app I have much use for :wink:). I installed it, completely removed it and it's still there in the Synaptic package list waiting for me to reselect it for installation.

Try closing and restarting Synaptic. Try clicking on 'Reload' to update the package metadata.

Was that 'ubuntu-desktop' you completely removed? That shouldn't be a problem. Ubuntu-desktop is only a metapackage to pull in all the constituent parts of the Ubuntu Gnome desktop. Or were there some other packages you removed completely?

---

### Post by markjensen on 2008-08-08
It might help if you could confirm what package, exactly, you removed.

---

### Post by mickeythecat on 2008-08-08
I tried Reload and I restarted Synaptic - missing package (songbird) still not listed.

Based on two posts that answered, this may be my screwup.  I removed songbird using Synaptic; however it may be that I had installed songbird NOT using Synaptic - not sure.  If that was the case, may be likely that once it is removed it would not be listed in Synaptic (not in a repository?).

In any case, I looked more extensively through by Synaptic history and found other packages I had removed and they are listed in Synaptic now.  So for now this appears to just a problem with this particular package - songbird.

If anyone can confirm that packages NOT installed through Synaptic would then disappear from Synaptic when the package is removed, that would be great, otherwise I will just assume that is the cause here.


Per my Synaptic History for today:
Commit Log for Fri Aug  8 04:43:12 2008

Completely removed the following packages:
songbird


Thanks.

---

### Post by markjensen on 2008-08-08
That seems reasonable.  I've not played around with it, but synaptic will show all packages in the repos.   If you have a package installed manually with a .deb, I am not 100% sure if it will show (and I am not at my Linux box to verify).  But if it is listed, and you remove it, synaptic will no longer know about the package because it was removed and it isn't in the repos.

I guess the trick will be to see if there is a repo that has songbird.

---

### Post by billgoldberg on 2008-08-08
Songbird is not in the Ubuntu repositories.

If you completely removed it from the system, you'll need to download it again and install it yourself.

---

