---
title: "Wifi problems (but not with wubi)"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by foz25 on 2008-10-04
Hi everyone, I hope someone can help me with this, because I'd really like to be able to use ubuntu more often, but without wifi it's not that much use to me.
I have a compaq laptop with the Intel IPW 3945 wifi card, and an XP/ubuntu dual boot setup.  I had gutsy installed previously, and couldn't get my wifi to work.  When hardy came out, I upgraded, and still no wifi. (I allowed the automatic upgrade, it wasn't a clean install).  The other day I downloaded and burned a hardy live cd, which works fine, but I still have no wifi when booting from the live cd.  A friend told me about the wubi installer, which I tried yesterday, and surprise surprise, with wubi I have wifi!
What I'd like to know is, if I do a clean install of ubuntu on my HD, is it likely to have wifi working?  Should I just stick with the wubi install (I'd prefer not to, as I'd like to have ubuntu in a separate partition if I can).  If I decide to do a clean install of ubuntu, what's the best way to do it?

I've searched this forum and others for answers, and have tried some of them as best I can, but haven't been able to get my wifi working.  If there is already a thread explaining how to do this then please point me in that direction.  Sorry for asking again if this has already been covered, but I can't seem to find what I'm looking for.

thanks,  foz25

---

### Post by shifty_powers on 2008-10-04
just a thought, but have you tried the pre release cd of 8.10? i'm using it and they have worked hard on wifi support. you might find it works for you... (you can then either use it, bearing in mind it is essentially beta software, or wait until it comes ut fully, on 31st october iirc).

---

### Post by foz25 on 2008-10-04
I'll definitely give it a go, but I'd prefer to wait until it's released.  I'm new to the ubuntu thing and there are still lot's of things I'm not sure or have no idea about, so I'd prefer not to play around with beta stuff.

Do you know where I can find out how to do a clean install of ubuntu on my dual boot PC?

Thanks

---

### Post by alpage2 on 2008-10-04
There is a HOWTO on installing a dual boot system, here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It will be worth waiting for the final release of 8.10, to ensure the main bugs are worked out, or you could be faced with doing it all over again ;-)

Few wireless adaptors work 'out of the box', but there are some useful resources to help you configure wireless adaptors. Some have no equivalent linux drivers, and for those, the ndiswrapper utility enables the use of the windows drivers, in most cases. Even when a linux driver exists, some manual configuration may be needed before it will work and/or connect to your wireless router.

A Wealth of wifi resources are listed here:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Advice on the Intel IPW 3945 is included in this HOWTO:

[https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy)

That should get you started - post here again if you get stuck along the way.

Alan

---

### Post by foz25 on 2008-10-04
That's great, thanks very much!

I'll let you know how I get on.

foz25

---

