---
title: "Untrusted packages"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by amazingadie on 2014-04-13
Hi There

I've been using 11.04 for at least a couple of years now but recently Firefox stopped working properly so I'm using another comp to send this. 

Now I say 11.04 because that's what it says I'm using when I click "about Ubuntu" but on the start up screen it actually says 10.10, but I don't know which it actually is. 

With Firefox I couldn't get any websites to load apart from google, and I couldn't open private windows or use the help function. That was all I checked before deciding it was screwed. 

I tried installing different browsers but each time got the response "Requires Installation of untrusted packages. The action would require the installation of packages from untrusted sources. " When you click on "details", all it says is Firefox.

So I tried uninstalling Firefox with the hope of re-installing it but when I tried to reinstall I got the same message as above. 

I went into terminal and typed "sudo apt-get update && sudo apt-get upgrade" Terminal then installed some files but ended saying "some index files could not be downloaded....". 

Can anyone help with what I should do to rectify this please? I really appreciate anyone taking the time to think about this. Perhaps I should just update to the most recent version of Ubuntu?

Many thanks in advance!

Adie

---

### Post by buzzingrobot on 2014-04-13
If it's 10.04, support for the desktop release ended in April  2013.  Support for 11.10 ended in May 2013.  When support ends, its repos are no longer available.  That would account for the update errors. The 'untrusted' messages could be due to the unavailability of keys from the now nonexistent repos.

So.... yes, think about moving to a supported release.

---

### Post by amazingadie on 2014-04-15
Excellent. Thank you very much for getting back to me!

Cheers

---

