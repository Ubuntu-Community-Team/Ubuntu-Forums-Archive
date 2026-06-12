---
title: "Update Flash Player"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by MIraan_Baloch on 2014-03-22
[FONT=verdana][SIZE=3][FONT=arial][SIZE=2]Hi,
I need to update firefox flash player please anyone can help me to solve this issue? I am waiting for team replies?[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by deadflowr on 2014-03-22
I'm guessing firefox plugin says that flash is out of date.
This is unfortunate, but the reality is flash for linux is stuck forever(until adobe decides to change this) at 11.2.
So from that point, if you installed flash from the software center/Ubuntu's repos, as long as you keep the system updated, you will have the latest version of flash for linux available.

If you need a version higher than 11.2, then two ways are either install google chrome, which has an updated version by default.
Or(big OR, as it is a work in progress) install pipelight
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

That's the best you can do under the circumstances.

---

### Post by craig10x on 2014-03-22
Yeah...unfortunately, adobe no longer makes newer versions of flash for linux...only provides updates for the very old version that is on ubuntu...so, if you use firefox you are stuck with it...
However, because adobe has an agreement with Google to provide the newest versions of flash for Google Chrome's pepperflash (which comes by default with Chrome) if you run Google Chrome as your web browser you will always have the latest flash on ubuntu...

When we say Chrome we mean the one you get from their website (not chromium that is available in the software center)...

---

### Post by Bucky Ball on 2014-03-22
You can install Pepperflash in Chromium, too. Fairly easy ...

---

### Post by monkeybrain20122 on 2014-03-23
Some websites don't work for FF not because of flash version but DRM, especially news websites. e.g [http://www.cp24.com/](http://www.cp24.com/)

Interestingly if you install pipelight-flash they would work with flash 11.2 from the system, you just need to install pipelight-flash, but without actually switching to it. I have been wondering why and here is the explanation[ http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html]("http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html")

widevine is installed along with pipelight-flash so system flash can use it even without switching to pipelight-flash. Chrome uses a google version of chrome only widevine which are not supported on many sites that support widevine so some sites may work with Firefox flash but not chrome's (though not the one I linked to above)

I rarely come upon  flash streaming sites that don't work with FF's  flash because of version being too old and I have not seen any advantage  of Chrome's pepper flash over the system's when both work (~98% of the  time) but I can name at least one disadvantage: Youtube. Except maybe  for Nvidia system hardware acceleration does work on Youtube (flash, not  html5) but it doesn't work with pepper flash (Chrome may accelerate  flash on its own but not nearly as efficient)

---

