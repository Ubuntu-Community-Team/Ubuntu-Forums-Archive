---
title: "[SOLVED] No (requires plugins) dialogue in firefox 2"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by jarl69 on 2008-06-24
Hello.
  I have set up ubuntu on a second computer When I point firefox to a site that requires flash, I get nothing. On my other setup, I was prompted with a dialogue which directed me to a download missing plugins screen.
 Any ideas how I can get this dialogue to appear, or at least install flash/gnash by other means.
 Thanks in advance

---

### Post by charbo on 2008-06-24
Hi,

Which version of Ubuntu are you using?

Regardless, I think the package to install is called 
flashplugin-nonfree.

I am not at a ubuntu system, so I am not 100% sure, but, try the following:

Go to the System menu on top bar of your desktop, choose Administration, and at the bottom there should be Add/Remove software.  Run that, and search for flashplugin-nonfree, and install it from there.

The following site shows you how to install without the package, but not recommended.  

[http://www.psychocats.net/ubuntu/flashmanual]("http://www.psychocats.net/ubuntu/flashmanual")

Hope this helps.

---

### Post by RomeReactor on 2008-06-24
Hi. Also make sure you don't have Gnash installed; close Firefox, open Synaptic (System->Administration->Synaptic). If mozilla-plugin-gnash is installed, uninstall it. Close Synaptic, and open Firefox again to see if you are asked to install Flash, or if it's already installed, see if it works now.

---

### Post by jarl69 on 2008-06-24
Thanks for the help, That got it working, Nice one!

---

