---
title: "[SOLVED] spell check in Open office 2.4, Australian English"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-05-31
This may have been posted, I DID look.
I want to be able to spell check my open office word processor documents, I could do it on my old install (just did a fresh install, because I was bored) and now I don't remember how I set up the dictionary. Can you please tell me how to set up open office, back to its spell checking glory.

thanks.

---

### Post by bumanie on 2008-05-31
Open the word processor. Go to Tools --> Options --> Languages settings. Then choose languages and set to Australian English. Then look under writing aids and check the things you want ie check a while typing etc.

---

### Post by barbedsaber on 2008-05-31
> **bumanie said:**
> Open the word processor. Go to Tools --> Options --> Languages settings. Then choose languages and set to Australian English. Then look under writing aids and check the things you want ie check a while typing etc.

I have done that, but still nothing, I would use abiword, but I am using synaptic already, and cant open 2 instances of it.

---

### Post by asrai on 2008-05-31
hop into synaptic and install the openoffice.org package (only the individual components are installed by default).  Then it will work :)

---

### Post by miraceti52 on 2008-06-03
Hi Guys  I have been having the same problem with OOO 2.4 on Ubuntu 8.04  The spelling checker just will not work. I have set the language to Australian, I have used synaptic to install openofficce.org to find that its already installed and with I try to add a dictionary with the wizard I get a small window that I cannot adjust. I'll attach a screenshot.   
Has anyone any ideas ?

Thanks

---

### Post by SonicSteve on 2008-06-03
> **miraceti52 said:**
> Hi Guys  I have been having the same problem with OOO 2.4 on Ubuntu 8.04  The spelling checker just will not work. I have set the language to Australian, I have used synaptic to install openofficce.org to find that its already installed and with I try to add a dictionary with the wizard I get a small window that I cannot adjust. I'll attach a screenshot.   
Has anyone any ideas ?

Thanks

I had this same problem, disable desktop effects /compiz
system>preferences> appearance > desktop effects and click none. 
retry the dicOOo wizard and it will likely work.

---

### Post by miraceti52 on 2008-06-04
Thanks heaps SonicSteve  !!  it worked like a charm :)

---

### Post by barbedsaber on 2008-06-04
Just a quick update of what I (the OP) did.
sudo apt-get install abiword

that worked for me :)

I realised that I like abiword better than OO.o, but thanks anyway.

---

### Post by Flynsarmy on 2008-06-04
> **SonicSteve said:**
> disable desktop effects /compiz
system>preferences> appearance > desktop effects and click none. 
retry the dicOOo wizard and it will likely work.

Is there a way to temporarily turn them off keeping your current settings? If i click 'none' in desktop effects then i want to turn them back on, all my custom settings are gone if i pick 'normal' or  whatever the super bloat mode is.

---

### Post by SonicSteve on 2008-06-04
> **miraceti52 said:**
> Thanks heaps SonicSteve  !!  it worked like a charm :)

You're welcome. I'm just returning the favor that so many others in this forum have shown to me. That's one area of strength we have here that we need to foster. When we help each other in the end we're all better for it.

---

