---
title: "Mercurial Server Ubuntu 10.04 Issue"
date: 2011-06-14
forum: Repositories &amp; Backports
---

### Post by jhartzell on 2011-06-14
Morning all!

I have been tinkering around with Mercurial Server trying to get it all working. I will try to make this as short and sweet as possible. When using Tortoise HG, after committing locally I push to the central repository on my ubuntu box which is under /var/hg/repos/name. Furthermore, the push goes through successfully with the following log:


pushing to [http://zzzz.zzz/hg/Binary](http://zzzz.zzz/hg/Binary)
searching for changes
remote: adding changesets
remote: adding manifests
remote: adding file changes
remote: added 1 changesets with 1 changes to 1 files
[command completed successfully Tue Jun 14 02:43:12 2011]

This is generally a sign that it was pushed properly and should reflect the changes. I am also using JIRA and FishEye/Crucible from Atlassian which is a Codereview / Issue tracking webapp. I see the changes to the repo here however the physical files are not actually changing. No matter what I do, when I push the files it will show successful and everywhere possible you will see the revision changelog but no file ever changes or updates to what was pushed.

Inside my repository location /var/hg I have the entire "repos" folder chown -R www-data:www-data because Mercurial is tied into Apache. I am running a cgi script that comes with mercurial so that it knows what to show, how to authenticate, etc. All this is configured in my /etc/apache2/sites-available/ inside the "default" file.

If anyone here has any experience with Mercurial that would be able to lend me a hand I would greatly appreciate any guidance. As I have been having so many issues with this as soon as I can get it working like it should I am going to write up a Installation tutorial for Mercurial Server being how I've had such a hard time..

Thanks in advance!

---

### Post by giuspen on 2011-06-20
> **jhartzell said:**
> Morning all!

I have been tinkering around with Mercurial Server trying to get it all working. I will try to make this as short and sweet as possible. When using Tortoise HG, after committing locally I push to the central repository on my ubuntu box which is under /var/hg/repos/name. Furthermore, the push goes through successfully with the following log:


pushing to [http://zzzz.zzz/hg/Binary](http://zzzz.zzz/hg/Binary)
searching for changes
remote: adding changesets
remote: adding manifests
remote: adding file changes
remote: added 1 changesets with 1 changes to 1 files
[command completed successfully Tue Jun 14 02:43:12 2011]

This is generally a sign that it was pushed properly and should reflect the changes. I am also using JIRA and FishEye/Crucible from Atlassian which is a Codereview / Issue tracking webapp. I see the changes to the repo here however the physical files are not actually changing. No matter what I do, when I push the files it will show successful and everywhere possible you will see the revision changelog but no file ever changes or updates to what was pushed.

Inside my repository location /var/hg I have the entire "repos" folder chown -R www-data:www-data because Mercurial is tied into Apache. I am running a cgi script that comes with mercurial so that it knows what to show, how to authenticate, etc. All this is configured in my /etc/apache2/sites-available/ inside the "default" file.

If anyone here has any experience with Mercurial that would be able to lend me a hand I would greatly appreciate any guidance. As I have been having so many issues with this as soon as I can get it working like it should I am going to write up a Installation tutorial for Mercurial Server being how I've had such a hard time..

Thanks in advance!

have you tried to run "sudo hg update" in the server repository?

---

