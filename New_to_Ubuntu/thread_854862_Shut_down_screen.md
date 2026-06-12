---
title: "Shut down screen???"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by FAMUgolfer on 2008-07-09
I'm having problems finding and working a solution to the shut down splash screen that i usually find when i first turn on my computer. its an acer with nvidea graphics card.  i searched all throughout the forum and havent seen any resolutions that fit my scenario.

When i shut down the computer, it usually looks like all the icons are gone except for my background image.  Then a series of blue squiggly lines on a black background appear for about 5 seconds before the screen goes completely black. And from there it looks like that screen illuminates from black to white before finally shutting down.  This whole process takes about 15 seconds total.

I never had this problem in 7.10 and have never seen the usual shut down loading bar splash screen since i upgraded to 8.04.

thank you for your help

---

### Post by bab1 on 2008-07-09
There are a number of splash screens.

The first is the BIOS splash, but I doubt you mean that.  Although your > when i first turn on my computer might indicate  it.

The second is the Grub splash screen which is loaded when the O/S is first loaded.  it is controlled by /boot/grub/menu.1st.  

Third is the usplash screen that is loaded when the system is coming up and going down.  I believe this is what you are looking for.

Here is a short tutorial:
[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html")

---

### Post by FAMUgolfer on 2008-07-10
Thank you for your response.

I think i should have been more specific when i mentioned splash screen.

I remember in 7.10, the loading bar splash screen would appear during the shut down sequence.

In 8.04 i am not getting this screen. I see nothing on SUM to get this screen back except changing the splash screens. What should I do to get the shut down loading bar bar splash screen.

I have no problems with the start-up loading bar, just the shut down loading bar is not visible and instead i get squiggly lines and a black to white illuminating fade.

Thank you.

---

### Post by LowSky on 2008-07-10
I had the same issue with Gutsy not Hardy, install a program called start-up manager (its in Add/Remove) its a GUI based tool to modify Grub and to use you monitors setting properly (like the correct screen size), which somehow is the root to your problem

---

### Post by kansasnoob on 2008-07-10
I'll bet you installed Hardy by "upgrade".

I've had about 50/50 luck with upgrades. That's out of 20+ upgrades.

Then again it appears that everything can be worked out.

---

