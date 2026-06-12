---
title: "Problem with Anjuta"
date: 2007-04-07
forum: Programming Talk
---

### Post by Axme on 2007-04-07
When I launch Anjuta I get the message

/usr/bin/create_global_tags.sh: 3: function: not found

I did a search on google and got the advice.



Seems to be triggered by the shift from bash to dash as the default /bin/sh.
[https://launchpad.net/distros/ubuntu/+spec/dash-as-bin-sh](https://launchpad.net/distros/ubuntu/+spec/dash-as-bin-sh)

Solution: change shell in line 1 from /bin/sh to /bin/bash and add bash as a dependency.

I have no idea about how to go about implementing the solution.

Please help

---

