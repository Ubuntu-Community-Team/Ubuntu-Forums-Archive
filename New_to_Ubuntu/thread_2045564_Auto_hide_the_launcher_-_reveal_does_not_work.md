---
title: "Auto hide the launcher - reveal does not work"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by tc101 on 2012-08-21
In 12.04, reveal does  not work when I auto hide the launcher.  I have tried adjuting sensitivity.  Nothing works.

---

### Post by Frogs Hair on 2012-08-21
The reveal is set to activate by moving the cursor directly to the left side by default due to the proximity of the title bar close button. 

The launcher  can be set to the top left also. The luncher won't appear if the the cursor is not moved to the location specified by the setting. Try logging out and back in or restarting after making the setting if the launcher is not responding.

---

### Post by era86 on 2012-08-21
I have also found that you need to move the cursor far to the left to get the launcher to show. Meaning, don't stop moving your cursor to the left once you hit the edge, simply keep going as if it would never stop. Haha, that seems to get the job done.

---

### Post by Shenarah on 2012-10-05
The reveal was working fine until an update this morning. Now it only works if I press the super key. Mouse movements wont reveal it.

---

### Post by NikTh on 2012-10-05
Known bug with Nvidia driver 304.51

[https://bugs.launchpad.net/unity/+bug/1057000](https://bugs.launchpad.net/unity/+bug/1057000)

Thanks

---

### Post by Shenarah on 2012-10-05
So it was caused by this morning's update? That sucks!

---

### Post by chrnoble on 2012-10-07
Having read through every comment on the bug report, I was wondering if someone might do me two favors.

1) Post the downgrade instruction as if you were telling an extremely stupid person how to do it. Because, in my case, you would be.

2) Tell me, which Nvidia driver is used in 12.10? I still have nightmares about getting NVIDIA to work in 12.04. If I can avoid the issue altogether, I'd be a very happy man.

Meanwhile, I'll flip between my Gnome shell and Cinnamon desktops.

---

### Post by deadflowr on 2012-10-07
> **chrnoble said:**
> Having read through every comment on the bug report, I was wondering if someone might do me two favors.

1) Post the downgrade instruction as if you were telling an extremely stupid person how to do it. Because, in my case, you would be.

2) Tell me, which Nvidia driver is used in 12.10? I still have nightmares about getting NVIDIA to work in 12.04. If I can avoid the issue altogether, I'd be a very happy man.

Meanwhile, I'll flip between my Gnome shell and Cinnamon desktops.

Follow the instructions in post #3 by timothymowens, in the bug report Nikth posted. It's probably the best point for point explaination you'll get.

---

### Post by chrnoble on 2012-10-07
> **deadflowr said:**
> Follow the instructions in post #3 by timothymowens, in the bug report Nikth posted. It's probably the best point for point explaination you'll get.

Okay. But I'm still curious if 12.10 has NVIDIA 304.51. If not, I may upgrade. Anyone know?

---

### Post by Pilot6 on 2012-10-07
12.10 does not have 304.51, since it has this bug. It has 304.43.
I think, this bug will be fixed it &#1090;&#1091;&#1095;&#1077; NVIDIA blob.

---

### Post by vaul on 2012-10-20
You are wrong. 12.10 does have 304.51 in its default shipping and is affected by this bug, judging by my desktop. I did not make any modifications to the driver installation since the upgrade.

---

