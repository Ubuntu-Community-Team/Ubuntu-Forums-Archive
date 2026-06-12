---
title: "Tip: CRM114 Anti-spam filter in Kmail"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by esdaniel on 2007-05-22
Just in case anyone else has this problem...

I decided to setup Kmail anti-spam fitlers and being YAN (yet another newb) was delighted to see I could configure this through the GUI, in the process of wondering whether I could use the filters as POP filters i.e. delete the spam before it gets to my inbox I began browsing the filter log view and realised my CRM114 was 'broken', is yours?

So, after reading a few posts on CRM114 installation I then created a hidden directory in ~/.crm114 and copied the CRM114 scripts to this location.

[Thanks to this article]("http://www.linux-magazine.com/issue/77/KMail_CRM114_Spam_Filter.pdf") I ventured nervously to the command line and there I learnt that the following files were omitted from installation/setup:

[I]rewrites.mfp
priolist.mfp
[/I]
Creating blank files in the directory did the trick I hope and it seems to be working now - might be useful for YAN with same issue.  Of course I'm still learning and might have got something mixed up here so please do post any clarifications below .

---

