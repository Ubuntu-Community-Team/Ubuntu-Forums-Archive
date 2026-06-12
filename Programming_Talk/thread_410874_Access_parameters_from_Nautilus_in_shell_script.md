---
title: "Access parameters from Nautilus in shell script"
date: 2007-04-16
forum: Programming Talk
---

### Post by thelinuxguy on 2007-04-16
Referring to my post at [http://ubuntuforums.org/showpost.php?p=2457295&postcount=8](http://ubuntuforums.org/showpost.php?p=2457295&postcount=8), is there any way a shell script can access what Nautilus would pass to an application/extension registered to start on clicking a menu item in the context menu? This data doesn't seem to be accessible to the script via positional parameters. Any ideas anyone?

---

### Post by WakkiTabakki on 2007-04-16
Here are a few
NAUTILUS_SCRIPT_SELECTED_FILE_PATHS: newline-delimited paths for selected files (only if local)
NAUTILUS_SCRIPT_SELECTED_URIS: newline-delimited URIs for selected files
NAUTILUS_SCRIPT_CURRENT_URI: URI for current location
NAUTILUS_SCRIPT_WINDOW_GEOMETRY: position and size of current window 

Edit! 
Found the url I was looking for [https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)

Good luck
/N

---

### Post by thelinuxguy on 2007-04-16
Great!!! Looks exactly like what I was looking for. Ill go through the page.
Thanks a ton.

---

