---
title: "Thunderbird Mail/Calender Problem"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by cressrt2 on 2013-10-28
Hi,
I have an error coming up when I load Thunderbird Mail, it gives the following message, error code and details, any ideas as to how to rectify please?
(Running Ubuntu 12.04, not Lubuntu)

"An error was encountered preparing the calendar located at moz-abdirectory:// for use. It will not be available."

Errot Code: 0x80570015

Details
[Exception... "Component returned failure code: 0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE) [nsIJSCID.createInstance]"  nsresult: "0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE)"  location: "JS frame :: resource://calendar/modules/calUtils.jsm -> file:///home/elcallao/.thunderbird/jxxe4iu7.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/calendar-js/calUtils.js :: <TOP_LEVEL> :: line 22"  data: no]

---

### Post by vanadium on 2013-10-28
Check wether this is a problem related to the faulty Lightning 2.6.1 being pushed on your system: [http://ubuntuforums.org/showthread.php?t=2184227](http://ubuntuforums.org/showthread.php?t=2184227)

---

### Post by cressrt2 on 2013-10-28
I can't see of this is installed, it is not showing as Installed in the Software Centre, is there anywhere else I should check?

---

### Post by marianoa on 2013-10-28
I've had a problem a few days ago with lightning, I solved it removing the extension from the Add-on page in Thunderbird and then installed it via the package manager (xul-ext-lightning). The problem could be related to this:

=====================================================
If you are using Linux, be sure to use the **exact version combination**:
Thunderbird 24.0: Lightning 2.6
Thunderbird 24.0.1: Lightning 2.6.1
Thunderbird 24.1.0: Lightning 2.6.2
=====================================================

(taken from [https://addons.mozilla.org/it/thunderbird/addon/lightning/](https://addons.mozilla.org/it/thunderbird/addon/lightning/))

---

### Post by cressrt2 on 2013-10-28
Thanks to you both, it was the 2.6.1 but I did not find it right away.

---

