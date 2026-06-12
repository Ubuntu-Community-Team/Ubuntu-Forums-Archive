---
title: "Webalizer not resolving IP addresses into host names in Ubuntu 12.04 LTS"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by rookie_11.04 on 2013-09-19
I am using webalizer to generate statistics for my website on ubuntu 12.04 LTS.
I concatenate all the apache access.log files and make make a single big file.

Now i follow the step 1 in "How it Works" section here - 
[ftp://ftp.mrunix.net/pub/webalizer/DNS.README](ftp://ftp.mrunix.net/pub/webalizer/DNS.README)

If you see the "**Top 30 of 10484 Total Sites**" section in [http://www.webalizer.org/sample/usage_199905.html](http://www.webalizer.org/sample/usage_199905.html), you can see that the Hostname column is populated with the domain names not the IP addresses. Similar is the case in the section "**Top 10 of 10484 Total Sites By KBytes**".

Unfortunately I get IP addresses in the Hostname section. But the "**U****sage by location**" pie chart at the bottom is working for me, so the Geo Location stuff works, but not for the domain names.

How can i solve this problem. Please help me out.

---

