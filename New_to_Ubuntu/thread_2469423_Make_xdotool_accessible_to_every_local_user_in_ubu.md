---
title: "Make xdotool accessible to every local user in ubuntu"
date: 2021-11-29
forum: New to Ubuntu
---

### Post by kilbha on 2021-11-29
Hi community,

                    I am having a problem of accessing xdotool when it run as service. I created a service where I used xdotool to capture some activity. xdotool is used to access active window name. I tried running as a service but error saying current window is null. Whoever the logged in user is there, I have to capture logged in user activity.  I am able to capture activity when I run it manually through terminal but when I run as service( under control of local user ) not able to capture activity. I have tried 2 methods to capture activity of logged in user. 

Method 1 -- Created service in ubuntu. Service is running here but not able to capture activity. Error saying current window is null. Not able to capture activity when logged in as user. 

Method 2 -- Created per user service. Not able to run service by using this method. 

I was stuck at this point. I tried different methods to resolve the problem. Please suggest me in this regard to capture activity of every single user.

**How can I make xdotool (Accessing current window name) available for every single user to capture current logged in user activity?**

Thanks in advance


[B]Possible errors
[/B]
Current window is null. 



**useful links**

Creating service for ubuntu

[https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6](https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6)


Creating service per user

[https://wiki.archlinux.org/title/Systemd/User#How_it_works](https://wiki.archlinux.org/title/Systemd/User#How_it_works)


xdotool

[https://github.com/jordansissel/xdotool#:~:text=xdotool%20lets%20you%20simulate%20keyboard,extension%20and%20other%20Xlib%20functions.&text=If%20your%20window%20manager%20supports,change%20the%20number%20of%20desktops](https://github.com/jordansissel/xdotool#:~:text=xdotool%20lets%20you%20simulate%20keyboard,extension%20and%20other%20Xlib%20functions.&text=If%20your%20window%20manager%20supports,change%20the%20number%20of%20desktops).

---

### Post by TheFu on 2021-11-29
BTW, xdotool only works with X11, not Wayland.

---

### Post by kilbha on 2021-11-30
Thanks TheFu. I will test and come back to you.

---

### Post by kilbha on 2021-12-01
> **TheFu said:**
> BTW, xdotool only works with X11, not Wayland.

Thanks for the answer. I am not looking for any tool to achieve this. I need like code ( preferably bash script code ) to solve this issue.

---

### Post by TheFu on 2021-12-01
> **kilbha said:**
> Thanks for the answer. I am not looking for any tool to achieve this. I need like code ( preferably bash script code ) to solve this issue.

Perhaps understanding how X11 works would be helpful? Programs run _under_ X11, so if they are started outside that session, there shouldn't be any access allowed. X11 doesn't have much security, but what it does have is useful to prevent people over the network from having access to information they shouldn't be able to access.  X11 is udp, so there isn't any real security other than the built-in session security.  Over the many decades, new security measures have been added to X11. When I was coding X11 apps, it was only the DISPLAY that controlled access with an xhost + {remote-client-IP/name}.  I'm not sure when, but that changed.  I don't know much about the new stuff, so you'll have to figure that out on your own.

Now, if you want to capture a screen, look at SimpleScreenRecorder or ffmpeg [https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop) or any of the other X11-capable screen capture tools.  Those 2 are the lightest and easiest.  If you need more, OBS is there, but it is heavy and for production video.
If you want to input commands to X11 programs, there are a few tools. **cnee** is what I've been using when xdotool doesn't work, but there are lots of better options if you have $$$$ for a proper, commercial, testing tool.

I have no idea how to have a single program be able to get passed X-security for multiple users.  For one user, you can try to set the DISPLAY (correctly), but that will only work if an X/session exists and doesn't violate X/security.  The X/Client is the application and sends commands to the X/Server for display and interaction.  That client-server connection is where most programs inject/break the security to accomplish non-standard things.  I'm loath to share this, but check out **xhost** which can be used to break X11 security.  The X/session on the client will need to allow it. It is a really bad idea, but some places use it, opening up every machine to attacks.

If you use Wayland, I have ZERO idea how to accomplish this. I think the only working screen capture things are from the Gnome project.  Wayland and Gnome seem to be partners in this crime.  OTOH, Wayland is local-only, non-networked, so the main goal for it is simplicity and performance.

---

### Post by kilbha on 2021-12-03
Thanks for the reply. I will you give you an update on this.

---

### Post by kilbha on 2021-12-07
> **TheFu said:**
> Perhaps understanding how X11 works would be helpful? Programs run _under_ X11, so if they are started outside that session, there shouldn't be any access allowed. X11 doesn't have much security, but what it does have is useful to prevent people over the network from having access to information they shouldn't be able to access.  X11 is udp, so there isn't any real security other than the built-in session security.  Over the many decades, new security measures have been added to X11. When I was coding X11 apps, it was only the DISPLAY that controlled access with an xhost + {remote-client-IP/name}.  I'm not sure when, but that changed.  I don't know much about the new stuff, so you'll have to figure that out on your own.

Now, if you want to capture a screen, look at SimpleScreenRecorder or ffmpeg [https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop) or any of the other X11-capable screen capture tools.  Those 2 are the lightest and easiest.  If you need more, OBS is there, but it is heavy and for production video.
If you want to input commands to X11 programs, there are a few tools. **cnee** is what I've been using when xdotool doesn't work, but there are lots of better options if you have $$$$ for a proper, commercial, testing tool.

I have no idea how to have a single program be able to get passed X-security for multiple users.  For one user, you can try to set the DISPLAY (correctly), but that will only work if an X/session exists and doesn't violate X/security.  The X/Client is the application and sends commands to the X/Server for display and interaction.  That client-server connection is where most programs inject/break the security to accomplish non-standard things.  I'm loath to share this, but check out **xhost** which can be used to break X11 security.  The X/session on the client will need to allow it. It is a really bad idea, but some places use it, opening up every machine to attacks.

If you use Wayland, I have ZERO idea how to accomplish this. I think the only working screen capture things are from the Gnome project.  Wayland and Gnome seem to be partners in this crime.  OTOH, Wayland is local-only, non-networked, so the main goal for it is simplicity and performance.


I am able to run other services without any issue, but with XDOTOOL it's not working.

---

### Post by TheFu on 2021-12-07
xdotool has to be tied to an X/session to work.  X/Sessions are per-userid and don't get created until a GUI login happens.
Google found this, which appears to have a possible workaround. [https://github.com/robinuniverse/Keebie/issues/10](https://github.com/robinuniverse/Keebie/issues/10) I haven't tested it, but did mention it in post #5 above.

---

