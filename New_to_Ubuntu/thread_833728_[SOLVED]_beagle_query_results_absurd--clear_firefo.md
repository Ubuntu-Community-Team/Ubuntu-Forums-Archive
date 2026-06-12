---
title: "[SOLVED] beagle query results absurd--clear firefox index?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by napzilla on 2008-06-18
I really dig the fact the I can have beagle index everything I visit with Firefox, but I think my beagle's becoming rabid. When I run a beagle-query on a topic that has occurred frequently in my past browsing (e.g. a topic related to my research), beagle returns an insane number of URLs. So many, in fact, that they flood the buffer on my terminal and I have to go back and pipe the query into less. Many of the older results are not particularly helpful, and, in addition to the inconvenience of having to sort through them, I don't see any point in wasting disk space on them. I was wondering whether I could instruct beagle to clear its Firefox index periodically, or, barring that, where beagle keeps its Firefox index so that I could manually schedule a cron job to clear it. I looked in the .beagle directory, but Firefox wasn't listed.

Thanks,
  -Brian

---

### Post by dbera on 2008-06-18
There isnt much of disk space wasted. But nevertheless there also other valid reasons to clear the Firefox (or other browsing history) index. Unfortunately this is a long standing feature request and not yet implemented. I will point you to 2 things which gets you close:

1) The firefox index is in ~/.beagle/Indexes/IndexingServiceIndex If you remove that directory, the firefox index is gooooooone. Just make sure you do that while beagled is not running.

2) You can use "beagle-master-delete-button <EXACT_URL>" to remove an indexed page. Use the exact URL as returned by beagle-query.

One additional thing: you can specify dates/date-ranges to narrow your query. Beagle website has the format of the date query.

Hope this helps.

---

### Post by napzilla on 2008-06-19
Thanks for pointing me in the right direction. If I end up writing a cool shell script to handle this, I'll be sure to post it here.

---

