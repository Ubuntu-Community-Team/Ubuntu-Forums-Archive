---
title: "HOW TO: Add &quot;Enqueue/Play in XMMS&quot; to your right click menu in XFCE"
date: 2007-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by digitalsonata on 2007-08-15
This is a How-To for people using XFCE and Thunar (the default file browser for XFCE) who want to add the "Enqueue in Winamp(or XMMS in this case for Linux)" to your right click menu in Thunar.

1. Open a window in Thunar, it doesn't matter where.

2. In the Thunar window click Edit -> Configure Custom Actions
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40769&stc=1&d=1187232139[/IMG]

3. A window will pop up like this.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40770&stc=1&d=1187232139[/IMG]

4. Click the plus button and a new window will pop up.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40771&stc=1&d=1187232139[/IMG]

5. Enter the values in the previous screenshot on the first tab.

6. Click the "Appearance Conditions" tab,

7. Check the options seen in the screenshot below.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40772&stc=1&d=1187232139[/IMG]

8. Close the windows and your done. :P

You can also add the option to play files in XMMS by using the command "xmms -p %D" in place of "xmms -e %D"

Not sure who this will be useful to but I like the options :P

---

### Post by frodon on 2007-08-16
For those who use gnome and nautilus and wish to do the same thing you can use "nautilus-actions" which is in the repositories and do the same thing than the thunar custom action window :
[http://www.grumz.net/?q=taxonomy/term/5/9&PHPSESSID=7ff824d169c734e0e9aa9777027f4b80](http://www.grumz.net/?q=taxonomy/term/5/9&PHPSESSID=7ff824d169c734e0e9aa9777027f4b80)

---

