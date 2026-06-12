---
title: "Priority Processing"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by Phil_Pene on 2013-08-09
Currently listen to internet audio that is sometimes sporadic.  Looking for a way to elevate to raise the priority of a URL and/or an online radio apps.  Guidance sought

---

### Post by SchnappiJedi on 2013-08-09
> **Phil_Pene said:**
> Currently listen to internet audio that is sometimes sporadic.  Looking for a way to elevate to raise the priority of a URL and/or an online radio apps.  Guidance sought

One option (depending on your router) would be set traffic from any given site to have a higher priority in the router. This is possible in a NETGEAR WGR614v8 router with the most up to date firmware and not possible in any 2Wire router I have seen. I cannot speak for other routers or 3rd party router firmware such as Tomato or DD-WRT.

*Here are links to some things referred to:
[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)
[http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)

---

### Post by Phil_Pene on 2013-08-10
Much thanks for the timely reply,  Have the Linksys wrv200 and will look at the documentation however I often visit my university and travel by commercial busses which offer wifi through routers I do not control.  Windows has features to give prioity to processes of my choosing...  Not ununtu?  Please advise

---

### Post by Cheesemill on 2013-08-10
Linux has the ability to change the niceness (priority) of processes but I don't think it will make a difference.

In my opinion it's the quality of your internet connection that's causing the problem rather than a lack of system resources. Try running the top command in a terminal while you're listening, if your CPU isn't running at 100% when the dropouts occur then it's definitely not an issue which changing the process priority can cure.

---

