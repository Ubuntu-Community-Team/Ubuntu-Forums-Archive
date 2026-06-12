---
title: "downgrading Firefox Add on Errors"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Shaded Spriter on 2008-05-18
I have downgraded Firefox from 3.0b5 to Firefox 2 and having problems installing Add ons - they come up with "not compatible with firefox 2.0.0.14" even if the add on is actually compatible (noscript for example.) I have tried uninstalling firefox and removing the /.mozilla/ directory in my home folder but It doesn't actually get rid of the problem...Is there any other folders I should try deleting?

---

### Post by hyper_ch on 2008-05-18
why not using ff 3 with the nightly build tester tools addon?

---

### Post by Shaded Spriter on 2008-05-18
I don't really see what that has to do with the problem.

But I downgraded to 2 for Addons which have/are not being upgraded regularly. I just used a add on which would be used a lot as an example in my post.

---

### Post by hyper_ch on 2008-05-18
most addons work with ff3 without a hitch... only the versioning in the addons keeps them from being loaded... so the nightly builder test tools addon helps on that

---

### Post by Shaded Spriter on 2008-05-18
I have installed Firefox3 again...and will you look at that...I am having THE EXACT SAME PROBLEM!

So I ask my question again - What other files/folders apart from the .mozilla folder in the home directory do I need to delete.

---

### Post by hyper_ch on 2008-05-18
~/.mozilla folder should be sufficient....

did you try to install the Nightly Tester Build addon first?

[http://www.oxymoronical.com/web/firefox/nightly](http://www.oxymoronical.com/web/firefox/nightly)

---

### Post by Shaded Spriter on 2008-05-18
For some reason it worked that time (7th time the charm I guess.)

I will check that extention you mentioned...If it helps with the add ons I want I will keep on 3b5.

---

### Post by hyper_ch on 2008-05-18
all of the addons I use work now.

---

### Post by vladi11 on 2008-05-18
After you remove Firefox 3 beta 5 ( by the way, yesterday was launched Firefox 3 release candidate 1), you should delete the ~/.mozilla folder (to view it, open nautilus, go to your home directory,choose show hidden files and there it is).
After that, you can install firefox 2 ( within synaptic) without any errors.

---

