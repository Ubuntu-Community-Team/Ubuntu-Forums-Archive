---
title: "[SOLVED] do I have plone installed?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by r3bol on 2008-10-06
I've just installed plone via synaptic. I completed the wizard straight after the install, but I can't get any sign of life from it. 

I've tried opening a browser and pointing the URL to:
[http://localhost](http://localhost)
[http://localhost:8081/](http://localhost:8081/)
[http://localhost:8081/manage](http://localhost:8081/manage)
[http://localhost:8080/](http://localhost:8080/)
[http://localhost:8080/manage](http://localhost:8080/manage)

but no joy. 

Anyone had any luck with plone?

Thanks.

---

### Post by r3bol on 2008-10-07
Well maybe it wasn't a plone install after all. I uninstalled everything and tried the universal installer with this guide. 
[http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer/tutorial-all-pages](http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer/tutorial-all-pages)
Remember after the install to run...
sudo /opt/Plone-3.1/zeocluster/bin/startcluster.sh 
...which starts the Zope server. That nearly caught me out. 
Also check the prequisits. I didn't have g++ and make (i think) installed by default.

---

