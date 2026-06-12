---
title: "Shifted image when hovering..."
date: 2022-12-29
forum: New to Ubuntu
---

### Post by Innernet on 2022-12-29
Good day.
I was buying some equipment at ebay and the magnified image of products when hovering over them, shifts way to the right outside field of view.  Tried several other products; same behavior.  Can you suggest a cure to keep it within centre of screen ?  I did not tweak any changes at all.  Firefox did its forced update recently.
[ATTACH=CONFIG]291480[/ATTACH]

---

### Post by Innernet on 2022-12-30
(*,)  I do need a new brain...  :confused:  Some expert that can explain, please ?

This is a screen from ebay  :
Are they telling ME that they cannot access their own server ?

How to 'refresh' the browser window???  beyond I did shut power off and on again; closed Firefox and open again.  Same message shows up.   Started happening on ebay visits after Firefox force updated its thing.  Always, every time they do it affects behavior in some way.

Attached screenshot

---

### Post by tea for one on 2022-12-30
Possibly Firefox Troubleshoot Mode may help?
[https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode](https://support.mozilla.org/en-US/kb/diagnose-firefox-issues-using-troubleshoot-mode)

---

### Post by Innernet on 2022-12-30
Thank you.
Entered the troubleshoot mode as you suggested and idled for about 30 seconds returning then to the troubleshooting mode instruction page with no dialog nor results of troubleshooting. 
 
I expected "the problem was not found", or "there is such and such problem", or "the problem was fixed".     -**Nothing** shown.- :(    Went to an ebay product for sale; same thing, a blank right side of the page.

---

### Post by Holger_Gehrke on 2022-12-30
I'd use the Firefox profile manager ('firefox --ProfileManager') to create a new profile without whatever add-ons you've got installed and try accessing ebay using that profile. If that works as it should, then you can try temporarily deactivating your add-ons one by one to see which one is to blame. I can tell you that on my system (XUbuntu 22.04 with Firefox 108.1 snap with Privacy Badger, ublock Origin, Noscript, Gesturify, Flag Fox and Mega add-ons) the page seems to behave as intended with details about the auction about 2 em to the right of the image getting hidden by the enlarged image and re-appearing when the pointer is outside of the image.

Holger

Edit: Never mind, after reading the link about trouble shoot mode I find that that would already deactivate all customization, so if that didn't work then this wouldn't either ...

---

### Post by tea for one on 2022-12-30
Boot into a live Ubuntu 22.04 session.
Open Firefox and visit the ebay site.
Any good?

---

### Post by Innernet on 2022-12-31
Thanks.  
Do not know what is a "live" Ubuntu session, nor how to do it.  I assume from your words Firefox has to be closed first; then power cycle shut-off to reboot and ... ?

---

### Post by tea for one on 2022-12-31
"Live Ubuntu session" or "Try Ubuntu"
More info here [https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

In essence, you will be using a virgin OS together with a pristine Firefox.
Hopefully, your ebay page will display correctly?
It would be a good move to use Ubuntu 22.04 for this exercise because it is an LTS and widely used.

---

### Post by Innernet on 2022-12-31
Hello.
Booted with the 22.04 CD, (same version I have in the hard drive) unable to get to ebay as that version did **not** include a browser in the CD.  :(
Tried with a 20.04 CD; did not boot from the CD by whatever reason, tried twice.  and went by itself to boot from the default hard drive.  Stopped, I turned it off. :(
Tried 18.04 CD, booted fine and worked as 'try Ubuntu' ; It **has** Firefox included, could not discern which version.  Got to ebay site and showed perfectly fine sevral different items-pages with no blank center, and proper magnification on screen range  :).  Now am typing this with the 18.04 live CD, behaving fine.

---

### Post by Innernet on 2022-12-31
Am back to 'normal' 22.04 hard drive boot,   Using the native Ubuntu - WEB browser instead of Firefox, went to Ebay and all works fine, images within range and in screen center.  In my ignorance; I would say it is Firefox fault.
What is next ? 
Guessing  - request a Firefox update and pray it will not behave worse ?  Any command to do it from the terminal, if you approve my guessing or better your expertise please ?

---

