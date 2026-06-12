---
title: "[SOLVED] Installing using Add/Remove and Synaptic"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by annamoo on 2008-10-13
Hello
I have been trying to install things using these programs but it doesn't work and just tells me to refresh without installing.
Please help!
Thanks

---

### Post by OldGrey on 2008-10-13
The first time you use these it usually asks you to refresh. Just do it and you should find that it all works after that.

---

### Post by NewJack on 2008-10-13
Here is a question.  Check your Software Sources.  Make sure that "CD Rom" is unchecked, then make sure the other repositories are checked off (Universe, Restricted, etc..).  

If you leave "CD Rom" checked and don't enable the other mentioned repos, it will show you the Repos available from the CD and always try & check for the Ubuntu CD to install from.  Since the CD Rom isn't present, it won't install the programs you wanted.

Hope that helped.

Joe

---

### Post by RequinB4 on 2008-10-13
> **NewJack said:**
> Check your Software Sources.

This is in system - admin - software sources, first tab

---

### Post by NewJack on 2008-10-13
> **RequinB4 said:**
> This is in system - admin - software sources, first tab

It would have helped if I added that.  Thanks!

Joe

---

### Post by annamoo on 2008-10-14
Thanks for your help dudes, it was checking for the CD so have changed that.  It doesn't seem to be able to connect to the internet to check for other software now that I have made the changes though and comes up with an error message saying that it has failed to download and I am not connected (my internet connection is fine).
Any ideas?
Ta

---

### Post by stephanvaningen on 2008-10-14
You say your internet connection is fine? 
Maybe check if the server to download from is reachable. What if you:
Go to System, Administration, Software Sources:
Go to tab Ubuntu Software (first tab)
At the drop-down-box 'Download from:', change the server to "Main server", or do: select 'Other' and on the dialog-box that appears: click 'Select best server' and wait the result: choose the proposed server (however my experience is that the main server is faster than a local (.nl in my case) server.

---

