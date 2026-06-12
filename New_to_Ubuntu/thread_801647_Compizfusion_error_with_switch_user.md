---
title: "Compizfusion error with switch user"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by noorez on 2008-05-20
Compiz-fusion doesn't seem to get along with the switch user tool. Here is what happens.

1) I login. compiz fusion is enabled by default..
2) I use the switch user tool
3) I'm taken to the login screen and login to the other user
4) The other user logs out
5) The screen then goes white and I need to use Ctrl-Alt-BkSp to get out of it.

Anyone know what is happening?

---

### Post by vrangforestillinger on 2008-05-23
Yup. You are using NVIDIA-drivers, am I right? This is the case for me as well: Whenever my screen is in a locked state, where I should be prompted for my password to unlock the screen, It is instead a white-screen-of-death.

The easy solution is to disable compiz. But you can learn to get around it: The screen is white, but the mouse cursor will usually be visible. If you move the cursor somewhere near the middle, it changes to a text-cursor. This is you password input! Type the password of the user which you expect to be taken to when you logged out the other user. You should now be taken to your desktop, if it works like here.

Launchpad entry here for more techy stuff: [Bug #160264]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264"). Jugding by the comments, a fix is not far away from us end-users.

---

### Post by FuturePilot on 2008-05-23
Yes, the white screen issue is a Nvidia driver bug. But I've found that there is no need to Ctrl+Alt+Backspace. Just blindly enter your password and hit Enter. :)

---

