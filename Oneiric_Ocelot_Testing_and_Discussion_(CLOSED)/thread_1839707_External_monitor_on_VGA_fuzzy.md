---
title: "External monitor on VGA fuzzy"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by aridus on 2011-09-06
One of the big disappointments of Ubunty 11.04, for me, is that, for some laptops, an external monitor connected to the VGA port is blurry and unusable. I eventually fixed mine using a new kernel (see the post from kencamargo at [http://ubuntuforums.org/showthread.php?t=1679181](http://ubuntuforums.org/showthread.php?t=1679181)). I was expecting that this problem would be absent in the beta 1 of 11.10 as it uses a more recent kernel. However, 11.10 does have this problem. I post this here in the hope that somebody who understands these matters may be able to rectify this.

Thank!

---

### Post by mcduck on 2011-09-06
That sounds like you might be using wrong display resolution for the monitor. Especially flat panel displays tend to give you blurred picture if you aren't using the panel's native resolution as the panel needs to scale the image to correct resolution.

Of course you'll also need working drivers for your graphics card, otherwise the correct resolution might not be available at all.

---

### Post by aridus on 2011-09-06
Many thanks. A possibility, yes, but not in this case. This problem occurs at all available resolutions, including the panel's native resolution of 1680 x 1050. Ironically I use a Dell flat panel and a Dell Vostro laptop: the problem occurs with Ubuntu but not with Windows. If you check the referenced thread in my first post, and many others that you can find elsewhere, you will see that many people have this problem.

---

### Post by aridus on 2011-09-12
Can anybody kindly tell me what I can do to ensure that the patch for this kernel bug (I hope I am using the correct terminology) is incorporated into Ubuntu 11.10 (please see the last post by kencamargo at 
[http://ubuntuforums.org/showthread.php?t=1679181)?](http://ubuntuforums.org/showthread.php?t=1679181)?)

This is a critical problem for a lot of people with NVidia cards and an external monitor that they need to access with a VGA connection.

With grateful thanks, Martin

---

