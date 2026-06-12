---
title: "Setting execute flags..."
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Boozel on 2008-10-02
Hey everyone, brand-new to Ubu (Hardy) and need a touch of help. I KNOW this is a really dumb question, but I've been searching for 30 minutes and can't get an answer and I really need to go. I'm just hoping I can get some help while I'm out. I'm currently installing ATI drivers for my Graphics card and have hit a hitch.

I'm working off of the guide here:[ https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)]( https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)) in the "From ATi.com" section. At one point it says to "make sure the ATi drivers have the execute flag first."

What is this, and how do I set it?:(

---

### Post by bumanie on 2008-10-02
You will be better off trying to install the restricted drivers that are in the ubuntu repositories. System --> Administration --> Hardware drivers. Click on the enable checkbox and the driver will be downloaded. Occasionally, these don't work due to peculiar system quirks, but this is rare. As a new user, this is the thing to try first.

---

### Post by mdszepher on 2008-10-02
> **bumanie said:**
> You will be better off trying to install the restricted drivers that are in the ubuntu repositories. System --> Administration --> Hardware drivers. Click on the enable checkbox and the driver will be downloaded. Occasionally, these don't work due to peculiar system quirks, but this is rare. As a new user, this is the thing to try first.

Also a good idea.  I'll leave my post up in case you still want to go with the original plan.



Though I am a bit limited in my knowledge of Linux, I believe the execute flag would be a file permission.  Files can have three permissions, read, write, and execute.

Find the file in question, right click, go to properties, and check the permissions tab.  Make sure the "Allow executing file as program" box is checked.  If it is, you should be set to go.  If it isn't check the box, apply the changes, and go from there.

---

