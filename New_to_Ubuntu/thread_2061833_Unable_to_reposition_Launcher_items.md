---
title: "Unable to reposition Launcher items"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-09-23
This is a minor problem, and possibly it will turn out it is me forgetting how it works rather than anything being broken. 

[LIST]
[*]If it is something broken or interfering with the launcher then I have no idea of the likely causes.
[*]Or have I just exceeded the design limits of the launcher ?
[/LIST]
I am unable to drag and reposition items in the launcher. I am fairly certain I used to be able to do this without problem. The launcher is on the LHS presumably default location and icon size. It is now larger than the space permits and so scrolls, there are I believe 19 items including the Rubbish bin.

I have for instance a launcher icon for a version of the Firefox browser. I have unlocked and removed this and then put it back but  it is remaining in the area that I need to scroll to access. I am trying to put it  higher up so it is visible and clickable all the time.

I also have shortcuts/launchers on the desktop.

Update.
One thing I note is that in Unity to move the launcher icons it is required to press and hold the left click.
I am not sure what the sensitivity or whatever setting is that affects that. But maybe I changed that inadvertently.
The launcher continues to work, but it is apparently requiring a longer delay.

I am using 64bit Ubuntu 12.04 LTS on an AMD laptop. 
Not sure what other information may help. 

Hopefully someone will be able to guess what I am doing wrong, thanks in advance.

---

### Post by deadflowr on 2012-09-23
Scrolling?
When you mean scrolling? Do you mean the icons are flat and scroll under the top and bottom icons?
Or do they collapse at the bottom?

---

### Post by daslinkard on 2012-09-23
> **aka-John99 said:**
> This is a minor problem, and possibly it will turn out it is me forgetting how it works rather than anything being broken. 

[LIST]
[*]If it is something broken or interfering with the launcher then I have no idea of the likely causes.
[*]Or have I just exceeded the design limits of the launcher ?
[/LIST]
I am unable to drag and reposition items in the launcher. I am fairly certain I used to be able to do this without problem. The launcher is on the LHS presumably default location and icon size. It is now larger than the space permits and so scrolls, there are I believe 19 items including the Rubbish bin.

I have for instance a launcher icon for a version of the Firefox browser. I have unlocked and removed this and then put it back but  it is remaining in the area that I need to scroll to access. I am trying to put it  higher up so it is visible and clickable all the time.

I also have shortcuts/launchers on the desktop.

I am using 64bit Ubuntu 12.04 LTS on an AMD laptop. 
Not sure what other information may help. 

Hopefully someone will be able to guess what I am doing wrong, thanks in advance.

If you are wanting to just reset the launcher icons you should be able to use the following command:

```
unity --reset-icons
```
If you are wanting to do a complete reset on Unity you can do the following:

```
unity --reset
```

---

### Post by aka-John99 on 2012-09-23
> **deadflowr said:**
> Scrolling?
When you mean scrolling? Do you mean the icons are flat and scroll under the top and bottom icons?
Or do they collapse at the bottom?

I am not entirely certain I understand the question.

The Rubbish bin is fixed. If I move my mouse pointer to the top or bottom of the launcher bar and there are hidden launcher icons then they will scroll into view.

---

### Post by deadflowr on 2012-09-23
Sounds like your running the 2d version. As that is the behavior of it. Unity-3d collapses icons as more and more are added.
First off, I'd follow the advice in post#3.
Then if you problems are still occurring, log out, and in the login screen, in the box with your name and password at the top right is a cog, or something. Click on the cog and select Ubuntu, then log in.
I do know the behavior of moving the icons in 2d differs from 3d.
When selecting an icon to move, press and hold the left-click, hold down on the icon and try wiggling it.
To find out if your system can run unity-3d run:

```
/usr/lib/nux/unity_support_test -p
```

If any of the responses is no then you can only run in 2d.
Which would make logging out to change the cog selection moot, as the default of Ubuntu will login as Ubuntu2d(unity-2d).

I don't know if this will help or not.
Good luck.

---

### Post by aka-John99 on 2012-09-23
Thanks both of you for the rapid respnses.

> If you are wanting to just reset the launcher icons you should be able to use the following command:

```
unity --reset-icons
```If you are wanting to do a complete reset on Unity you can do the following: ... Ok thanks. I will have to study this more closely but it seems to have worked.

The icons now will move as expeced and can be dragged on and off of the launcher.

Rather oddly I now seem to have four identical or similar workspaces. The launcher bar on the other workspaces may be as before. The launcher bar aside in the current workspace seems t have the default set of ten launcher Icons plus the dash at the top and the Rubbish bin at the bottom. 

I will look at how it behaves over the next few days before asking further questions or marking the thread as solved.

I did notice the reset command is documented at [http://manpages.ubuntu.com/manpages/precise/en/man1/unity.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/unity.1.html) but I have not yet discovered where 
```
unity --reset-icons
```  is documented.

---

### Post by daslinkard on 2012-09-23
Glad we could get this solved for you....please mark as solved!

---

### Post by aka-John99 on 2012-09-25
Has anyone got a link to the documentation for the documentation for the reset icons command ?

I have now added back icons to the launcher and it continues to work, thanks everyone for the quick responses. I will now mark this as solved.

---

### Post by aka-John99 on 2012-09-25
Someone asked above whether the icons were flat or collapsed. I have since seen them collapse as in rotating into a stack, although they are flat at present. I am guessing that is probably dependent on whether I have 2D or 3D selected. Not sure if that is the case, also not sure if the setting is global, or can be chosen on a per account basis.

---

