---
title: "Nvclock, underclocking"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by farukdgn on 2015-01-03
Hi. I have a notebook installed Ubuntu 14.04 with GT 240M graphics card. I need to underclock it but I have trouble. It seems like Ubuntu can't recognize my card (check the screenshot). What can I do?
[IMG]http://s28.postimg.org/qu962lcp9/image.png[/IMG]

---

### Post by efflandt on 2015-01-06
Newer nvidia driver versions can overclock 400 series or newer cards with sliders in NVIDIA X Server Settings by setting CoolBits to 8 (gpu/ram) or 12 (+fan). That works for my GTX 750 Ti using nvidia-346 from xorg-edgers ppa.
[http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item](http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item)

Maybe **Option "CoolBits" "1"** still works for older chips. But I wonder if mobile chips can be overclocked since heat could easily be an issue.

Not sure if I ever had much luck using nvclock (a long time ago) and have no need for it now.

---

