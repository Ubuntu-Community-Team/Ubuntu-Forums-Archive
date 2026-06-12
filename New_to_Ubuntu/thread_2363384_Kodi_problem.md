---
title: "Kodi problem"
date: 2017-06-09
forum: New to Ubuntu
---

### Post by rudybaby on 2017-06-09
I am new to Ubuntu but not new to Linux, as I've used mint in the past.  I installed Ubuntu on an Intel PC as the lone OS yesterday.  I successfully was able to configure my VPN (yeah). Then I installed Kodi from the software manager.  When I click to open Kodi, the icon goes to the left toolbar and the mouse and desktop freeze, but no Kodi. Also I have to turn the power off to shutdown and reboot.  I tried all those F1, F2, stuff, no help.   HELP, please.

---

### Post by sp40140 on 2017-06-09
Can you explain " I installed kodi from the software manager"? 
Do you mean "Ubuntu Software"? 
Did you download a .deb file? Where did you get the deb file?

---

### Post by rudybaby on 2017-06-09
No package, it was offered in the Ubuntu software.  I choose Kodi, clicked install, and it installed. Mint called it software manager.

---

### Post by monkeybrain20122 on 2017-06-10
The freeze may be due to some interactions with your DE (unity?). You can run a stand alone session of Kodi instead of embedded in your DE. Just logout and from the greeter click the little ubuntu symbol of the login box, choose kodi instead of Ubuntu and login again. When done logout from Kodi and from the login choose Ubuntu to log back into Ubuntu

You may also want to upgrade Kodi. [https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa](https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa). In the terminal type
```

[COLOR=#333333]sudo add-apt-repository ppa:team-xbmc/ppa && sudo apt update && sudo apt upgrade[/COLOR]
```



PS: Just in case your config is corrupt, delete the hidden folder .kodi. To see it open the fie manager and press ctr+h or choose "show hidden" from file browser then  delete it. Or just in the terminal type

```
rm -r ~/.kodi
``` However, this is drastic as it will remove all your custom configurations and addons. So only do it when the other alternatives fail.

---

### Post by rudybaby on 2017-06-10
Thank you for the help. I reinstalled Mint and Kodi was working as it should. There seems to be problems with Kodi wherein I am not alone.

---

### Post by Tadaen_Sylvermane on 2017-06-12
I'd recommend using the kodi ppa instead of the package manager version. I use unstable myself. Never had a problem with stable or unstable on ubuntu from the ppa (when I used it.)```
ppa:team-xbmc/ppa
``````
ppa:team-xbmc/unstable
```

---

