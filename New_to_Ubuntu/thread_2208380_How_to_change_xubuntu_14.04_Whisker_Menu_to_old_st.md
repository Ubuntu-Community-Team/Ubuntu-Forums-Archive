---
title: "How to change xubuntu 14.04 Whisker Menu to old style menu?"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by Erik_Lash on 2014-02-28
So I'm a recent linux convert and settled on xubuntu 12.04 last year after trying out various flavors. 

One of the things I especially like about it was the panel menu that was clean, uncluttered, easy to navigate, well designed (graphically), and intuitive to use. It was really the deciding factor for me in picking xubuntu over other flavors.

Because of my favorable experiences with xubuntu I decided to become an early adopter of 14.04 when the Beta came out. 

By default in the 14.04 Beta the Whisker menu is enabled. While I fully understand that a lot of people like that menu, it makes me cringe everytime I open it. It was the main reason I stayed away from Linux Mint. It's just not my preferred type of menu/application interface. 

This newbie would like to go back to the old xubuntu xfce menu style and is trying to figure out how to do that. I'm not finding anything in my searches and can't seem to find a menu item that will let me do it.

Could someone please tell me what I need to do to completely disable (or remove) the Whisker menu in 14.04 and go back to the older menu style that is standard in xubuntu releases up until now? Or point me in the direction of the instructions to do so?

Thanks!

---

### Post by Dennis N on 2014-02-28
Right click on panel. Choose [B]Panel > Panel Preferences > Items
[/B]Select Whisker Menu and press the red **X** on the right (remove)
Then press **+** on the right for new item, select 'Applications Menu' and finally press 'Add'
Use the up and down arrows to position it where you want.

---

### Post by Erik_Lash on 2014-02-28
Works Perfect. Thanks.

---

### Post by artie3 on 2014-03-05
Hi Erik, 

I'm also using 14.04, although I run it from a USB flash drive. So far, my 14.04 runs like a champ!!!

I have the same feelings about the whisker menu. But, I left my whisker menu in place and created 2 new panels. Both are vertically oriented and I have them set to autohide. In both panels, I placed the old style menus as directed above. In my left hand panel, I have utility programs and related launchers and my right hand panel has commonly used programs. But, having the old style menu in both panels works for me.

I'm loving 14.04 so far, haven't encountered any  of the instability or broken functions that we'e warned about when we download 14.04.

Enjoy.

Artie

---

### Post by The Cog on 2014-03-05
I think whisker menu would look really good if only it wasn't backwards. The category buttons should be on the left of the applications panel, so that usage flows from left to right. As it is, usage flows from the left edge to launch the menu, to the category button on the right, and then back to the left edge for the application. It's just awkward.

---

### Post by james-auble2 on 2014-05-02
I like Whisker Menu and have used it on other distros but have never had  editing issues with it like I've had so far on Xubuntu 14.04. I found  today that I couldn't add items to the System category with MenuLibre,  Alacarte, or by manually editing .desktop files. Became pretty  frustrated as it seems like this is a common task that should be pretty  simple and straight forward. Finally I found a post from somebody else  with the same issue (can't find the post anymore) that described a  simple fix for this. Open MenuLibre (by terminal if it's not in whisker,  or right click on the panel applet), find the item you'd like to have  show up under 'System', and remove the line that says Settings -  Settings under category attributes. This will unlock the item so you can  do as you please with it. A simple fix but I wouldn't have figured it  out without finding that post so if you're having the same problem I  hope that works!

Sorry if it seems I hijacked this thread, but with my search string for this issue this thread is all I get that's relevant.

---

### Post by dannyboy79 on 2014-05-03
i don't really care which menu i use but I can't get items to show up in it. for example Gparted, whether I edit the menu using menu editor or main menu gparted is there in the list BUT it just won't show up in my menu. This machine is an upgrade from 12.04 so I am assuming some config file is preventing it from displaying correctly. Can anyone help please?

UPDATE: i went and read that link above and it mentions that gparted and others were moved to the settings-manager which i think is stupid. So is there a way to manually create .desktop files for certain apps i want in the menu whether i use the old applications menu or the new whiskers menu?

---

### Post by mrsfixit on 2014-07-25
> **james-auble2 said:**
> I like Whisker Menu and have used it on other distros but have never had  editing issues with it like I've had so far on Xubuntu 14.04. I found  today that I couldn't add items to the System category with MenuLibre,  Alacarte, or by manually editing .desktop files. Became pretty  frustrated as it seems like this is a common task that should be pretty  simple and straight forward. Finally I found a post from somebody else  with the same issue (can't find the post anymore) that described a  simple fix for this. Open MenuLibre (by terminal if it's not in whisker,  or right click on the panel applet), find the item you'd like to have  show up under 'System', and remove the line that says Settings -  Settings under category attributes. This will unlock the item so you can  do as you please with it. A simple fix but I wouldn't have figured it  out without finding that post so if you're having the same problem I  hope that works!



I just did a fresh install of Xubuntu 14.04.1 on my laptop, and (after having to manually install both) gparted and gnome-disks shortcuts were buried in the settings. I like to have easy one-click access to these.

I despise MenuLibre. It's a continual headache. It has a horrible GUI. It is confusing and needlessly complicated, and I'm not exactly a newbie. Read some of the threads all over the net concerning MenuLibre, and some of the advice given. It's ridiculous.

Linux should be getting easier to use, one shouldn't have to be browsing forums for answers on how to do stuff that ought to be simple, and getting advice on how to edit system files and use the CLI to do something that used to be ONE click and DONE with alacarte!

Jeez sometimes I feel like I'm back in Windows 95 having to edit config.sys and autoexec.bat files to get stuff to work!

Anyway, I followed your instructions and was able to add both utilities to my menu. I was tearing my hair out trying to get it to work. I would **never** have figured that one out on my own. Thank you so much! You're a lifesaver!

---

