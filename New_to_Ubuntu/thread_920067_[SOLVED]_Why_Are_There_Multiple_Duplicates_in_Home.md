---
title: "[SOLVED] Why Are There Multiple Duplicates in Home/~/.local/share/applications/?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-14
Is it normal to have multiple duplicate desktop configuration files in Home/~/.local/share/applications/? What purpose do the duplicates serve, and why do some programs contain 5 duplicates, while others have only the original? Thanks.

---

### Post by bmac on 2008-09-14
Someone may correct me, but I believe the duplicates are based on your menu. The duplicated app. is listed in multiple categories in you menu structure. 

If you right click on you Application Menu and select "Edit Meuns" you will probably find the duplicates listed under multiple categories (Accessories,Programming, Other, etc.). By removing them from multiple categories it will remove the duplicates from your "Home/~/.local/share/applications/?" 

When assigned to that category, it simply get placed it in that folder.

I could be wrong but believe that is exactly why it duplicates - stores in that folder each time the app is selected in a category....

Hope this helps.....

---

### Post by mc4man on 2008-09-14
> I believe the duplicates are based on your menu yes and no, some entries are from new menu itens, some become new menu items, others have nothing to do with the menu.

They are created in various ways, usually from going 'open with other application' -> use custom command. Also when you set a file association you can get an entry there.
Setting an app as a default choice will also add an entry there, while creating an entry there is the first step to adding an app as a default choice.
You can safely delete them though I wouldn't remove the ones that start with an uppercase letter and have normal app icon unless they are duplicates.

You can only open them for viewing and or editing with a text editor, but by right clicking -> properties -> launcher you can tell if they are duplicate entries if they have same launch command.

See screen
some have been added by the open with other ... custom... or by setting file associations - they have blue diamond shape (i've renamed some)

Others ( with normal icons) were added by enabling menu items, or from just plain 'open with'

Others were created intentionally

If your interested in "offshoots' of that folder or custom launch commands or custom file associations. Ill post some links.

Suffice to say if your r.clicking on something and see an app listed multiple times you can delete the duplicates in this folder

Edit: it's kinda hard to explain everything about this folder and what's in it. Ithink this thread address's what you were talking about (vs. default players ect.)

[http://ubuntuforums.org/showthread.php?p=5741897#post5741897](http://ubuntuforums.org/showthread.php?p=5741897#post5741897)

---

### Post by bobsmith2 on 2008-09-15
Thank you mc4man and bmac.

---

