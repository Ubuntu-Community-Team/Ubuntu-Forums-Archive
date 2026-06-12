---
title: "uri.host is explosive! &amp; ufw"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by Eglefino on 2013-08-30
The last month my Firefox-22 and now version 23 had circa 350 crashes. I've tried to search for a solution in Flash/Java, but that wasn't the point. I have no sound either. But host/firewall problems can't something to do with each others. So I asked here for help, but did not get it.

So I try to get help for my Firefox-crashes. I deleted all my add-ons and tried also the 'saved modus', but the crashes they stay! Now I tried to start Firefox from the terminal and it crashes again, but now it gave more times a warn:

eglefino@EglefinoPC:~$ firefox
uri.host is explosive!
(about:sessionrestore)
Could not check applicable rules for about:sessionrestore
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
NOTE: child process received `Goodbye', closing down
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
uri.host is explosive!
(about:healthreport)
Could not check applicable rules for about:healthreport
uri.host is explosive!
(about:healthreport)
Could not check applicable rules for about:healthreport
uri.host is explosive!
(about:healthreport)
Could not check applicable rules for about:healthreport
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
uri.host is explosive!
(about:healthreport)
Could not check applicable rules for about:healthreport
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
uri.host is explosive!
(about:blank)
Could not check applicable rules for about:blank
NOTE: child process received `Goodbye', closing down
eglefino@EglefinoPC:~$


Can somebody give me an help? explosive???

And I have installed (g)UFW, after I asked a status, it said it will enable after reboot (something like that), but after reboot it is disabled!

---

### Post by Jonathan Precise on 2013-08-30
As for GUFW, you must provide your password (by pressing the UNLOCK button) to see changes in firewall.

As for any warnings posted by firefox, put them in code tags:
(CODE)Paste all your commands and outputs (or warnings) here.(/CODE)

Change the parenthesis to brackets to get:
```
Paste all your commands and outputs (or warnings) here.
```

EDITS POSTED BELOW:

1) I'm _**assuming**_:

    ```
uri.host is explosive!
```

    means that gufw (or firefox) has detected that the website is malicious. Look at the command line output when navigating to another site.

---

