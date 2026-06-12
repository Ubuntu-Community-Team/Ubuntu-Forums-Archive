---
title: "Whatsapp For Desktop"
date: 2021-06-21
forum: New to Ubuntu
---

### Post by jackdusty on 2021-06-21
Another Question Quy's

I want to be able to make voice and video calls via whatsapp from my desktop (I am an Iphone 11 users) , - I have done some research and I understand I need some kind of emulator, is this correct and if so what is the best and simpleist emulator for an Iphone.


Thanks



Jack

---

### Post by ActionParsnip on 2021-06-21
You can use the web client. I'm unsure how feature rich it is
[https://web.whatsapp.com/](https://web.whatsapp.com/)

---

### Post by ActionParsnip on 2021-06-21
Or use whatdesk
[https://websiteforstudents.com/how-to-install-whatsapp-on-ubuntu/](https://websiteforstudents.com/how-to-install-whatsapp-on-ubuntu/)

---

### Post by jackdusty on 2021-06-21
Looked at those they only give messaging not calling facilities

---

### Post by ActionParsnip on 2021-06-21
WhatsApp is proprietary protocol so until they make a client for Linux you're pretty much screwed.

---

### Post by ActionParsnip on 2021-06-21
The Windows client doesnt run in WINE either
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=17534](https://appdb.winehq.org/objectManager.php?sClass=application&iId=17534)

If you can get your pals to install something you can chat with on Linux as well then you will be OK

---

### Post by TheFu on 2021-06-22
There are many, many, options in this space.  Over the last few months, most of my friends and family closed their WhatsApp accounts due to FB demands for data.  [https://www.bleepingcomputer.com/news/technology/whatsapp-to-restrict-features-if-you-refuse-facebook-data-sharing/](https://www.bleepingcomputer.com/news/technology/whatsapp-to-restrict-features-if-you-refuse-facebook-data-sharing/)
Most moved to telegram (or was it signal)?  I don't recall.  The nerds moved to Matrix which does point-to-point encryption and supports federated servers like all our different email servers are federated. No single company holding all the servers and data.

Of course, not everyone has the same level of interest in these things.
Sometimes the only answer is to run a Windows virtual machine to have Windows-only applications work. I do that for a few applications.

---

### Post by jackdusty on 2021-06-22
For saying the number of people that use Whatsapp and the principle of Linux I feel it would be a backwards step to run Windows in a VM machine, I am surprised more people are not up in arms about it

---

### Post by TheFu on 2021-06-22
> **jackdusty said:**
> For saying the number of people that use Whatsapp and the principle of Linux I feel it would be a backwards step to run Windows in a VM machine, I am surprised more people are not up in arms about it

Does [https://snapcraft.io/whatsapp-for-linux](https://snapcraft.io/whatsapp-for-linux) not work? It doesn't do the audio stuff.  Should be in the the _Software Store_ for GUI users or just run 
```
sudo snap install whatsapp-for-linux
```

Appears there are lots of other options to try:
```
$ sudo snap search whatsapp
Name                Version        Publisher        Notes  Summary
whatsapp-for-linux  1.1.7          nshecan          -      An unofficial WhatsApp desktop application for Linux.
whatsapp-4linux     1.1.0          chimekkoo        -      WhatsApp unofficial desktop app for linux
whatsie             0+git.e03ea12  keshavnrj        -      WhatsApp Web Client written in Qt
whatsdesk           0.3.5          zerkc            -      whatsdesk
ramboxpro           1.5.2          ramboxapp&#10003;       -      Rambox Pro
kesty-whatsapp      1.2.5          olubunmi708      -      An unofficial fast and reliable whatsapp client for linux. Enjoy smooth notification and lock screen alerts and so on.
walc                0.2.1          cstayyab         -      WALC - unofficial WhatsApp Linux Client
wrapup              0.1.3          validatedev      -      A Whatsapp client for Linux
wazzapp             0.1.9          elpombo          -      Unofficial WhatsApp client for Linux.
beeper-beta         2.0.9          novachat         -      Beeper is a multi-network chat app
beeper              2.0.9          novachat         -      Beeper is a multi-network chat app
matterbridge        1.22.3         popey            -      MatterBridge protocol bridge
```
That's just the snap store.  
In APT, the normal repos, there is yowsup-cli - no GUI. [https://manpages.ubuntu.com/manpages/xenial/man1/yowsup-cli.1.html](https://manpages.ubuntu.com/manpages/xenial/man1/yowsup-cli.1.html)

We've also learned that convincing companies like facebook to do anything for a 2-5% base of users is like blowing into a hurricane.

I don't think anyone made any suggestions for an iPhone emulator either.  Apple ignores Linux all the time.  I've never heard of any iPhone emulator that didn't require an apple OS and apple hardware. [https://askubuntu.com/questions/539233/how-to-install-an-iphone-application-in-linux](https://askubuntu.com/questions/539233/how-to-install-an-iphone-application-in-linux) seems to confirm this, but that's just one answer.

There are a number of Android emulators that run on Linux. If fact, you can connect to a real android device and control it from Linux all day over USB, if you like.  There are a number of tools for that.  I don't think the audio is integrated, just the mouse and screen.  scrcpy is one of those tools.  There are others.  A $40 android phone, wifi-only network connection with USB cable to Linux and you're done - unless whatsapp requires a phone number?  Then you'll need a cheap cell plan.

Of course, someone with an itch and the skills to scratch it by developing a solution can do amazing things.

Lots of other options, if bridges can work.  Remove whatsapp and a few other tracking/social apps, but still have access from a F/LOSS tool from your desktop or phone or tablet or a websites that is under your control.
[https://matrix.org/docs/guides/whatsapp-bridging-mautrix-whatsapp/](https://matrix.org/docs/guides/whatsapp-bridging-mautrix-whatsapp/) 
[https://zblesk.net/blog/setting-up-matrix-bridges/](https://zblesk.net/blog/setting-up-matrix-bridges/)

---

### Post by monkeybrain20122 on 2021-06-22
> **TheFu said:**
>   A $40 android phone, wifi-only network connection with USB cable to Linux and you're done - unless whatsapp requires a phone number?  Then you'll need a cheap cell plan.



It does require a phone #, but apparently a virtual number can work
[https://sendapp.live/en/2020/04/08/virtual-number-to-turn-on-whatsapp/](https://sendapp.live/en/2020/04/08/virtual-number-to-turn-on-whatsapp/)

---

### Post by jackdusty on 2021-06-23
None give voice and video calling

---

### Post by monkeybrain20122 on 2021-06-23
> **jackdusty said:**
> None give voice and video calling

Just use a phone. that is the normal use case anyway. If you must and have a Windows license set up a VM (I don't think you can make calls from any android emulator but I can be wrong)

---

### Post by TheFu on 2021-06-23
> **monkeybrain20122 said:**
> Just use a phone. that is the normal use case anyway. If you must and have a Windows license set up a VM (I don't think you can make calls from any android emulator but I can be wrong)

Don't know, but that would be surprising, since there are VoIP apps that work inside Android emulators on Linux. I've done it.

Can't test the WhatsApp aspects. Won't load any of the major social network/tracking apps on my phones.
The main reason I can see for wanting this is to have automated dialing or automated chat ... which would be possible using cness for the dialing and any of the the other options can do chat.  With VoIP, an asterisk/freeswitch server can be used by hundreds of different people concurrently.  I had Skype-Out setup for about a year to replace both older VoIP and POTS phone service long ago.  It was just before MSFT bought Skype and it usually worked, but I wouldn't bet a business on it.  Dumped that for a quality VoIP provider and never thought about it again.  Use phones through an ATA, computers, tablets, cell phones all through VoIP with that service from all around the world.  Normal SIP traffic over an openvpn tunnel back home to my server there before hitting the service provider.  About 1 in 30 times, the VPN connection doesn't work. It used to be much worse.

The point is there are all sorts of methods, but none are a 1-click install and none are a direct, 1-for-1 replacement that makes the OP happy.  Let your inner nerd free and there are lots of options.

I wish you all luck.

---

### Post by jcas0058 on 2021-12-27
I once tried an electron-cointained app emulating Whastapp web. It was quite slow, so I ended-up using Whatsapp web directly on my browswer.

---

