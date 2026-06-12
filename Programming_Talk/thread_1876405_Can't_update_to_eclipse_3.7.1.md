---
title: "Can't update to eclipse 3.7.1"
date: 2011-11-06
forum: Programming Talk
---

### Post by Frozen Forest on 2011-11-06
I was hoping to give java 7 a try and besides installing openjdk-7 was I trying to update eclipse to 3.7.1 problem is that I get this error. Got these sites in the software sites
[http://download.eclipse.org/eclipse/updates/3.7](http://download.eclipse.org/eclipse/updates/3.7)
[http://eclipse-color-theme.github.com/update/](http://eclipse-color-theme.github.com/update/)
[http://download.eclipse.org/releases/indigo/](http://download.eclipse.org/releases/indigo/)
[http://pydev.org/updates](http://pydev.org/updates)

Using Xubuntu 11.10

```

Cannot complete the install because of a conflicting dependency.
  Software being installed: Eclipse Plug-in Development Environment 3.7.1.r37x_v20110810-0800-7b7qFVtFEx2XnmZ4jlM5mjM (org.eclipse.pde.feature.group 3.7.1.r37x_v20110810-0800-7b7qFVtFEx2XnmZ4jlM5mjM)
  Software currently installed: Eclipse Platform 3.7.0.I20110613-1736 (org.eclipse.platform.ide 3.7.0.I20110613-1736)
  Only one of the following can be installed at once: 
    Eclipse RCP 3.7.0.dist-9gBsFnkFlfr2B21319 (org.eclipse.rcp.feature.jar 3.7.0.dist-9gBsFnkFlfr2B21319)
    Eclipse RCP 3.7.1.r37x_v20110729-9DB5FmNFnFLSFCtLxnRfMqt15A4A (org.eclipse.rcp.feature.jar 3.7.1.r37x_v20110729-9DB5FmNFnFLSFCtLxnRfMqt15A4A)
    Eclipse RCP 3.7.0.v20110216-9DB5Fm1FpBGy_AaVz-mFamgY (org.eclipse.rcp.feature.jar 3.7.0.v20110216-9DB5Fm1FpBGy_AaVz-mFamgY)
  Cannot satisfy dependency:
    From: Eclipse Plug-in Development Environment 3.7.1.r37x_v20110810-0800-7b7qFVtFEx2XnmZ4jlM5mjM (org.eclipse.pde.feature.group 3.7.1.r37x_v20110810-0800-7b7qFVtFEx2XnmZ4jlM5mjM)
    To: org.eclipse.platform.feature.group 3.7.1
  Cannot satisfy dependency:
    From: Eclipse Platform 3.7.0.dist-9pF7UHbtFs8vdhkukhQodUHz-siCnGGYotSeiRH (org.eclipse.platform.feature.group 3.7.0.dist-9pF7UHbtFs8vdhkukhQodUHz-siCnGGYotSeiRH)
    To: org.eclipse.rcp.feature.group [3.7.0.dist-9gBsFnkFlfr2B21319]
  Cannot satisfy dependency:
    From: Eclipse Platform 3.7.1.r37x_v20110729-9gF7UHOxFtniV7mI3T556iZN9AU8bEZ1lHMcVK (org.eclipse.platform.feature.group 3.7.1.r37x_v20110729-9gF7UHOxFtniV7mI3T556iZN9AU8bEZ1lHMcVK)
    To: org.eclipse.rcp.feature.group [3.7.1.r37x_v20110729-9DB5FmNFnFLSFCtLxnRfMqt15A4A]
  Cannot satisfy dependency:
    From: Eclipse Platform 3.7.0.I20110613-1736 (org.eclipse.platform.ide 3.7.0.I20110613-1736)
    To: org.eclipse.platform.feature.group [3.7.0.dist-9pF7UHbtFs8vdhkukhQodUHz-siCnGGYotSeiRH]
  Cannot satisfy dependency:
    From: Eclipse RCP 3.7.0.dist-9gBsFnkFlfr2B21319 (org.eclipse.rcp.feature.group 3.7.0.dist-9gBsFnkFlfr2B21319)
    To: org.eclipse.rcp.feature.jar [3.7.0.dist-9gBsFnkFlfr2B21319]
  Cannot satisfy dependency:
    From: Eclipse RCP 3.7.1.r37x_v20110729-9DB5FmNFnFLSFCtLxnRfMqt15A4A (org.eclipse.rcp.feature.group 3.7.1.r37x_v20110729-9DB5FmNFnFLSFCtLxnRfMqt15A4A)
    To: org.eclipse.rcp.feature.jar [3.7.1.r37x_v20110729-9DB5FmNFnFLSFCtLxnRfMqt15A4A]

```

---

