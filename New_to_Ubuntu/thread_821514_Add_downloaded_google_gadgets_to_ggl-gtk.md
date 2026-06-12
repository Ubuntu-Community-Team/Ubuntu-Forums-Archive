---
title: "Add downloaded google gadgets to ggl-gtk"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-06-07
I just installed googles gagdets and I downloaded some of them, since the ones available aren't that great.

I added the xxx.gg files to /home/username/.google/gadgets/downloaded_gadgets

but they don't seem to appear

Could someone tell me how I should add them?

Also, how do I enable the sidebar?

Thanks.

---

### Post by alexandremrj on 2008-06-16
Hello


for you to add the downloaded gadgets in google gadgets you have to enable them (one by one) from the command-line:

ggl-gtk <path of the gadget>/xxx.gg

this way google gadgets will enable the gadget and it will be there even at next restart (so you won't need the downloaded file anymore).

For the use of the sidebar the google gadgets must be started with the command

ggl-gtk -s

---

