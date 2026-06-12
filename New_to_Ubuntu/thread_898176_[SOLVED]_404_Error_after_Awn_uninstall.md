---
title: "[SOLVED] 404 Error after Awn uninstall"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by lobo_blanco on 2008-08-23
[Solved, thanks]

Hi,

Ubuntu 8.04 all updates
Problem = 404 error
Similar to problem here --> [http://ubuntuforums.org/showthread.php?t=752787&highlight=error+404+awn](http://ubuntuforums.org/showthread.php?t=752787&highlight=error+404+awn)
Link does not tell me how to redirect to different repository or how to get rid of the error upon uninstall.

I installed AWN but didn't do it through Synaptic Package Manager ...
... lesson learned.](*,)

Actually, it worked fine but I got the following error when I used the Update Manager:

Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/heardy/main/source/Sources.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/heardy/main/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I uninstalled AWN and associated packages but still get the same update error.
I checked for orphans and did an autoclean but still get the error.

Is there a file that lists the repositories for update, where I can tell Update Manager not to try to update AWN any more?

I'll probably install it again, (using Synaptic) but want to start out without the 404 error.

Any help on clearing this up would be greatly apprciated!

Thanks,

Dave

**Update: Found the answer** myself, I had no idea it would be so easy.
I did some more searches and found that all I needed to do was:

**System>>Administration>>Software Sources... pick a new server**
(or in my case delete the Software Source)

Just goes to show ya, just about anything you experience as an Ubuntu newbie has been done before and documented right here on this forum.
**What a great resource! - Thanks All**

---

