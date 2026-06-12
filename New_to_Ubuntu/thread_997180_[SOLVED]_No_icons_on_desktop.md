---
title: "[SOLVED] No icons on desktop"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by bmeacham on 2008-11-29
I just installed Ubuntu 8.10 and had no icons on my desktop.  Various documentations suggested that I should see Computer, My Home and Trash.  I looked through the forums here and found enough clues to help me solve the problem, as follows:

1) Alt+F2

2) type:
   gconf-editor

3) Click Run

   Configuration Editor appears

4) Open apps / nautilus / desktop

5) Make sure the following are checked:
   * computer_icon_visible
   * home_icon_visible
   * network_icon_visible
   * trash_icon_visible
   * volumes_visible

6) Close Configuration Editor

7) Log off and log back on again

---

