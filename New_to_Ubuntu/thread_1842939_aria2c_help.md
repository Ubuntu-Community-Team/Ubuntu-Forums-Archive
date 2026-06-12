---
title: "aria2c help"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by vasa1 on 2011-09-12
Firefox 6.02 + DownThemAll doesn't seem to work well nowadays to resume downloads from the point they were disrupted due to a net disconnection.

After reading about aria2c (CLI) in this forum, I'm trying it out using the version available from the Ubuntu repository. I have no problem in resuming downloads whether I break them with Ctrl+C or they break by themselves.

I have a question about one of the switches, "**_-xN_**" where **_N_** represents the number of connections to a particular server and can be as high as 16.

Without the switch, download speed was slow. I then tried with "-x6", the speed increased but the connections were only **4** and not **6**. I don't know why. Right towards the end of the download, the number of connections dropped to 3. Is that normal?

Just to be clear, this was my first download using aria2c and the command line looked like this with **x6** as the only switch:
user@user-Machine:~$ aria2c -x6 "http://sitename/pub/file.name"

---

### Post by madjr on 2011-09-12
sorry i dont use aria2 (i used to use aria)

but now i use better ones like fatrat or steadyflow

[http://www.omgubuntu.co.uk/2011/05/steadyflow-download-manager-gets-updated-for-natty-adds-subtle-improvements/](http://www.omgubuntu.co.uk/2011/05/steadyflow-download-manager-gets-updated-for-natty-adds-subtle-improvements/)

but first install the flashgot extension in firefox

---

### Post by vasa1 on 2011-09-12
I just came across a forum for aria2c:
-http://sourceforge.net/apps/phpbb/aria2/index.php-
It's quite active.

And this link is to the various options:
[http://sourceforge.net/apps/trac/aria2/wiki/UsageExample](http://sourceforge.net/apps/trac/aria2/wiki/UsageExample)

---

