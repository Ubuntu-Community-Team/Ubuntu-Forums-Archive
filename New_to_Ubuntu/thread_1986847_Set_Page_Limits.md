---
title: "Set Page Limits"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Estech on 2012-05-25
Hello all,
I'll start out saying that I have no training in Linux, but part of my job is to use Ubuntu, so I'm trying to pick it up. 
I am using Ubuntu 10.04.

My goal is to set a page limit on a networked printer. 
I've done some research and come across using lpadmin and CUPS to set a page limit. When I test it, the entire job gets printed.

This is the command that I have been trying to get.  The name of the printer is "TestPrint" and I wanted to set the limit to 1 page and set the quota period for 30 seconds.

cupsenable TestPrint
lpadmin -E -p TestPrint -o job-page-limit=1 -o job-quota-period=30
sudo /etc/init.d/cups restart

When I view printers.conf the QuotaPeriod has a value of 30 and the PageLimit has a value of 1.

Everything looks to me like when I try to print to the TestPrint printer, I should only get 1 page. Sadly, this is not the case.

What is it that I'm not doing right?

Please advise

---

