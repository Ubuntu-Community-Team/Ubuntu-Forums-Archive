---
title: "Help with splash screen"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by famous3warriors on 2008-07-03
I have ubuntu studio 8.04 hardy heron i386.  I upgraded from just ubuntu 8.04 to ubuntu studio and when I did something happen to the splash screen when the system shuts down.  When first booting in the system the screen that has ubuntu studio logo and underneath it there is the name and the bar that goes back and forth and that same as when you shut down the system.  I get the splash screen when it first boots up but when it shuts down my screen just fades to black then shuts down.  Is there any way to reset it or fix that problem?  Thanks for your help.:confused:

---

### Post by hakko on 2008-07-03
Try booting with the Ubuntu 8.04 CD and see if there is a repair option.

Also you can try this for another issue:
> 
 Fix the shutdown "Network Error" display (restore shutdown splash screen)

Many Ubuntu systems have a minor bug when shutting down. Instead of displaying a splash screen indicating the progress of the shutdown process, the user is dropped out to a console screen flooded with shutdown notices (mostly network error messages). These messages are normal and expected, there is nothing to be concerned about. But it can be a bit unsightly, and it would seem that the Ubuntu team intended to have those messages hidden by the splash screen. The splash screen can be restored without much effort:

    * Go to System &#8594; Administration &#8594; Login Window, and select the Local tab
    * Select a different theme, then re-select the default theme ("Human"). This just refreshes the setting
    * Click Close, then go back to System &#8594; Administration &#8594; Login Window, and select the Local tab again
    * You'll notice that the settings are different to what you've just chosen. Restore the setting to their defaults -- Choose Selected only from the Theme drop-down box (instead of "Random from selected"), and re-select the default Ubuntu theme ("Human"). When complete, click Close. The setting will have saved properly this time, and the shutdown splash screen should work as intended.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29)


---

### Post by philinux on 2008-07-03
The only repair broken system option is on the alternate cd.

I don't think thats necessary to fix this.

Sounds like usplash has a problem.

Like the previous poster says, sometimes changing themes and then back again can fix it.

---

### Post by famous3warriors on 2008-07-03
Thansk guys I really do appreciate your help I will give this a try.

---

