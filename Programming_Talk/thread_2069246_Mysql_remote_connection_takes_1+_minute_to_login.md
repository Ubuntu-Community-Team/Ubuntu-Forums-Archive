---
title: "Mysql remote connection takes 1+ minute to login"
date: 2012-10-10
forum: Programming Talk
---

### Post by benkaiser on 2012-10-10
I have recently been trying to get my php development up and running on ubuntu (switching from mac) however executing a local php script that connects (using mysqli) to the remote database takes a significant amount of time. I have identified that it is definitely client side as when I boot up into mac on my dual-booted computer, it executed the page in a second or so (good considering my internet connection). I have also identified it is cross-site as in I have tried multiple websites I develop and they both take long time mostly a minute or more to run a simple connection and maybe a few queries (no big amount of queries or lots of queries in a loop).

One of the servers I have tested remote connecting to is a VPS with hostgator and the other a shared cloud hosting on redhat's openshift. However due to it seeming to be a client-side (on my localhost) problem I don't think that should help much.

I have looked at some other tutorials and problems other people had but they all had to do with the remote database not being configured for remote connections, nothing to do with a local problem.

Another bit of information is that I was using MAMP on mac and on the ubuntu installation I just separately installed PHP, Apache2, Mysql and PhpMyAdmin.

Thanks in advance

EDIT:

Fixed the problem, seemed that redhat openshift required port forwarding by "rhc port-forward -a <app_name>" and the reason I though it was occurring on the other server was because it would not connect to another remote mysql database whilst processing the first one (only processes one page request at a time maybe?).

---

