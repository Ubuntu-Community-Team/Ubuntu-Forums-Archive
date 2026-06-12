---
title: "Wireless Slows Down After Update"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by Javelin Dan on 2013-03-25
**SOLVED! **Running Ubuntu 12.04 on Compaq Presario dual core AMD processor, 250 GB hard drive, 2 GB RAM.
   
  I recently had the experience that after an update about two months ago, my wireless internet connection slowed down to a crawl. I first began to wonder if I had somehow corrupted my installation, and since I had little on this computer I cared to save, I backed everything up and re-installed. I wish I had tested the connection on the basic re-install before I updated everything, but I didn&#8217;t and after the full system update there was no change &#8211; you could still time the opening of a web page with a sundial. So I started searching on this forum and on Google for a fix.
   
  [FONT=&amp]I actually found this to be a somewhat common problem; or at least a lot of posts about it. It appears that this is related only to wireless connections &#8211; that confirmed my own personal experience as I have two other computers running 12.04 that have etho connections, and they have experienced no change. I found at least about a half dozen suggested solutions and tried them all, but the only solution I tried that actually worked for me was found at the following link: [http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/). This problem first raised its ugly head in 11.04, but the fix worked like a charm for me in 12.04. [/FONT]

  [FONT=&amp]Apparently after a certain update, there is a problem with the power manager reducing the power to the wireless device slowing it down considerably. I simply copied and pasted the commands the author listed in the terminal and I had my old speed back.  Make sure that you follow the entire post including the last piece of code toward the bottom. As the author reports (and I can confirm), you won&#8217;t recover *_all_* of your speed unless you do. I&#8217;m posting about it here since I actually found this fix on a different site and I&#8217;m not sure how many people know about it here. If this is old news, I apologize, but I always like to share when I find a solution to a vexing problem. Hope it helps someone else! [/FONT]

---

