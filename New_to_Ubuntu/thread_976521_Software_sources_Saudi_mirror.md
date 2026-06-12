---
title: "Software sources Saudi mirror?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by gysvanzyl on 2008-11-09
At some point I changed the server setting in the Software Sources dialog from the Saudi mirror that was the default when I built the machine.  Now I can't find a way to set it back, as Saudi is not on the provided list of servers.  Any idea how to set it back?

---

### Post by _sAm_ on 2008-11-09
The best is to find the server witch is fastest for you(where you are). To do this go to:
System > Administration > Software Sources 
Change the "Download from:" to "Other..." and hit the "Select Best Server" button. Let it test the different servers and take the one it finds(as best).

---

### Post by gysvanzyl on 2008-11-09
I did that, but as the Saudi server is not on the list, it doesn't find it.  It ends up selecting some server in France, while I know from experience that the Saudi one is faster.

I have another machine with ubuntu installed, so I ended up copying that one's sources.list file.  That solved the problem.

Still strange though that the Saudi mirror, which was installed by default, does not show up in the list of servers?

---

