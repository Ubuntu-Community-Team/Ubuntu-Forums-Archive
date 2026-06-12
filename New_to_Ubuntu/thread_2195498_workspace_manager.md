---
title: "workspace manager"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by dwjeanes2 on 2013-12-24
I recently upgraded to ubuntu 13.10 from 12.xx (don't recall the specific revision) and I had a workspace manager that allowed me to choose a number of workspaces among which to place my apps. I cannot remember where I found this facility, or even if it was an add-on. Evidently. I just stumbled upon it and used it, never really paid that much attention to it other than to just use it.

Here is my problem: I need it again and I have no idea where I found it. Can anyone point me to a Ubuntu workspace manager? I would really prefer it to come from the Ubuntu approved list, or better yet, be a part of the base system, or an addon. I seriously don't have a clue where I found it.

Any help would be greatly appreciated. Ubuntu rocks!

Thanks in advance

---

### Post by deadflowr on 2013-12-24
In 12.04 we had an app called MyUnity, but it is broke for all versions beyond 12.04.
In 13.10 we have unity-tweak-tool. It's in the software center.

Additionally, if you've installed ccsm, you can change the workspaces in the general options > desktop size.

---

### Post by dwjeanes2 on 2013-12-24
Thanks! perfect solution. Please mark this as answered and completed! (And in record time, I might add. Have you ever tried to get an answer from Microsoft support? How long did THAT take?)

I know you guys do this out of love for the community, and I just want to be sure and thank all who contribute to making Ubuntu the best user supported community help group I have ever seen.  Keep up the good work!

---

### Post by steeldriver on 2013-12-24
if you don't want to install *any *additional software, you can modify the setting directly in the dconf database using the gsettings command-line tool e.g.

```

gsettings get org.gnome.desktop.wm.preferences num-workspaces

gsettings set org.gnome.desktop.wm.preferences num-workspaces 6
 
gsettings reset org.gnome.desktop.wm.preferences num-workspaces

```

---

### Post by Iowan on 2013-12-24
> **dwjeanes2 said:**
>  Please mark this as answered and completed! 
You can do that yourself. :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by deadflowr on 2013-12-24
> [COLOR=#000000]I know you guys do this out of love for the community, and I just want to be sure and thank all who contribute to making Ubuntu the best user supported community help group I have ever seen. Keep up the good work![/COLOR]

Thank you's are always nice.
Thank you for the thank you!:)

---

### Post by dwjeanes2 on 2013-12-24
> **Iowan said:**
> You can do that yourself. :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Old dog just learned new trick.

Many thanks.

---

