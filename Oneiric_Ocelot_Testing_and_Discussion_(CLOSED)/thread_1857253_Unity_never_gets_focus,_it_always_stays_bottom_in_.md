---
title: "Unity never gets focus, it always stays bottom in the windows stack"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Tasu on 2011-10-10
I looked if someone other have had this issue in Oneiric, but I can't find this exact behaviour, a lot of people is complaining about windows not getting focused the right way, the problem I face is kinda different: my unity launcher stays always on the bottom level of the windows stack.

Ubuntu Oneiric amd64
nvidia proprietary drivers

When I login, I can use unity to start a software, if I keep the software un-maximized, when I place the mouse on the left side, unity appears and stays on top of the other windows, as soon as I maximise a window, I can no more access unity using the mouse, if I use the Super key on the keyboard, I can see the current window's toolbar on the upper panel (the one with the File, Edit, etc.. menus), replaced by unity's one (I can say this because I see the close, minimize and miximize icons change from the application's one to the semi transparent ones typical of unity, now it starts a stranger thing, it looks like unity is in focus (I cannot click on the visible window's buttons), but is invisible due to it's stack level being the bottom one... I can say it's unity in focus because if I type (blindly) the name of an application I know (say Terminal) and I tap tewo times the down arrow key on the keyboard, it launches terminal...

I try to file a bug report on this, however, if someone has a quck fix, I'm glad to test it, using the desktop this way is really annoying... (I'm as a workaround, keeping a terminal opened in another desktop and run applications from there...

Bye!

---

### Post by effenberg0x0 on 2011-10-10
Yes, I will +1 on this bug. And I have a workaround.

On **CompizConfig-Settings-Manager** (ccsm),  go to the **Window Rules Plugin**.

At the row labeled "**Above**", add: "**(title=launcher | name=Dash | title=Dash)**" (use no quotes)

Then mark the checkbox on the left (**Enable Window Rules**). At this point, unfortunately, ccsm might crash your session, as it sometimes is a little too unstable. Either way, restart your session, so the changes might take effect. You can open a terminal window and run "**sudo service lightdm restart**"

Let me know if it works for you. Works 100% here.

Regards,
Effenberg

**EDIT:** Sorry, code had a typo.

---

