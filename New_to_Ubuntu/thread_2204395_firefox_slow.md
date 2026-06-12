---
title: "firefox slow"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by pyrforos on 2014-02-08
Hi  community !
my  problem  is this : 
 While firefox and Rekkong became (i  cant  remember when  that happened ) suuuuuuper slow  chromium   is super fast.. We are talking about  30-50 sec slower for every  page... 
I don't like using  chromium and i'm a big  fan of firefox  so  i purged everything  with :


sudo apt-get purge firefox

Delete .mozilla/firefox/ 

Delete .macromedia/ and .adobe 

Delete /etc/firefox/, 

Delete /usr/lib/firefox/ 

Delete /usr/lib/firefox-addons/ 

as suggested here : [http://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed](http://askubuntu.com/questions/16758/removing-firefox-in-ubuntu-with-all-add-ons-like-it-never-existed) , thinking that  there might be something with my plugins. So i  reinstalled firefox with no plugins  and guess...  same thing...
am i missing something?

---

### Post by ajgreeny on 2014-02-08
Try renaming your hidden .mozilla folder as a backup to see if FF suddenly starts working at speed again.

If it is fine with a new profile, then it is something in your current profile that is corrupting the application's working; usually an add-on or plugin, but in view of you final comment that seems unlikely.

---

### Post by pyrforos on 2014-02-09
i also  tried  to  download the .tar package from  firefox site but same thing  happens...

---

### Post by pyrforos on 2014-02-10
anybody?

---

### Post by Vladlenin5000 on 2014-02-10
After reinstalling have you tested without sync? Otherwise your plug-ins/add-on will activate again...

---

### Post by ajgreeny on 2014-02-10
And what about having changed the hidden .mozilla folder as I suggested in post #2?  That will not only mean there are no plugins or extensions, but all other config will be totally new for you to try out.

---

### Post by pyrforos on 2014-02-17
guys please read my first post... i  deleted them.. so  i don't have  to  rename or sync anything

---

### Post by pyrforos on 2015-02-01
solved... [https://en.opensuse.org/SDB:Disable_IPv6_for_Firefox](https://en.opensuse.org/SDB:Disable_IPv6_for_Firefox)
 it was the IPv6...

---

