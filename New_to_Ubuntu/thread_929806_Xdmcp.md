---
title: "Xdmcp"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by REDace0 on 2008-09-25
I go to a university where the Computer Science department has this awesome lab set up running Fedora 9. I'd been ssh-ing into them for a couple years to write code for homework and such. I finally decided to dual-boot my system about a week ago, thankfully with very few problems. I discover XDMCP in the session manager and find out that I can use that to log into the lab's computers graphically from my room. So now I wonder if I can do this the other way? How would one go about setting this up? I know that the campus network is set up so that the only traffic of this kind allowed must be in-network. I can't ssh from somewhere outside of the network, so I'm not terribly worried about security, since the majority of users on campus don't run anything that can XDMCP anyways.

That's a bit long I guess. This may be in the wrong forum and not really a beginner issue. I don't know.

Thanks for any advice or instructions you can offer.

---

### Post by nhasian on 2008-09-25
if your using Gnome then you can access the Gnome display manager with:

```
sudo gdmsetup
```

Under the Remote Tab you need to change it from "remote login disabled" to either "same as local" or "plain with face browser"

---

