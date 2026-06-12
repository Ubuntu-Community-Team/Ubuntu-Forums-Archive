---
title: "[SOLVED] Quick Search doesn't work in Synaptic (8.10)"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by the8thstar on 2008-11-03
I'm having a peculiar problem with synaptic that never occurred with the previous versions of Ubuntu. Apparently, the Quick Search tool is broken. It can't find anything at all.

Is there a fix for this? Thanks a lot!

---

### Post by ajgreeny on 2008-11-03
But surely there was no "Quick Search" in previous versions of synaptic.  At least there isn't in my synaptic in 8.04 version.  I haven't looked at 8.10 yet.

---

### Post by drs305 on 2008-11-03
> **the8thstar said:**
> I'm having a peculiar problem with synaptic that never occurred with the previous versions of Ubuntu. Apparently, the Quick Search tool is broken. It can't find anything at all.

Is there a fix for this? Thanks a lot!

Quick search works for me. You might try reinstalling synaptic via command line:
```
sudo aptitude reinstall synaptic
```

---

### Post by Paqman on 2008-11-03
> **the8thstar said:**
> Apparently, the Quick Search tool is broken. It can't find anything at all.


Check that you're not filtering for more than one thing. I got caught out by this the first time I used the quick search bar, too.

---

### Post by the8thstar on 2008-11-03
> **drs305 said:**
> Quick search works for me. You might try reinstalling synaptic via command line:
```
sudo aptitude reinstall synaptic
```

I did it, but nothing is changed.

---

### Post by the8thstar on 2008-11-03
> **Paqman said:**
> Check that you're not filtering for more than one thing. I got caught out by this the first time I used the quick search bar, too.

What do you mean? This?

---

### Post by drs305 on 2008-11-03
Can you be more specific about what happens? I have 'ALL' selected in the left window. When I type "2v" into the Quick Search box the only thing I see in the package list is "2vcard". If I type "Acrobat" I get a long list of packages associated with *acroread*.

I am using synaptic 0.62.1ubuntu10

---

### Post by cariboo on 2008-11-03
Upate your sources list, the database needs  to be populated, and always have All highlighted in the left hand pane. If you have anything highlighted you won't get the expected result.

Jim

---

### Post by the8thstar on 2008-11-03
> **drs305 said:**
> Can you be more specific about what happens? I have 'ALL' selected in the left window. When I type "2v" into the Quick Search box the only thing I see in the package list is "2vcard". If I type "Acrobat" I get a long list of packages associated with *acroread*.

I am using synaptic 0.62.1ubuntu10

Well, NOTHING happens, that's the problem really.

---

### Post by philinux on 2008-11-03
I thought I remembered this being buggy during testing.

Click Status first then quick search works or just click any package, that seems to kickstart it, then type.

---

### Post by the8thstar on 2008-11-03
> **cariboo907 said:**
> Upate your sources list, the database needs  to be populated, and always have All highlighted in the left hand pane. If you have anything highlighted you won't get the expected result.

Jim

Update - this is the first thing I did, before I started the thread
Database populated - I don't see anything, hence the problem
All - this is the default

---

### Post by the8thstar on 2008-11-03
This is not meant to be a fix, but I got it to work again "by accident" when I was following **cariboo907**'s ideas. I changed the following setting in System > Administration > Software Sources in the Ubuntu Software tab: I switched the server for download from "Main Server" to one of my own country and then back to "Main Server" again.

Now it's working again. I'm thinking that this might have been a syncing issue after all.

Thanks to all of you guys for your invaluable help!

---

### Post by Bao2 on 2009-02-07
I have same issue. Search don't works. I tried change to another server like suggested but still don't works. When I type 2v in Quick Search (All is selected) I don't see 2vcard like I did in previous Ubuntu versions. I am using Jaunty

---

### Post by drs305 on 2009-02-07
> **Bao2 said:**
> I have same issue. Search don't works. I tried change to another server like suggested but still don't works. When I type 2v in Quick Search (All is selected) I don't see 2vcard like I did in previous Ubuntu versions. I am using Jaunty

I just tried 'quick search' and it worked fine for me. This may be a bit basic, but have you enabled the 'extra' respositories? 2vcard is in the universe repository. 

You might also check synaptic's Settings > Filters: Status Tab to make sure the appropriate boxes are ticked.

---

### Post by c-m on 2009-02-07
i have the same problem on ubuntu umpc 8.10 - is there a permant fix yet?

---

### Post by osaks on 2009-03-01
I had the same problem, the solution is this: 

```
sudo update-apt-xapian-index 
```

---

### Post by tfga on 2009-08-06
I'm having this problem with Synaptic 0.62.5 on jaunty, I've tried everything mentioned above including the reinstall, xapian-index update and changing countries.

I'll try and explain the bug more clearly:


[LIST]
[*]Search used to work (it broke after a full re-install of ubuntu)
[*]Search works only for installed packages and only some installed packages at that. Non-installed packages simply wont show up in a search
[*]Without using search/quick-search I can see all packages as normal, both installed and non-installed
[*]Installing a package and then searching for it doesn't seem to work either
[*]Both search and quick search are affected
[*]Filtering/sections work as you would expect, just not with search
[/LIST]
Thanks

---

### Post by tfga on 2009-08-09
Anyone else experiencing this try:

```
(sudo) dpkg --configure -a
```

Seems to work now.

---

### Post by Lockheed on 2009-09-03
I tried all those methods multiple times and still nothing. IF I type something in Quick Search box, nothing happens. 

Besedes, even when I use full-search option, found packages don't list in relevance order.

---

### Post by UUB86 on 2009-09-22
> **osaks said:**
> I had the same problem, the solution is this: 

```
sudo update-apt-xapian-index 
```

This worked for me, thanks osaks__.

---

### Post by randumnumber on 2010-08-17
This might be a bit late, but if anyone else sees this and it helps them it will be worth it.

I had this problem after a reinstall of jaunty 9.04 i tried all these things and nothing worked.

I could use regular search but not quick search

I fixed it by going to settings>filters

in filters i hit the "deselect all" button so that all the check marks for all the boxes went away... low and behold i can now use my quick search!!!

My only guess is that somewhere in the 1's and 0's something is backwards..

---

### Post by Hammi on 2011-10-03
```
apt-get install apt-xapian-index
```

fixed it for me.

---

