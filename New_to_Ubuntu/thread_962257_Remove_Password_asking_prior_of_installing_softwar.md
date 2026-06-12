---
title: "Remove Password asking prior of installing software"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by theamber on 2008-10-29
Hi, I removed the start up password but how can I change o remove when it asks for the administrative password before installing a program or changing settings. Is there any way to change that I am the only one using this system, thanks.

---

### Post by macogw on 2008-10-29
Uh, that'd fall under the "bad idea" category.  Then it'd be like Windows, where any old drive-by download that wanted to infect your computer with heaven only knows what kind of nastiness could do it very easily.  The fact that you need to authorize all software installations is a major part of what makes it so difficult for Linux to get viruses.  Though I guess rootkits are more likely than viruses since more of them exist for Linux than viruses do.  They're also quite a bit worse than your average virus because instead of just being annoying, some malicious person has complete and total control over your machine...like a botnet.

---

### Post by theamber on 2008-10-29
That make sense somehow in order to stops automatic installations of spyware and all but... If I am getting software from the net which I don't know what it contains to begin with what different does it makes if I am going to authorize it anyways. I just wanted to now if there is an easy way to change that at least when you are changing settings.

---

### Post by macogw on 2008-10-29
No, there isn't an easy way to change it, I don't think, and...well...you kind of do know where it comes from.  There are certain repositories which are trusted.  There are the official Ubuntu repositories you see listed in System -> Administration -> Software Sources.  Those are maintained by Ubuntu developers, so we know they're safe.  There's Medibuntu which exists for certain video and DVD codecs, and that's a well-trusted one.  Any other 3rd party repository you add...well, it's up to you to decide if you really trust the maintainer of that repository or not.  And random software downloaded from anywhere other than the official website for a project (preferably a project with a good reputation)...that's generally a bad idea.  

If you stick to the official repositories, the code's been checked, and it's safe.  It's other stuff where it's a judgement call.  The trouble is, without the authorization, you don't get to make that judgement.  Random malicious software can download and install itself without you ever knowing that anything at all happened...and that's bad.

---

### Post by blastus on 2008-10-29
You could probably try increasing the sudo timeout value. 

[http://ubuntuforums.org/showthread.php?t=685319](http://ubuntuforums.org/showthread.php?t=685319)

---

### Post by Samosurfer on 2008-12-26
> **theamber said:**
> Hi, I removed the start up password but how can I change o remove when it asks for the administrative password before installing a program or changing settings. Is there any way to change that I am the only one using this system, thanks.

If you can explain how you removed the initial startup password it would be highly appreciated!!!!!! Btw I agree with not disabling the synaptic ect. auth. passwords....If only to gaurd ourselves from ourselves!!!!!    Also looking for a way to disable the keyring password protect for mail notification also on startup....double trouble!!!!!!! This is for my friends Dell laptop btw.......thankyou

---

### Post by sportscrazed2 on 2008-12-26
yeah i wouldn't mind that either since i get most of my software from add/remove or synaptic anyway and everything else is usually something ive used before

---

