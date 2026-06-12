---
title: "Question about Auto Updates"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by BGThree on 2008-05-11
Is it correct/safe to always install the updates whenever the manager in the taskbar notifies you that updates are ready?  A lot of the time I don't really know what they are for but I install them because it says to.

Are these updates always safe?  Do the repositories you have make a difference?

Thanks!

---

### Post by louieb on 2008-05-11
Depends on what your comfort level is. As long as you stick to the official repositories the updates have gone through some type of review process.  Having said that if you stick around the forum long enough  you will see threads about updates breaking systems. The 1st one that got me was an xorg update in 6.06.1. 

I just generally install them unless its an update to xorg or a kernel update. Then if I think about it I'll wait a day or two and check the forum and see if there are threads about the update breaking stuff.

If your using some 3rd party repository then you guess is a good as mine if the update is safe to install.

---

### Post by Shazaam on 2008-05-11
Security updates are a must do. Others can wait if you want. Use the Ubuntu approved repos and you will be fine. Use other repos only if you trust them.
I never have auto-download enabled. I have it set to just show me the updates so I can make a choice.

---

### Post by dizee on 2008-05-11
Generally it should be safe. You can click on the arrow beside "Description" to see what the updates do - usually they are security updates. The only real risk is if you are upgrading to a newer kernel. You can may up needing to reinstall graphics drivers for the new kernel (or occasionally your hardware might not work as well as it used to).

You should only really use the main Ubuntu repositories. There is a lot more potential for breakage when updating programs from third-party ones.

---

### Post by mmb1 on 2008-05-11
Like others have said, its generally safe. However, most of the time, (unless its an important security update or something vital) its fine to wait a few days to see if anything breaks.  I had a 7.04 system break on me due to an X update.

Its handy to know the terminal command to update, just in case you get stranded at the CLI:

sudo apt-get update

---

### Post by BGThree on 2008-05-11
Thanks everyone!:guitar:

---

