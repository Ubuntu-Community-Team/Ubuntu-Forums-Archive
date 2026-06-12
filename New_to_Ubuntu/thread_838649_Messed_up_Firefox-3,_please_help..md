---
title: "Messed up Firefox-3, please help."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by madu on 2008-06-23
Hello,

On the 'Download day' I was really excited about downloading FF-3 ( was already using Beta-5). First I checked the about and it said "Firefox 3.0". I thought it has already being upgraded (which I thought was strange because I didnt see any upgrade notice) so I installed Google toolbar. It installed but the 'bookmarks' didnt give my old bookmakrs. So I thought I dont have the correct version-3, so I went to Synaptic to install. 
At that time the FF-3 in Synaptic was still RC-1. Then I did the stupidest thing and "completely removed" FF-3 I had installed. When it removed, it also removed a large number of libraries with it too. I didnt think much of it at that time.
Anyway then I downloaded the package from the FF site and installed it. And it didnt work. I mean it works. I can browse. But the history, back/forward buttons, etc., are not working. Then I went back to Synaptic to install the FF-3 in there, but when I chose it, it only installed FF-3, no other libraries.

I distinctly remember Synaptic removing lot of libraries and I think that's what making FF-3 not to work now. I searched around but could not find the dependencies for FF-3. So now I'm back to FF-2. :(

Any help would be greatly appreciated. 

Thank you.

---

### Post by Frak on 2008-06-23
sudo apt-get install build-deps firefox-3.0

---

### Post by madu on 2008-06-23
> **Frak said:**
> sudo apt-get install build-deps firefox-3.0

Thanks heaps mate. Worked like a charm.

---

