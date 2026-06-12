---
title: "How to activate the OpenOffice plugin in Firefox and Epiphany"
date: 2006-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by VosaxAlo on 2006-07-25
Hi to all,

Breezy was the last Ubuntu version with the OpenOffice plugin for mozilla browsers. From the Dapper version, no more plugin packaged.

I don't know why, but when you check the Mozilla-Plugin option in the OpenOffice Options, this will create a broken link in your home/.mozilla folder, because this link search a non existent **libnpsoplugin.so** library in the folder "/usr/lib/openoffice/program".

So I have downloaded the openoffice-core package from the Breezy repository, and I have put the plugins files in the right folder
(**/usr/lib/openoffice/program**). Restarting Epiphany now all function very well again.

I have attached to this thread the two plugins files that you can download and put in the folder **/usr/lib/openoffice/program**. It should function well for you too.

---

