---
title: "advice on restoring mistakenly deleted files"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by zirgut on 2012-06-26
In an attempt to delete a form autofill package I deleted some files listed below. This may be the cause of sound loss as the two events were very close in time. Is there a way to restore them and if so a step by step approach in doing so would be helpful?
These are the files:
 the list of packages I inadvertently removed
 2012-06-16 23:58:17 remove icc-profiles-free 2.0.1+dfsg-1 <none>
2012-06-16 23:58:18 remove libattica0 0.2.80-0ubuntu2 <none>
2012-06-16 23:58:19 remove libwww-mechanize-formfiller-perl 0.10-2 <none>
2012-06-16 23:58:20 remove libdata-random-perl 0.06-1 <none>
2012-06-16 23:58:21 remove libgd-gd2-perl 1:2.46-3build1 <none>
2012-06-16 23:58:22 remove libgtkspell3-0 2.0.16-1ubuntu2 <none>
2012-06-16 23:58:22 remove libwww-mechanize-perl 1.71-1 <none>
2012-06-16 23:58:23 remove libhttp-server-simple-perl 0.44-1 <none>
2012-06-16 23:58:24 remove libid3tag0 0.15.1b-10build2 <none>
2012-06-16 23:58:25 remove libindicator3-6 0.4.1-0ubuntu1 <none>
2012-06-16 23:58:25 remove libindicator6 0.4.1-0ubuntu1 <none>
2012-06-16 23:58:26 remove libllvm2.9 2.9+dfsg-3ubuntu4 <none>
2012-06-16 23:58:26 remove libminiupnpc5 1.5-2ubuntu2 <none>
2012-06-16 23:58:27 remove libnatpmp1 20110808-3ubuntu1 <none>
2012-06-16 23:58:28 remove libnl3 3.0-1.1ubuntu1 <none>
2012-06-16 23:58:28 remove libx264-116 2:0.116.2042+git178455c-1ubuntu1 <none>
2012-06-16 23:58:29 remove linux-headers-3.0.0-12-generic 3.0.0-12.20 <none>
2012-06-16 23:58:35 remove linux-headers-3.0.0-12 3.0.0-12.20 <none>
2012-06-16 23:58:39 remove nvidia-settings 295.33-0ubuntu1 <none>
2012-06-16 23:58:40 remove screen-resolution-extra 0.14ubuntu2 <none>

Hopefully yours
zirgut

---

### Post by audiomick on 2012-06-26
> **zirgut said:**
> 
 the list of packages I inadvertently removed
 2012-06-16 23:58:17 remove icc-profiles-free 2.0.1+dfsg-1 <none>
2012-06-16 23:58:18 remove libattica0 0.2.80-0ubuntu2 <none>
[COLOR="Red"]2012-06-16 23:58:19 remove libwww-mechanize-formfiller-perl 0.10-2 <none>[/COLOR]
2012-06-16 23:58:20 remove libdata-random-perl 0.06-1 <none>
2012-06-16 23:58:21 remove libgd-gd2-perl 1:2.46-3build1 <none>
2012-06-16 23:58:22 remove libgtkspell3-0 2.0.16-1ubuntu2 <none>
[COLOR="Red"]2012-06-16 23:58:22 remove libwww-mechanize-perl 1.71-1 <none>[/COLOR]
2012-06-16 23:58:23 remove libhttp-server-simple-perl 0.44-1 <none>
2012-06-16 23:58:24 remove libid3tag0 0.15.1b-10build2 <none>
2012-06-16 23:58:25 remove libindicator3-6 0.4.1-0ubuntu1 <none>
2012-06-16 23:58:25 remove libindicator6 0.4.1-0ubuntu1 <none>
2012-06-16 23:58:26 remove libllvm2.9 2.9+dfsg-3ubuntu4 <none>
2012-06-16 23:58:26 remove libminiupnpc5 1.5-2ubuntu2 <none>
2012-06-16 23:58:27 remove libnatpmp1 20110808-3ubuntu1 <none>
2012-06-16 23:58:28 remove libnl3 3.0-1.1ubuntu1 <none>
2012-06-16 23:58:28 remove libx264-116 2:0.116.2042+git178455c-1ubuntu1 <none>
2012-06-16 23:58:29 remove linux-headers-3.0.0-12-generic 3.0.0-12.20 <none>
2012-06-16 23:58:35 remove linux-headers-3.0.0-12 3.0.0-12.20 <none>
2012-06-16 23:58:39 remove nvidia-settings 295.33-0ubuntu1 <none>
2012-06-16 23:58:40 remove screen-resolution-extra 0.14ubuntu2 <none>
Hallo.
At a guess, the packages I have marked in red are the ones you needed to remove for the autofill thing you were trying to get rid of.

The Linux headers packages must have been an older kernel if you can still boot the thing, so you can leave them out as well.

You can put the rest of them back by opening the software centre, copying the package names from the list you have posted here into the search window of the software centre and marking them for installation. 

There may be a terminal command that lets you install them all at once, but I don't know it. :)

---

### Post by zirgut on 2012-06-27
Thanks Michael,
I have done as you suggested. Some of the deleted files were not recognised but I was able to reinstall perhaps 8 or9 of those on the list. However it has not brought back my sound so it is back to square one.
Appreciatively
zirgut

---

