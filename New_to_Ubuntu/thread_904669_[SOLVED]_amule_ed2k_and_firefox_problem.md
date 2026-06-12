---
title: "[SOLVED] amule ed2k and firefox problem"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by RolandFlagg on 2008-08-29
Hi all, I've been trying to fix this ed2k problem in firefox:
"Firefox doesn't know how to open this address, because the protocol (ed2k) isn't associated with any program."

I followed directions from both 
[http://ubuntuforums.org/showthread.php?t=195035](http://ubuntuforums.org/showthread.php?t=195035)
and 
[http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later](http://www.amule.org/wiki/index.php/Ed2k_links_handling#Mozilla_1.7_(or_later)_&_Firefox_0.9_(or_later))

Now the error message doesn't pop up, but it doesn't do anything else when I click it either, please help?

---

### Post by RolandFlagg on 2008-08-29
bump* Someone must know this

---

### Post by RolandFlagg on 2008-08-29
Sorry but I really need this solved. Bump again

---

### Post by RolandFlagg on 2008-08-30
I can't believe it, but I'm going to have to bump this again

---

### Post by RolandFlagg on 2008-08-30
bump again...

---

### Post by RolandFlagg on 2008-08-31
bump again

---

### Post by stanks on 2008-09-04
[http://forum.amule.org/index.php?topic=15604.0](http://forum.amule.org/index.php?topic=15604.0)

---

### Post by RolandFlagg on 2008-09-04
thanks but that didn't work...

---

### Post by stanks on 2008-09-05
It didn't work on my machine too, but try to open firefox Options menu and choose Applications. Then find edk and choose 'Ask every time'. After that it worked for me

---

### Post by stanks on 2008-09-05
Menu 'Edit' -> 'Preferences' - 'Applications' then search for Contect type ed2k and for action choose 'Always ask'

---

### Post by RolandFlagg on 2008-09-06
K thanks, it's really wierd actually, because when I chose "always ask", and afterwards when I clicked a ed2k link, it still didn't work when i chose "ok", so I went into "open with another application". Here I found the "ed2k" program, chose it, and it worked! looks like its because for some reason it was looking at the wrong "ed2k" or something

---

### Post by RolandFlagg on 2008-09-06
edit: Oops... I thought my last post didn't register and retyped it... sorry

---

### Post by sicofante on 2008-09-06
Thanks for the info here. I would like to add that there's no clue that the link has worked, until you open aMule and check the transfers list. In Windows, eMule is opened and the transfers list shown, so you get feedback. I guess I should ask the aMule developers to do something about this.

---

