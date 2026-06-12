---
title: "Remote Desktop Connection 12.10 x64 , using Doze HP 7 x 32"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by 90Ninety on 2012-12-31
Hmm got Ubuntu 12.10 x64 and Windoze 7 x32 client machine . I want to run the Ubuntu headless and control it remotely . 
[https://answers.launchpad.net/ubuntu/+source/unity-2d/+question/211997]("https://answers.launchpad.net/ubuntu/+source/unity-2d/+question/211997")
 Its supposed to be easy but im having technical difficulties . im using the steps 1-14 below . However I get to step 10 and Windows give me a Biatch 'cant connect'error . I have a feeling I slightly messed my Samba config file . Anyhows Suggestions , any of ?

```
You just need to set up the Desktop Sharing and make a note of my computer name on the Ubuntu 12.10 PC:
1. dash - Type in "Desktop Sharing"
2. Click on Desktop Sharing
3. Tick Settings -
   Allow Users to View
   Allow User to Control your Desktop
   Require Password - set a password (remember this for later)
   Notification - what ever you like
4. Close window
5. To get the computer name click on the top right hand icon - Slect About This Computer. (Make a note of the computer name)
[COLOR="Red"]
On Windows 7 PC[/COLOR]
6. Click on Start - Search Box - Type in "Remote Desktop Connection"
7. Select "Remote Desktop Connection"
8. Put Ubuntu PC name in "Computer"
9. Edit the username and password to that of your standard Ubuntu login
10. Click on "Connect"
11. Change "Module" to "vnc-any"
12."IP" should have the Ubuntu PC name in there (or IP address if you know it)
13. Port should be "5900"
14. Password is the one you put in the Ubuntu Desktop Sharing box above in line 3.
15.  Click on ok.

You should now be able to connect. It's not as good as Ubuntu 12.04 when I used to use "sesman-xvnc". There's more lag on the mouse and the screen does not auto resize but it's more than good enough for admin purposes. t
```

---

### Post by 90Ninety on 2013-01-09
Bump

---

### Post by cybergalvez on 2013-01-09
desktop sharing in Ubuntu has nothing to do with samba, it uses vnc by default. steps 1-5 set up vino (vnc server) on ubuntu to accept passworded connections. Assuming you've done that correct, you need to make sure you can actually see the ubuntu box from the windows box. try opening up a command prompt and ping your ubuntu computer. if you can't reach it try pinging the ubuntu IP. if you can ping it with the IP but not the name, then just use the IP in step 8, or configure you router better is you want to use the name. If you can't ping the ubuntu computer even with the IP address you are going to have give us some more info.

---

### Post by Sean.m on 2013-01-09
Do you have the firewall enabled?

You can check this by running ```
sudo ufw status
```

Can you even ping the Ubuntu machine? I don't mean to patronize but there have been plenty of times when I didn't check the obvious things and wasted a lot of time.

Also, have you verified that you can log in to Unity 2D? VNC doesn't work on a composited window manager, meaning a desktop that has OpenGL accelerated effects. Any more specifics you can give about your setup and the error you're seeing would be helpful.

---

