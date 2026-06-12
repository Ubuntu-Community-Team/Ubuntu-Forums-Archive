---
title: "Trouble downloading 12.04"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2012-05-05
For the last couple of days I've been trying without success to download the 701MB ubuntu-12.04-desktop-i386.iso.    I've made 6 attempts so far,  each yielding slightly different results:  

1.  Download appeared to complete but resulting filesize was only 584MB so MD5SUM check failed

2.  Download failed at 369MB

3.  Appeared to complete correctly at 701MB but MD5SUM check failed

4.  Appeared to complete but resulting filesize was too large at 734.4MB and MD5SUM check failed

5.  Appeared to complete but resulting file was only 102.0KB

6.  Appeared to complete but resulting file was 119MB

Any suggestions?

---

### Post by Curtis6767 on 2012-05-05
Have you tried a torrent? 

The image is at isohunt, among other places.

If you're on an Ubuntu system, then you can use Transmission. 

A search on how to use Transmission will bring you several results.

---

### Post by kdane4 on 2012-05-05
Hello,

Here's the [ubuntu releases website]("http://releases.ubuntu.com/12.04/") so you can download the torrent file and run  it with a client like transmission or if you use windows to download, [utorrent]("http://www.utorrent.com/").


Torrent is the best way to download large files, even if it gets interrupted, you can continue downloading because it automatically checks and fix hashes.

---

### Post by Sleepy-zz-John on 2012-05-05
Thanks Curtis and thanks kdane for your helpful replies.  

Problem solved.

As it turns out,  my original No3 attempt was actually a good one and I'd made the mistake of comparing my MD5SUM with those listed on the MD5SUMS-metalink page instead of on the MD5SUMS page.

However,  I didn't discover my mistake until after I'd followed your advice about using torrent and transmission and successfully downloaded another copy (much faster this time) and found it giving me the same MD5SUM as No3 attempt.    So now I've got two good copies  :D

Although neither of your replies actually pinpointed my trouble,  they got me thinking and usefully got me going in the (for me) unfamiliar territory  of torrent and transmission,  so thanks again for both replies.

---

### Post by kdane4 on 2012-05-06
Glad to hear you finally downloaded Ubuntu successfully. [You can now mark this thread as solved..]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Cheers! :)

---

