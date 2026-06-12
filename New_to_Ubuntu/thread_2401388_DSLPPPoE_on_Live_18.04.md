---
title: "DSL/PPPoE on Live 18.04?"
date: 2018-09-17
forum: New to Ubuntu
---

### Post by noobsoftheworld on 2018-09-17
Is there a way to create a simple DSL connection when booting live from the CD? I can't seem to find a way to do so using the Network tab on Settings; my Ethernet connection is recognized and activated but I can't add the PPPoE connection with my ISP username and password.
I found this solution somewhere, where you type in the terminal: *nmcli con edit type pppoe con-name "My DSL*" and then *set pppoe.username <real username here>*. That does indeed create a DSL connection "My DSL" that appears on the list, BUT when opening its configuration window none of the options I get in the Parent Interface dropbox seem to be the right one: whichever one I choose (and there aren't that many), upon pressing Save the "My DSL" connection disappears from the list. This includes deactivating the Ethernet connection, which is silly anyways as that's how it's running on this machine right now.

Could anyone confirm this only happens when booting live from the CD? I have never been able to make Internet work properly on Ubuntu 16 and I don't want to install 18 in my hard drive only to find out it's still giving me a lot of trouble and having to reinstall Ubuntu 14 for the tenth time. I'm quite noobish at Linux and this is extremely frustrating. Thank you for any help.

---

