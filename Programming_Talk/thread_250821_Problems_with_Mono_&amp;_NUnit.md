---
title: "Problems with Mono &amp; NUnit"
date: 2006-09-04
forum: Programming Talk
---

### Post by Ben.McKenzie on 2006-09-04
Hey. I've been trying to compile the GData C# library from Google, which should compile fine under Mono 1.1.13 and up.

The problem I'm running into is that when I try to compile, Mono isn't finding the nunit.framework.

I've checked, and the GAC has it listed there as an available library.

I'm not sure where to go from here. Do I need to scrap the Ubuntu Mono packages and install from the main site? Has anyone else had a problem with the nunit package not installing properly? I'm not too familiar with Mono. I tried specifying the exact path to nunit.framework, but no good.

To complicate things, GData API uses ant to compile with. Is it possibly something wrong with ant?

Any suggestions on where to go next?

Thanks in advance for your help.

---

