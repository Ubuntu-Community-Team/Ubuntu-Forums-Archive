---
title: "[SOLVED] Network Manager Bus connection failed?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by germanix on 2008-10-07
Normally when I shut-down Ubuntu it makes a very elegant exit. The Ubuntu Logo appears and it switches off. Now all of a sudden, without me having changed anything, the following happens:
On shut down the Ubuntu Logo appears, then I get a black screen with the cursor blinking in the top left corner, after some time the screen fills with text about "Network manager Bus connection failed" and then it only switches off. I tried a couple of re-boots getting the same effect. Any ideas what this could be and how I can correct it? I know it is maybe not that serious but its very nervy.

---

### Post by germanix on 2008-10-08
bump

---

### Post by bumanie on 2008-10-08
On occasions I have seen the same message - never looked into what it exactly means as the computer is working fine - unless something is obviously broken, I would leave it alone. Trying to fix something that doesn't need fixing, brings the possibility of breaking something else. You could look up launchpad and see if the issue had been logged with them or not.

---

### Post by jasonchoi on 2008-10-31
Do you mind sharing the solution? i have the same problem. Private message sent. Thanks.

---

### Post by germanix on 2008-10-31
There are 2 fixes for this problem. The fix listed below is one of them. This fix helps in a lot of the cases. Hope it works for you. I cannot remember where I stored the 2nd fix, should this one not work but I will look for it.

Fix the shutdown "Network Error" display (restore shutdown splash screen) 
Many Ubuntu systems have a minor bug when shutting down. Instead of displaying a splash screen indicating the progress of the shutdown process, the user is dropped out to a console screen flooded with shutdown notices (mostly network error messages). These messages are normal and expected, there is nothing to be concerned about. But it can be a bit unsightly, and it would seem that the Ubuntu team intended to have those messages hidden by the splash screen. The splash screen can be restored without much effort: 
Go to System &#8594; Administration &#8594; Login Window, and select the Local tab 
Select a different theme, then re-select the default theme ("Human"). This just refreshes the setting 
Click Close, then go back to System &#8594; Administration &#8594; Login Window, and select the Local tab again 
You'll notice that the settings are different to what you've just chosen. Restore the setting to their defaults -- Choose Selected only from the Theme drop-down box (instead of "Random from selected"), and re-select the default Ubuntu theme ("Human"). When complete, click Close. The setting will have saved properly this time, and the shutdown splash screen should work as intended.

---

### Post by germanix on 2008-10-31
There are 2 fixes for this problem. The fix listed below is one of them. This fix helps in a lot of the cases. Hope it works for you. I cannot remember where I stored the 2nd fix, should this one not work but I will look for it.

Fix the shutdown "Network Error" display (restore shutdown splash screen) 
Many Ubuntu systems have a minor bug when shutting down. Instead of displaying a splash screen indicating the progress of the shutdown process, the user is dropped out to a console screen flooded with shutdown notices (mostly network error messages). These messages are normal and expected, there is nothing to be concerned about. But it can be a bit unsightly, and it would seem that the Ubuntu team intended to have those messages hidden by the splash screen. The splash screen can be restored without much effort: 
Go to System &#8594; Administration &#8594; Login Window, and select the Local tab 
Select a different theme, then re-select the default theme ("Human"). This just refreshes the setting 
Click Close, then go back to System &#8594; Administration &#8594; Login Window, and select the Local tab again 
You'll notice that the settings are different to what you've just chosen. Restore the setting to their defaults -- Choose Selected only from the Theme drop-down box (instead of "Random from selected"), and re-select the default Ubuntu theme ("Human"). When complete, click Close. The setting will have saved properly this time, and the shutdown splash screen should work as intended.

---

### Post by jasonchoi on 2008-11-01
sadly your first fix is not an option for me as i accidentally deleted all my themes. But i think that fix makes sense because it the error message happened after i installed a custom gdm. i am definitely going to be waiting for you second fix.


Thanks alot for the help

---

