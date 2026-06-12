---
title: "Apache localhost + userdir problem"
date: 2010-05-12
forum: Programming Talk
---

### Post by sarduwie on 2010-05-12
Hi,

I'm having 2 separate problems with my Apache installation...

The first one is when I'm trying to open [http://localhost/](http://localhost/) , I get a 'Save File' dialog:
[http://svenarduwie.be/localhost_opening.png](http://svenarduwie.be/localhost_opening.png)

The second one is a 403 Forbidden error when I'm trying to open [http://localhost/~sven](http://localhost/~sven) after setting up the userdir configuration. This is my userdir.conf file: [http://svenarduwie.be/userdir.conf](http://svenarduwie.be/userdir.conf)

Could anyone help me out with these problems? Thanks :)

---

### Post by sarduwie on 2010-05-14
First problem solved by reinstalling Apache, the second problem persists :( I have worked around it by using /var/www instead of /home/sven/Website , but I would prefer to be able to use the latter. Anyone any ideas? Thanks! :)

---

