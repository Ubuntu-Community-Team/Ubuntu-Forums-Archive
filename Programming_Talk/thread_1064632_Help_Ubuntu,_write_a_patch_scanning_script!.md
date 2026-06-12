---
title: "Help Ubuntu, write a patch scanning script!"
date: 2009-02-09
forum: Programming Talk
---

### Post by jsmidt on 2009-02-09
I'm sure somebody would know how to do this.  Ubuntu has a great tool that picks off new patches coming into fedora and alert the devs so they can consider using the patches into Ubuntu.  Could someone try to help me write a script that does the same thing for opensuse?

The script would need to:

1.  Scan all the entries at this website: [http://tmp.vuntz.net/opensuse-packages/browse.py?project=openSUSE:Factory](http://tmp.vuntz.net/opensuse-packages/browse.py?project=openSUSE:Factory).  
2.  Pick off all items that end in .patch.
3.  Output the website of the patch when a new patch is added.

For example it would output: adns-1.4-ipv6.patch  linked to this webpage in html form: [http://tmp.vuntz.net/opensuse-packages/browse.py?project=openSUSE:Factory&package=adns](http://tmp.vuntz.net/opensuse-packages/browse.py?project=openSUSE:Factory&package=adns)  

Then later, when there is a new patch for at that link, it would display the new information.  Thanks.

---

