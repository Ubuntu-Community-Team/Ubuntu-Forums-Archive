---
title: "IceCat 6.01 slow after new version intalled"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by Wanda's on 2011-09-08
[SIZE=2]Greetings,[/SIZE]

[SIZE=2]A couple of days ago I had an update for the new version to IceCat 6.01 it came with two plug-in which I have disabled hoping that it would improve the slowness. I believe there is a problem specifically with flash as the pages that stream do not load. I am running Lucid Lynx 10.04. 

Prior to the upgrade, Icecat ran perfectly. I have considered removing this latest version and replacing it with Icecat 5.0.1. I am not sure how to go about doing that and retaining all my bookmarks from this newer version that is just not working well enough.  Or should I try to resolve the problem of crash/flash and very slow loading of pages? I am not sure where I could get help with this Gnu for Ubuntu browser, which I like **very** much.

Any advice is welcome. Please make your response simple. TIA
[/SIZE]

---

### Post by mvelte54 on 2011-09-11
I too am disappointed with the latest update to Icecat, when I start Icecat all is well but if I close it then I get nothing when I try to open it again.
After going into systems monitor to see whether it's running or not I get this:
Icecat          sleeping
Icecat-bin    zombie
Icecat-bin    zombie
Icecat-bin    zombie
Icecat-bin    sleeping

I then highlight all then 'end process' then I can open it again. 

I guess we will just have to wait till some one comes up with a fix for this. Saving your bookmarks is the same as if you were in 'Firefox' go to bookmarks > organize bookmarks > import and back up. Click on import and backup select where you would like to save, backup; your bookmarks then you can uninstall Icecat without worry of losing your bookmarks.
If I may suggest you might want to store them not only on your hard drive but a USB if you have access to one and for an added measure email them to yourself.

Also you should not have posted this as 'solved' as it is not...
Hopefully someone will take pity on our poor souls and maybe help us out.

---

### Post by Mr_Freez3 on 2011-09-12
Hello,

I found a fix for the flash causing Icecat to crash problem thanks to Google.  Here is the [link]("https://lists.gnu.org/archive/html/bug-gnuzilla/2011-08/msg00040.html").

To do the fix, open a new tab and type  about:config  in the URL/address bar.  Click the "I'll be careful, I promise!" box.  Then in the "Filter:" bar at the top of the page, type  dom.ipc.plugins.enabled  .  Now you should see 4 items listed...and you will see "dom.ipc.plugins.enabled" is set to "true".  Double-click that item to change it to "false".  That should make all 4 items listed set to "false".  Now close Icecat and the next time you open it, flash should work again.

Hope that helps you out.

Icecat 6.0.1 from ppa:gnuzilla-team/ppa on Linux Mint 11 (Ubuntu 11.04)

---

