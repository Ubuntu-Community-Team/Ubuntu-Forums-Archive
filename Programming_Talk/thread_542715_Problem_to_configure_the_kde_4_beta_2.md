---
title: "Problem to configure the kde 4 beta 2"
date: 2007-09-04
forum: Programming Talk
---

### Post by marcomangiante on 2007-09-04
Hello,

following the tutorial at [http://techbase.kde.org/Getting_Started/...quired_Software](http://techbase.kde.org/Getting_Started/...quired_Software) I find a problem to configure the qt4. I start the configure command like written in the tutorial bu received the error:

You don't seem to have 'make' or 'gmake' in your PATH.
Cannot proceed.

So I do the command 'which make' and it found at /usr/bin/make, so the make command is there. Also I see that in the path there is also /usr/bin.

In your opinion, what is the problem. I also tried to change the part in the configure script where is the 'if' that control the variable $MAKE, but with poor result: I comment out all the line related to that 'if' and left also the line MAKE='/usr/bin/make' (note that the original line have only 'MAKE').
First I received the message that the script want a 'fi' at the final of the script, after this I received another error, regarding the directory mkspecs.

Is possible to set directly in the script the path of the 'make'. Can someone help me.

Thanks in advance for your help.

--
Regards,

Marco Mangiante

---

### Post by kedadi on 2007-09-05
i guess in couple of days packages for kde4 beta2 should be in backports

---

