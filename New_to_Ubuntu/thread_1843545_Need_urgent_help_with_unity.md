---
title: "Need urgent help with unity"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2011-09-13
I installed some software for advanced compiz settings. Tried to changes some settings to see what happens if i change them and now unity application launch bar upper panel everything has vanished. started. no window has minimize, maximize, restore buttons. Infact no title bar. How can I restore unity?

---

### Post by howefield on 2011-09-13
Try

```
unity --reset
```

see man unity for more information.

---

### Post by oscarivera9 on 2011-09-13
For future reference, I like to get in the habit of making backups once a week.  If I do something that completely messes up my system, if I have a backup I can restore my system to an earlier time.  I know this doesn't really help you now but just something to consider for the unpredictable future.  You can download some great backup tools straight from the Ubuntu Software Center, like Deja Dup for example.

---

### Post by dfarrell07 on 2011-09-14
Restarting would likely also work - that is a great first step in solving any issue like this.

---

### Post by sujitrjadhav on 2011-09-14
[SIZE=3]Thanks very much for suggestions. It was too late night when I had posted this message. So after posting problem here I tried to solve it for sometime and then went to bed. I had to get it running before I reach office. So I took backup and reinstalled ubuntu in the morning as I could not wait till I get proper solution. Anyway thanks very much for help. But I would like to share what had happened.

I had installed compizconfig-settings-manager. In the "Desktop" sub menu of the compizconfig-settings-manager I check marked "Desktop Cube" and "Desktop Rotate" option. I got some on screen message that prompted me to either cancel enabling  "Desktop Cube" or disable "Desktop Wall"  I selected disable  "Desktop Wall" which again prompted me to either enable "Desktop Wall" or disable OpenGL. I selected to disable OpenGL which again brought something else on screen prompting me to either enable OpenGL or disable something else. I blindly clicked on some enable disable prompts but appearing of new prompts continued. So I closed a prompt (by clicking X) without clicking enable or disable button. And checked if something in unity had at all changed.

I found that nothing had changed so I though may be logging off and then again logging in would make effects appear. And so I re-logged in. And found that only files on desktop were accessible. Application Launcher and upper panel had disappeared. Alt+Tab, windows key or no keyboard shortcut was working. I created a shortcut to terminal. And started firefox from there. Posted problem here. For sometime I tried to solve problem by purging unity/compiz and re-installing them. Nothing worked. As it was  late night I switched off laptop and went to bed. In the morning  reinstalled ubuntu.

[/SIZE]

---

### Post by grahammechanical on 2011-09-14
There is a lesson here that some are learning the hard way (like myself). Some of the enhanced effects available through Compiz Configure Settings Manager clash with the way Unity works.

The answer I found was to reboot into Classical Ubuntu and remove the changes that I made and then reboot back into Ubuntu (Unity3D).

I found that I can have wobbly windows in Classical Ubuntu but not in Unity.

Regards.

---

