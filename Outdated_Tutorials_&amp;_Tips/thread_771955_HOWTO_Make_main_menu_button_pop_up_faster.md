---
title: "HOWTO: Make main menu button pop up faster"
date: 2008-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by oakgrove on 2008-04-28
I posted about this in Absolute Beginners but thought it was important enough to put it here too.  This also assumes, you have replaced the Applications|Places|System menu bar with the "Main Menu" button in the panel applets selection menu.

Introduction: Like many people, I can't stand having the Applications|Places|System menu bar hogging up my panel real estate.  So, again like many people, I replaced it with the "Main Menu" menu which consolidates all three of the former menus into one clickable button on the panel.  

The only problem is, this new button is much slower than the former three the first time you click it after a reboot as unlike the former, it isn't cached automatically.  I looked high and low for a good solution to this issue and couldn't find one.  So, after tinkering around a bit, I realized that since the Applications|Places|System menu bar is cached upon boot up and the Main Menu button has the same entries as the bar, maybe if they are both on the panel, the Main Menu will receive the benefits of the caching and will pop right up when you press it the first time.  

Well, I put them both on there, rebooted, and it actually worked.  Only problem is, you're right back where you started with a big old menu bar on your panel that you don't want along with the much smaller main menu button that you do want.

The solution:

1. Right click on the panel and click "Add to Panel..."

2. Find the "Drawer" applet, click it and then click add.  You now have a drawer which can hold (and hide) other applets on your panel.

3. Right click on this new drawer and click "Add to drawer..."

4. On the dialog that pops up, click "Menu Bar" then click Add.

5. Now, just right click on the drawer, select "Move" and place it wherever you want it.  Preferably in as unobtrusive spot as possible.

Wrap up: That's it.  Now instead of a big menu taking up so much space, you just have a tiny drawer.  And since the menu is there inside of the drawer, you get the benefit of it caching the entries so your other "Main Menu" will just pop right up now.  To really see the difference, just reboot and click on it.  It should pop up virtually immediately.

I hope this helps.

---

### Post by Doug77 on 2009-03-03
Thanks a lot; I had this problem and this solution works.  It would be nice to not even have the drawer icon (I really try to maximize screen real estate), but at least now my menu is cached.

---

