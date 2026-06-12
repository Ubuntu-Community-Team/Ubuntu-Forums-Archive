---
title: "Gateway NV53 - Mobility Radeon HD 4200"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by Juices on 2012-12-14
Hey, I'm new to Ubuntu! I spent my entire night last night confused trying to install my ATI proprietary driver. I read that it can be activated under Software Sources but no matter what I do (I enabled Canonical Partners repository, and ran apt-get update) I was never presented with an option. The integrated card in question is in the thread title. How do I go about getting the ATI drivers installed?

---

### Post by QIII on 2012-12-14
Are you using Ubuntu 12.10?

---

### Post by Juices on 2012-12-14
Yes, I accidentally left that out. I'm running Ubuntu 12.10

---

### Post by QIII on 2012-12-14
Then I am afraid you won't be able to install a proprietary driver unless you are willing to downgrade your X Server to 1.12 from 1.13 -- which I highly recommend against.  The "additional drivers" method will not offer you a driver.  If someone wants to come along and point you towards one of the many sites that tell you how to use a script to downgrade X Server and install the legacy driver, they are welcome to and you are welcome to do so.  I can't personally recommend it.  It effectively breaks your OS and it is impossible to tell what problems you may have in the future when you upgrade to the next version of Ubuntu.

This is not a problem with Ubuntu.  AMD/ATI has chosen to put their proprietary drivers for all HD 1000 - HD 4000 series cards in a legacy branch and they will work only with versions of Linux that use X Server 1.12 and earlier.  Quantal uses 1.13.

That is to say that your card is no longer supported in Linux by AMD/ATI.

You man continue to use the default open source Radeon driver, which should meet the needs of the vast majority of users. 

If your machine is a laptop and you encounter overheating issues with the open source driver, you may install Jupiter to manage power consumption -- and the heat that goes with it.

---

### Post by Juices on 2012-12-14
> **QIII said:**
> Then I am afraid you won't be able to install a proprietary driver unless you are willing to downgrade your X Server to 1.12 from 1.13 -- which I highly recommend against.  The "additional drivers" method will not offer you a driver.  If someone wants to come along and point you towards one of the many sites that tell you how to do that, they are welcome to and you are welcome to do so.  I can't personally recommend it.  It effectively breaks your OS and it is impossible to tell what problems you may have in the future when you upgrade to the next version of Ubuntu.

This is not a problem with Ubuntu.  AMD/ATI has chosen to put their proprietary drivers for all HD 1000 - HD 4000 series cards in a legacy path and they will work only with versions of Linux that use X Server 1.12 and earlier.  Quantal uses 1.13.

That is to say that your card is no longer supported by AMD/ATI.

You man continue to use the default open source Radeon driver, which should meet the needs of the vast majority of users. 

If your machine is a laptop and you encounter overheating issues with the open source driver, you may install Jupiter to manage power consumption -- and the heat that goes with it.
Looks like I'm going to go install Jupiter now.

---

### Post by QIII on 2012-12-14
I wish I had been able to give you better news.  I'm a bit unhappy with AMD/ATI right now after having defended them in the Linux community for years.

---

