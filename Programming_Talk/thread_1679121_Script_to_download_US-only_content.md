---
title: "Script to download US-only content?"
date: 2011-01-31
forum: Programming Talk
---

### Post by kittkatt on 2011-01-31
Hello,

I recently had one of the podcasts I listen to start restricting downloads to US IPs only.  I was wondering how I could program a simple script to get the content to me in Canada.  I have a personal website with HostGator which I think is located in the US.  Can I use that somehow?  

The podcast I wanted to try this out with is [Real Time with Bill Maher (audio) ]("http://www.hbo.com/podcasts/billmaher/podcast.xml")

Thanks for all yall help.

---

### Post by lavinog on 2011-01-31
You can request shell access at hostgator.
Then use wget to download the content.

I would refrain from writing a script though, because there are time limits on how long a script can run on hg.
Also the TOS has a clause about using your site for file storage, so it would be a good idea to remove the files afterwards.

---

