---
title: "How can I view the custom menu in Bluefish editor?"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by omid020 on 2012-11-25
Hi,

I have installed Bluefish 2.2.3.
In some blogs I have seen an screenshot of this editor with a custom menu:

[IMG]http://s10.postimage.org/r1uhs90d5/image.png[/IMG]

I have seen version 2.2.0 introduction movie too and again I have seen the
custom menu in it.

How can I view this menu?

---

### Post by linux4me on 2012-11-25
It's called the Snippets Menu. What you need to do is to click View on the main menu in Bluefish and make sure Snippets Menu is checked.

If Snippets Menu is checked, and is still not showing up, you may be running into an issue with the Unity menu overlays. I had this problem with Bluefish in Ubuntu 12.04, but not in 12.10. Apparently, the Unity menu overlays only display the first menu associated with an application. The developers of Bluefish elected to use two menus (the main menu and the Snippets menu) so the second menu (Snippets) doesn't show up when menu overlays are active for Bluefish.

If you have the Snippets Menu checked and it's still not showing up, you can disable menu overlays globally, quit using Unity, or use this workaround:

[LIST=1]
[*]If it's already added to the launcher bar, unpin Bluefish from the launcher bar.
[*]Copy the Bluefish .desktop file to your home directory by running the following command in Terminal: cp /usr/share/applications/bluefish.desktop ~/.local/share/applications
[*]Open Nautilus to your home directory, push Ctrl+H to show hidden files, and then browse to .local/share/applications. Right-click on the bluefish.desktop file and choose Properties.
[*]Replace the text in the Command box with the following: env UBUNTU_MENUPROXY= bluefish
[*]Run the following command in Terminal to make the file executable: chmod +x ~/.local/share/applications/bluefish.desktop
[*]Double-click the icon in Nautilus--which will now be named "Bluefish Editor"--to open it, and pin it to the launcher bar.
[/LIST]
From now on when you click the Bluefish icon in the launcher bar, the menu overlays will be disabled for Bluefish and the Snippets menu will work.

---

### Post by omid020 on 2012-11-26
Many thanks linux4me!
Works like a charm :)

---

