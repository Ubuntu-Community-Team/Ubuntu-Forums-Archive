---
title: "[SOLVED] Slow program installation"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by methodmarvel on 2008-07-07
I'm installing ubuntu-restricted-extras and it's taking an exceptionally long time and going very slowly.

I can normally get 200kb/s but at the moment it's running at 3000b/s. Does anyone know the reason for this? Are the servers being slow for anyone else?

---

### Post by chrisccoulson on 2008-07-07
Sometimes the download servers can be quite slow, especially if there are a lot of people downloading. This normally happens at release time though, and is caused by lots of people upgrading.

Do you know what mirrors you're using? If not, you can just post your /etc/apt/sources.list.

You could try downloading from a different mirror by going to System -> Administration -> Software Sources and select a new mirror in the 'Download from' box

---

### Post by tuxneo on 2008-07-07
I think you can try to change the server from which you're downloading the files.

Just go in **system > administration > software sources**; in **download from** , select **others** and then click on **best servers**. Now wait, the program is finding you the best server. It might fix your problem ;)


Edit : woops, too late ^^

---

### Post by methodmarvel on 2008-11-25
> **tuxneo said:**
> I think you can try to change the server from which you're downloading the files.

Just go in **system > administration > software sources**; in **download from** , select **others** and then click on **best servers**. Now wait, the program is finding you the best server. It might fix your problem ;)


Edit : woops, too late ^^

It did indeed - I now do this every time I install a new ubuntu version (8.04, 8.10 etc) and occasionally check I'm running smooth with the best server.

Thanks both of you

---

