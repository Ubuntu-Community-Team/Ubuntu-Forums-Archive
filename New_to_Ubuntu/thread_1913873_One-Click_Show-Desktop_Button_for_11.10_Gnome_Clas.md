---
title: "One-Click Show-Desktop Button for 11.10 Gnome Classic"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-23
I recently failed to upgrade from 11.04 to 11.10 & made a clean install of 11.10, using Unity 2D as default.
I was surprised not to find a "Show Desktop" button & amazed when it seemed there was none available.

After a lot of digging, I found this item on the useful site Webupd8:
[http://www.webupd8.org/2011/10/show-desktop-indicator-for-ubuntu-quick.html](http://www.webupd8.org/2011/10/show-desktop-indicator-for-ubuntu-quick.html)

Following instructions there, I was able to install a Button on the top panel (my preference over Unity Launcher).
This did what I wanted, but in 2 clicks rather than one.
One click to bring up & "Toggle Desk" icon & another to do the job - I wonder why?

For many reasons discussed elsewhere, I gave up on Unity & reverted to Gnome Classic.

Obviously (?) I expected to find the good old "Show Desktop" button at the left of the bottom panel, as always.
Image my surprise, to coin a phrase, when it wasn't there!
Imagine my disbelief when it was not even available (I hope somebody can correct me there).

So I was left with the W8 2-click solution on the top panel.

With a bit more digging on W8 & a bit of trial & error, I now have a 1-click Show Desktop button where I want it - left hand corner of bottom panel.

I will explain how in a separate post, uncluttered by this history.

---

### Post by 2CV67 on 2012-01-23
**HOW TO: Put a One-Click "Show Desktop" Button at Left Corner of Bottom Panel.**

99% of this is due to W8 website - many thanks!
[http://www.webupd8.org/2009/10/show-desktop-applet-for-docky-gnome-do.html](http://www.webupd8.org/2009/10/show-desktop-applet-for-docky-gnome-do.html)

Using GUI methods where possible instead of CLI on W8:
1. In Synapt > Install "wmctrl".
2. If you don't already have one, create folder "Scripts" in your home folder.
3. Create empty document in "Scripts" & name it "show_desktop.sh".
4. Copy/Paste inside "show_desktop.sh":
> #!/bin/sh
if wmctrl -m | grep "mode: ON"; then
exec wmctrl -k off
else
exec wmctrl -k on
fi
5. Save "show_desktop.sh".
6. Right-click "show_desktop.sh" > Properties > Permissions > Check "Allow executing file as program." & Close.
7. Alt+Right-click top panel & select "Add to panel".
8. Select "Custom Application Launcher".
9. Name it "Show Desktop" or whatever - this will appear when hovering over icon.
10. Next to "Command" click "Browse..." & navigate to "show_desktop.sh" & double click it to apply & close Launcher Properties window.
You should now have a new default icon (Jack in the Box) on top panel.
11. Test new icon to see if it works OK to alternately show desktop & re-show previous windows.
12. If you prefer your button on bottom panel > Alt+Right-click on icon & select "move".
13. Drag & drop icon to bottom panel (my preference - left corner, where it always was).
14. If you find the new icon shifting from bottom corner when opening new windows: Alt+Right-click on icon whilst one or more windows are open > select "move" > Drag back to left corner.
15. Assuming you want a relevant icon instead of Jack in the Box: Browse available icons in Nautilus. This is tedious. Go to /usr/share/icons where you can find thousands & see them only by opening each folder. For instance, I chose "/usr/share/icons/oxygen/48x48/preferences-desktop-display...". Leave Nautilus open there or carefully note your choice.
16. Right-click on your J-in-Box icon on bottom panel or wherever > Select "Properties".
17. Click on J-in-B icon in Launcher properties.
18. Navigate to icon chosen in (15) & double-click to install it.
19. Finished!

Thanks again to W8 for nearly all the above.

If there is a simpler GUI method, I would be pleased to see it.

This button should be there as default.

---

### Post by Roliat on 2012-05-02
Good work, thanks!

> **2CV67 said:**
> For instance, I chose "/usr/share/icons/oxygen/48x48/preferences-desktop-display...".

/usr/share/icons/oxygen/48x48/actions/dashboard-show.png seems also pretty suitable for that matter (please mind that you'll have to apt-get install oxygen-icon-theme for that, obviously).

---

### Post by ikem.krueger on 2012-08-12
I skipped the script part and just created a desktop file called "show-desktop.desktop":

```

[Desktop Entry]
Encoding=UTF-8
Name=Show Desktop
Exec=wmctrl -k on
Comment=Minimize all windows
Icon=user-desktop
Type=Application

```

---

