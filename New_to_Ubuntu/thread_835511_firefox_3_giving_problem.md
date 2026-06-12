---
title: "firefox 3 giving problem"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by HunkieChan on 2008-06-20
everytime i download something. my firefox crashes right after it finishes downloading. and everytime i load videos on youtube or sites alike, firefox crashes. what can i do to fix this ? thank you

---

### Post by alexandremrj on 2008-06-20
Most problems of sites with flash in firefox are due to the use of the opensource flash plugin.

You may have to install the flashplugin-nonfree that downloads the Adobe flash plugins from their site.

In synaptic choose the flashplugin-nonfree package or in terminal:
 sudo apt-get install flashplugin-nonfree

---

### Post by paulderol on 2008-06-20
it may be an extension though, try disabling all of them and then replicate the conditions under which the problem occurs, then start turning them back on one at a time to see if it is a particular one. 

better question--

what extensions ARE you using? any weird, wonky, or otherwise obscure ones?

---

### Post by HunkieChan on 2008-06-21
> **paulderol said:**
> it may be an extension though, try disabling all of them and then replicate the conditions under which the problem occurs, then start turning them back on one at a time to see if it is a particular one. 

better question--

what extensions ARE you using? any weird, wonky, or otherwise obscure ones?

i am using the same extensions that i used with firefox 2 and i didnt have this problem. and about flash plugin.. i have the adobe one.. so i dont know whats causing this problem

---

### Post by alienexplorers on 2008-06-21
Where is your flash plugin at. Mine is in the .mozilla/plugins folder and flash works great.

---

### Post by ubuntuguru on 2008-06-22
> **HunkieChan said:**
> i am using the same extensions that i used with firefox 2 and i didnt have this problem. and about flash plugin.. i have the adobe one.. so i dont know whats causing this problem
even though you you used the same extensions in firefox 2 they may cause undesired actions in firefox 3.  try disabling all your extensions and try to replicate your issue.

---

