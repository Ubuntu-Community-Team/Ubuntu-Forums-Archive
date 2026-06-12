---
title: "Ubuntu 12.04 LTS Gnome Class &quot;Places&quot;"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by mdavis1231 on 2013-06-27
I's there any way for me to switch back to the old style showing under "Places"?  Now, when I click on "Places", this is what I see:

[IMG]http://i1223.photobucket.com/albums/dd512/mdavis1231/Places_zps2d810bb7.png~original[/IMG]

Thanks!

---

### Post by snowpine on 2013-06-27
Hi, which part of that menu is confusing, specifically?

---

### Post by mdavis1231 on 2013-06-29
> **snowpine said:**
> Hi, which part of that menu is confusing, specifically?

Oh, there's absolutely nothing about this menu that's "confusing" at all.  My question is, and it's just my preference, how do I get it to look like the old "Places" menu again, like this example from my laptop?

[IMG]http://i1223.photobucket.com/albums/dd512/mdavis1231/TraditionalPlaces_zpsc8c5e772.png~original[/IMG]

---

### Post by 3rdalbum on 2013-06-29
When you reach a certain number of bookmarks, they stop appearing directly in the menu and appear under a Bookmarks submenu.

I don't think you can change this attribute, but you can look in gconf-editor and dconf-editor and see if there's any item there that changes the number of bookmarks you need in order for it to appear in the submenu.

---

### Post by DaveMcC on 2013-06-29
I also, would like to do away with the task bar down the side, and revert back to "the look of" version 10.10, I think that is what (mdavis1231) wants

Dave

---

### Post by mdavis1231 on 2013-06-29
> **3rdalbum said:**
> When you reach a certain number of bookmarks, they stop appearing directly in the menu and appear under a Bookmarks submenu.

I don't think you can change this attribute, but you can look in gconf-editor and dconf-editor and see if there's any item there that changes the number of bookmarks you need in order for it to appear in the submenu.

You were exactly right.  I removed the Google Drive "bookmark", and now it looks the same as my laptop again.  Apparently, there's a limit of 8 or 9 folders that you can have "bookmarked", then, like you said above, it compacts and they appear under a Bookmarks submenu.  Thanks!!!

---

