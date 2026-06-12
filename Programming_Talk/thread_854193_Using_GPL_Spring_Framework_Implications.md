---
title: "Using GPL Spring Framework Implications"
date: 2008-07-09
forum: Programming Talk
---

### Post by chromaticbum on 2008-07-09
Hello everyone,

I am pretty sure I know the answer to this question, but I don't want to go down a long road without being sure. Under the Apache License v2.0 (which is the license that Spring Framework uses), would we be able to write software using this API and distribute our software closed-source, while distributing the API under the Apache License v2.0?

Similarly, we would like to use Spring Source as our application server, which is currently under the GPL v3.0. Would we be able to write our application to run on top of Spring Source, distribute it closed-source, and distribute Spring Source under the GPL v3.0?

Thank you in advance!
Hollin Wilkins

---

### Post by nvteighen on 2008-07-09
> **chromaticbum said:**
> Hello everyone,

I am pretty sure I know the answer to this question, but I don't want to go down a long road without being sure. Under the Apache License v2.0 (which is the license that Spring Framework uses), would we be able to write software using this API and distribute our software closed-source, while distributing the API under the Apache License v2.0?

From the Apache License 2.0:
"(...) For the purposes of this License, Derivative Works shall not include works that remain separable from, or merely link (or bind by name) to the interfaces of, the Work and Derivative Works thereof." (Section 1, paragraph 8).

So, according to that, your application doesn't even enter into the License's scope.

> Similarly, we would like to use Spring Source as our application server, which is currently under the GPL v3.0. Would we be able to write our application to run on top of Spring Source, distribute it closed-source, and distribute Spring Source under the GPL v3.0?

Well, probably you could consider Spring Source as a "System Library" under GPLv3's Section 1. If so, you are not bound to it... But I suggest you to email FSF (licensing AT fsf DOT org).

If any doubt, ask a lawyer.

---

### Post by tinny on 2008-07-09
FYI

The Apache License V2 overview

[http://www.oss-watch.ac.uk/resources/apache2.xml]("http://www.oss-watch.ac.uk/resources/apache2.xml")

The GNU General Public License v2 (couldnt find a V3 overview)

[http://www.oss-watch.ac.uk/resources/gpl.xml]("http://www.oss-watch.ac.uk/resources/gpl.xml")

---

