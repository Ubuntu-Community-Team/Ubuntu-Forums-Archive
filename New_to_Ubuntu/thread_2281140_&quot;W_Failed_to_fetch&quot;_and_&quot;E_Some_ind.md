---
title: "&quot;W: Failed to fetch&quot; and &quot;E: Some index files failed to download&quot;"
date: 2015-06-04
forum: New to Ubuntu
---

### Post by roberto52 on 2015-06-04
[COLOR=#ff0000][I]W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found                              

E: Some index files failed to download. They have been ignored, or old ones used instead.[/I][/COLOR]

Hello everyone,
I'm totally new in Linux (Ubuntu 15.04). When I update by the terminal, those two come out.
Could anybody help me out, please??

Thank you in advance.

---

### Post by QIII on 2015-06-04
That means the url for that ppa has either been taken down or has moved.   Try removing it by disabling it in your package manager and then attempt the update again.

Are you using the Software Center to do your updates?

---

### Post by matt_symes on 2015-06-04
Hi

The two are related and show that there is no vivid ppa for tualatrix.

If you click on the link in your post above, you will see this page ion your browser.
> 
**Not Found**

 The requested URL /tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages was not found on this server.

 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at ppa.launchpad.net Port 80


The error is no a show stopper, so you can either leave it and see if they update the ppa for vivid or remove the ppa using ppa-purge.

EDIT:

You have speedy fingers QIII. :)

Kind regards

---

