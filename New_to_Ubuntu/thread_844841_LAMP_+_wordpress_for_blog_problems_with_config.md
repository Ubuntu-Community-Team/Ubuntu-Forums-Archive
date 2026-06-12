---
title: "LAMP + wordpress for blog problems with config"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by joe_l on 2008-06-30
Ok, here's the situation. I installed Ubuntu (LAMP install), then proceeded to install wordpress for my blog that I want to setup. Everything went/was kosher, until I made a change that I can not seem to trace for the life of me, and it's bugging the hell out of me b/c I can usually find my mistakes with some careful back-tracking.

Now, on to the problem. When I navigate to the URL of my blog [http://mydomain.net/apache2-default/blog](http://mydomain.net/apache2-default/blog)  I get redirected to  [http://myinternalserverIP/apache2-default/blog](http://myinternalserverIP/apache2-default/blog)

I can not find which conf file is the cause of this. Can anyone point me in the right direction please? Or, would this be better suited for the WP forums?

---

### Post by indytim on 2008-06-30
I suspect it is because you are running a local server only. If you want to open it up to the world, you'll have to do the DND-thinger.  You may want to cross-post to the Server discussion board for additional assistance.

IndyTim

---

### Post by indytim on 2008-06-30
Sorry it should have read DNS not DND (It's early here..)

---

