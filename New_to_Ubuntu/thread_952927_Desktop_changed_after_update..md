---
title: "Desktop changed after update."
date: 2008-10-19
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-10-19
Hello,

After getting 8.04 to load on my laptop a messege stating that two updates were available. So I connected to the internet via my router and an ethernet cable and elected to get the updates. After that, I noticed that the information bar that has Applications Places and System plus the date and other icons was now on the left hand side of my screen and had swapped places :confused:.

I would like to get it back the way it was befor the update. Any ideas as to how to go about this?

Thanks

---

### Post by drs305 on 2008-10-19
By information bar I am guessing you mean one of the panels. If so, right click, Properties, change the location in the Orientation setting. Or hover your mouse over an empty part of the panel for a couple of seconds and you may be able to just drag it where you want it.

**Addded**: I think I misunderstood. The bar didn't move, just the justification? Although inconvient if you have a lot of icons, you can right click on each item and slide it where you want. If it won't move or when it is in position, you can again right click and select 'lock' to keep it at that position. As you are sliding it, if it stops before you want it to the reason is the adjoining icon is probably locked. You will have to unlock that one to get be able to move another one past it.

Once you have the icons where you want, you can save the relative positions (sometimes they will move but still be in the same order) by running this command. You can change the filename to whatever you wish:
```

gconftool-2 --dump /apps/panel > ~/Desktop/panel_settings

```

To restore:
```

gconftool-2 --load ~/Desktop/panel_settings && killall gnome-panel

```

---

### Post by Uchiha_madara on 2008-10-19
Maybe that was the Beta version of Ubuntu 8.10

---

### Post by Uchiha_madara on 2008-10-19
> **nu2this2 said:**
> 
I would like to get it back the way it was befor the update. Any ideas as to how to go about this?
Thanks




you can't Rollback the data before Updating....
however , I need to ask you when did you made the Last Update
If you made it before these Days , I'm not sure if it was the Beta version of 8.10 or not.....

---

### Post by nu2this2 on 2008-10-19
Hi,

I just did the two updates this morning. 

I am speaking of the area of information that contains the sign out icon, the date,volume control,network connections, help icon, Firefox and evolution mail icons, all of that, which, until updating today, was at the very top of the Ubuntu desktop. If I were using windows, I believe it would be the "Task Bar" that is located at the bottom of the windows desktop screen. The position occupied currently by this Ubuntu information bar is vertical and on the left side of the desktop. I cannot move this bar or any of the icons by Rt. clicking and dragging. The new position is difficult to get used to because the writing is going vertical instead of horizontil.

I hope someone has experienced this befor and can help.

Thanks again.

---

### Post by tuxxy on 2008-10-19
I know it sounds simple but did you try left click dragging it to where you want the panel?

---

### Post by drs305 on 2008-10-19
> **nu2this2 said:**
> Hi,

I just did the two updates this morning. 

I am speaking of the area of information that contains the sign out icon, the date,volume control,network connections, help icon, Firefox and evolution mail icons, all of that, which, until updating today, was at the very top of the Ubuntu desktop. If I were using windows, I believe it would be the "Task Bar" that is located at the bottom of the windows desktop screen. The position occupied currently by this Ubuntu information bar is vertical and on the left side of the desktop. I cannot move this bar or any of the icons by Rt. clicking and dragging. The new position is difficult to get used to because the writing is going vertical instead of horizontil.

I hope someone has experienced this befor and can help.

Thanks again.

I guess we are back to what I thought was the problem originally, When you right click on the panel and select Properties, is there no Orientation section with Top, Left, Right, Bottom? If that doesn't work, normally click/hold and dragging works. 

If those fail, you should be able to use gconf-editor to place the panels with the following commands:
```

gconftool-2 --type string --set /apps/panel/toplevels/bottom_panel_screen0/orientation 'bottom'
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation 'top'

```

If these don't work, you can change the settings to top, bottom, left, right as you wish. You can also open gconf-editor and follow the path above to the section which contains these settings (apps, panel, toplevels).

---

### Post by nu2this2 on 2008-10-19
> **tuxxy said:**
> I know it sounds simple but did you try left click dragging it to where you want the panel?

Thanks,

Tried that---------------no luck. I can't imagine what happened. :confused::confused:

---

### Post by nu2this2 on 2008-10-19
Drs305,

When I rt. click the area I refer to. The options shown are; Help, Edit Menus, Remove from Panel and Lock to panel. The Move option is greyed out.

If I Rt. click the desktop the options are; Create Folder, Create Launcher, reate Document, Clean up by name, Change desktop Background. The Paste option is greyed out.

"Properties" never shows up as an option.

  This is only my second day using Ubuntu. I am assuming you are  referring to going into the terminal? If so, if this doesn't work, will I have made an unremovable error?

---

### Post by Shazaam on 2008-10-19
Right-click an empty space on the panel (usually in the middle unless the panel is full) and click "Properties". Orientation is the box you want.

---

### Post by drs305 on 2008-10-19
> **nu2this2 said:**
> Drs305,

When I rt. click the area I refer to. The options shown are; Help, Edit Menus, Remove from Panel and Lock to panel. The Move option is greyed out.

If I Rt. click the desktop the options are; Create Folder, Create Launcher, reate Document, Clean up by name, Change desktop Background. The Paste option is greyed out.

"Properties" never shows up as an option.

  This is only my second day using Ubuntu. I am assuming you are  referring to going into the terminal? If so, if this doesn't work, will I have made an unremovable error?

nu2this2,

No, it is not a irreversible. You would just have to change the string value (top, bottom, right, left) in the command to put it where you want. Chances are it is going to work or not - either way it won't mess anything up.

As Shazzam mentioned, you have to right click on a blank area of the task bar to get the options we are discussing. Right clicking on a symbol would produce the results you are experiencing. It is very possible you don't have any blank area to click on since it's been moved to the side (ask me how I know this!!). If that is the case, you will have to delete some of the icons (Remove from panel) until you get enough empty space to click on.

Stick to it, we'll get this sorted out!

---

### Post by robert shearer on 2008-10-19
> **nu2this2 said:**
> Drs305,

When I rt. click the area I refer to. The options shown are; Help, Edit Menus, Remove from Panel and Lock to panel. The Move option is greyed out.

If I Rt. click the desktop the options are; Create Folder, Create Launcher, reate Document, Clean up by name, Change desktop Background. The Paste option is greyed out.

"Properties" never shows up as an option.

  This is only my second day using Ubuntu. I am assuming you are  referring to going into the terminal? If so, if this doesn't work, will I have made an unremovable error?
edit   beaten to it!
you need to click on an unoccupied area of the panel to bring up the properties menu. Sounds like you are clicking on an icon or separator.
Try clicking at different points on the panel.

---

### Post by nu2this2 on 2008-10-19
> **Shazaam said:**
> Right-click an empty space on the panel (usually in the middle unless the panel is full) and click "Properties". Orientation is the box you want.

I'm sorry but I'm confused as to the word panel. Do you mean the area that I am trying to correct, or the desktop itself( the one that shows the Heron)?

---

### Post by robert shearer on 2008-10-19
> **nu2this2 said:**
> I'm sorry but I'm confused as to the word panel. Do you mean the area that I am trying to correct, or the desktop itself( the one that shows the Heron)?

The area that you are trying to correct. It is a 'Panel" 
Not the desktop with the Heron.

---

### Post by nu2this2 on 2008-10-19
> **robert shearer said:**
> The area that you are trying to correct. It is a 'Panel" 
Not the desktop with the Heron.

OK, We are on the same page. I've tried that but I don't get the option "properties". The panel is very full with little space between the icons or print and irrespective of where I click, the result is allways the same.

With all this clicking and such I now have a large "Default Printer" icon occupying my desktop.

Maybe what I should do is reinstall Ubuntu. If I do that, can I just reinstall over my current version?

---

### Post by nu2this2 on 2008-10-19
Going to have to sign off till tomorrow. Wifey is all P.O'd at me and want's me to start the BBQ and get dinner goin'

Till Later.

---

### Post by Shazaam on 2008-10-19
Save some for us!
As drs305 said you may need to remove some of the panel (taskbar) icons to free up the empty space. Also, since a lot of them are probably open windows right-click one and see if it says "Close" at the bottom.

---

### Post by nu2this2 on 2008-10-20
In retrospect, when I opened Firefox the first time I noticed that the webpages were too large for my screen. I then tried to adjust my screen resolution. When I did that, the screen display split into two sections. I tried to exit out but could not do so. I had to shut down and reboot. It was after the reboot that the panel position had changed. The Icons and print are now much larger and spaced together very closely. Perhaps this is why I cannot click and get the properties option. 

I have tried to increase my screen resolution through SYS-PREF-Screen Res, and only can go to 800 x 600. Is there any way to increase this resolution?

---

### Post by nu2this2 on 2008-10-24
Hi,

I reinstalled Hardy and the desktop issue resolved itself. Then I went on the internet with Firefox and the exact problem resurfaced!!

I believe it has to do with my screen resolution because all of the text and icons are very large in size. Somewhere along the way when I go online to browse, the resolution must change. When I was originally working with Hardy ( not online), the resolution never changed irrespective of how many times I shut down or restarted. 

Does anyone know why this happens??

Thanks for any suggestions.

---

