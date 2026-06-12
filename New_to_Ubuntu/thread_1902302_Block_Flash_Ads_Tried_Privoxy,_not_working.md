---
title: "Block Flash Ads? Tried Privoxy, not working"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by aem0512 on 2011-12-30
My Google Chrome browser uses a ton of CPU to display flash ads..I'd like to block them. (but I still want to be able to view youtube videos and hulu, etc.)

I tried downloading and installing Privoxy, using synaptic.

Then I even tried to change the global proxy settings in /etc/environment by using gksudo thunar in graphical mode. I just added the line [COLOR="Navy"]export http_proxy="127.0.0.1:8118"[/COLOR] and saved the file.

(I first tried to use gksu /etc/environment in the terminal but after entering the password nothing would come up. It didn't tell me the password was incorrect though...just nothing happened.)

But after cleaning out the history,cookies, etc and reloading Chrome, the ads still appeared...pages loaded much slower though.

What could be the problem?

System: Dell B110, 2.8 Ghz Celeron processor, 2GB RAM, Xubuntu 11.10

---

### Post by Sijmen on 2011-12-30
I don't use chrome, but I'd like to suggest an alternative. Firefox with Adblock. That hides all the ads. Add Ghostery and you can block cookies as well.

---

### Post by arochester on 2011-12-30
Chrome has Adblock Plus and Flash Block extensions...

---

