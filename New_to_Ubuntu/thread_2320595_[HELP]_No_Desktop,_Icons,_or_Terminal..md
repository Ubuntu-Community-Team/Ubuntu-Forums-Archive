---
title: "[HELP] No Desktop, Icons, or Terminal."
date: 2016-04-15
forum: New to Ubuntu
---

### Post by jordan63 on 2016-04-15
Please help. I log in and there is nothings here. I can't open terminal (ctrl+t). I really need documents inside so I would really rather not have to delete all my data in order to get my desktop back. 

Please someone one with knowledge help me step by step. I have read multiple forums and spent hours trying. To no avail.

---

### Post by jordan63 on 2016-04-15
I fixed it guys. Here's how


[LIST=1]
[*]Switch to a virtual terminal (Ctrl+Alt+F1), log in and run the following commands:
sudo apt-get install gnome-panel
sudo mv ~/.Xauthority ~/.Xauthority.backup

[*]Reboot and select gnome on login.

[*]Once logged in open a terminal (e. g. with Ctrl+T) and run:
sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity

[*]Log out and log in again using Unity this time and that fixed it for me.
[/LIST]

---

### Post by RobGoss on 2016-04-17
Glad to see you solved your problem and thank you for posting your solution, If you don't mind can you mark this thread as Solved just use the **Thread tool tab** from the drop down menu at the top of this post

---

