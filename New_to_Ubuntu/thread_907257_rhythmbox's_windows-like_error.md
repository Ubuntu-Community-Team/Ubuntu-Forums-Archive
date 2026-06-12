---
title: "rhythmbox's windows-like error"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by yamatteo on 2008-09-01
Every time I start Rhythmbox, appears to pop-up windows. They say : "Unable to activate plugin Jamendo" and "Unable to activate plugin Negozio Magnatune".
Even it is not such a problem, because I will never use those plugins, it is tiresome: it reminds me my past windows' startups. And I wish to forget.

Is there a way to solve this problem (activating these plugins or stopping their request) ??

---

### Post by sayakb on 2008-09-01
You may disable the plugins. I don't actually remember how to and I dont have it installed either.

---

### Post by Dougie187 on 2008-09-01
If you go to Edit->Plugins you can disable them there.

---

### Post by mick222 on 2008-09-01
EDit-->plugins and untick the boxes

---

### Post by yamatteo on 2008-09-01
But in Edit -> plugins   they are already unticked. If I try to tick it, that pop-up error reappears, and the box is still not ticked. If close Rhythmbox and restart it, those error raise again, even if the boxes where unticked.

---

### Post by Dougie187 on 2008-09-01
I'm not sure if it would help, but you could always try to remove, clean, and re-install rhythmbox.

If you want to do this, you can try these commands, but again, I don't know that this will help your issue, but maybe something got configured wrong at some point.

```

sudo apt-get autoremove rhythmbox
sudo apt-get audoclean
sudo apt-get install rhythmbox

```
Just do each command one at a time, and then try it again.

---

### Post by yamatteo on 2008-09-02
I did. It did not work.
But when I open rhythmbox after remove-reinstall every song is still in the playlist. So some setting option were not deleted.
Is there some deeper way to remove it?

---

