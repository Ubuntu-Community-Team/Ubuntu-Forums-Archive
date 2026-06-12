---
title: "Graphics card question"
date: 2015-05-02
forum: New to Ubuntu
---

### Post by randy23 on 2015-05-02
Hello everyone,

I am a newbie to Linux and I am enjoying it a lot. I have a graphics card driver question.
I have **[COLOR=#6A6A6A][FONT=arial][B]ATI Radeon HD 2400XT**[/FONT][/COLOR][/B] and when I installed Ubuntu 14.04 the graphics card driver was installed automatically.
Did Ubuntu install the **latest** ATI graphics driver or is it a generic driver. Do I manually have to go to the ATI support site and download this 2013 legacy version driver:
[http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy2&os=Linux%20x86_64)

Also, how to do install the AMD/ATI catalyst control center for Ubuntu 14.04.2 LTS for change my graphic settings.
Thanks in advance and your feedback is appreciated
[IMG]http://i59.tinypic.com/2cwpo61.jpg[/IMG]

---

### Post by QIII on 2015-05-02
Hello!

That is an older card and no longer enjoys Linux support from AMD.  The legacy driver will not work with the current version of X Server.

When you installed Ubuntu, the default open source Radeon driver was installed -- otherwise you would not be seeing anything.

That is the driver you will need to use.

---

### Post by randy23 on 2015-05-02
That's good to know and thanks for the reply

---

