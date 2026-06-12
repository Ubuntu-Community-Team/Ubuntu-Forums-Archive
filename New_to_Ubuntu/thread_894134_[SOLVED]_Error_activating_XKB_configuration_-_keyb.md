---
title: "[SOLVED] Error activating XKB configuration - keyboard mixed up"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-19
after upgrade to 8.04 and a few problems I now have everything working except a problem with XKB which means all my keyboard symbols are mixed up
UIM for japanese works OK
Ive done a search and it seems I need to change some settings in xorg.conf but I have no idea how to go about this
any ideas

the error message on start up is  

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by LTFC2020 on 2008-08-19
using the command sudo dpkg-reconfigure xserver-xorg

and following the instructions leads to 

 For the X server to handle the keyboard correctly, a keyboard model must  &#8593; 
 &#9474; be entered.  Available models depend on which XKB rule set is in use.     &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474;  With the "xorg" rule set:                                                &#9618; 
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys, common in   &#9618; 
 &#9474;           the United States.  Has no "logo" or "menu" keys;               &#9618; 
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually engraved  &#9618; 
 &#9474;           with a "logo" symbol and a "menu" symbol;                       &#9618; 
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - pc105: similar to pc104 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - macintosh: Macintosh keyboards using the new input layer with Linux    &#9618; 
 &#9474;               keycodes;                                     
 For the X server to handle the keyboard correctly, a keyboard model must  &#8593; 
 &#9474; be entered.  Available models depend on which XKB rule set is in use.     &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474;  With the "xorg" rule set:                                                &#9618; 
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys, common in   &#9618; 
 &#9474;           the United States.  Has no "logo" or "menu" keys;               &#9618; 
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually engraved  &#9618; 
 &#9474;           with a "logo" symbol and a "menu" symbol;                       &#9618; 
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - pc105: similar to pc104 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - macintosh: Macintosh keyboards using the new input layer with Linux    &#9618; 
 &#9474;               keycodes;                                     

which is stuck and I cannot enter my preferences
I us jp 106 keyboard

---

### Post by LTFC2020 on 2008-08-19
solvedish
had to burn a cd iso and do a complete reinstall
won't be using the update manager for installing again ](*,)

---

