---
title: "How to set default paper size to A4 in AbiWord?"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by Kexolino on 2011-11-06
I'm using AbiWord 2.8.2 (Lucid). I can't seem to find a way to set the paper size to A4 by default, and I have to do it every time I open a new blank document. I don't know if it makes any difference or not, but after some googling I checked /etc/papersize, and it was set to "letter" so I set it to "A4" and then "a4", but neither makes any difference.

---

### Post by llamabr on 2011-11-06
You must adjust your normal.awt file, either as a user, or globally:

[http://www.abisource.com/~fjf/InvisibleAnt/Templates.html](http://www.abisource.com/~fjf/InvisibleAnt/Templates.html)

[http://www.crazy-wormhole.com/AlinaMeridon/AbiWord/abidocs/howto/howtonormaltemplate.html](http://www.crazy-wormhole.com/AlinaMeridon/AbiWord/abidocs/howto/howtonormaltemplate.html)

Seems like an odd way to fix such a simple problem though.  Incidentally, why do you use abiword rather than openoffice?

---

### Post by Kexolino on 2011-11-06
Thank you, problem solved :)

I like using AbiWord more for everyday tasks like writing one or two page long notes, though I do have LibreOffice installed. Another reason I don't like Libreoffice that much is because the documents I create with it don't look the same in Windows, and I don't know what I can do and what I can't (though probably I should just quit being lazy and read some documentation)...

---

### Post by llamabr on 2011-11-06
Happy to help.  I use abiword for the same reason.  Much smaller and lighter program, for just knocking out some quick notes or something simple.

One benefit of openoffice, too, is that it exports to PDF natively, so if you won't be editing again, or want to send to another user, the pdf will appear the same for everyone.

Glad it worked.

---

