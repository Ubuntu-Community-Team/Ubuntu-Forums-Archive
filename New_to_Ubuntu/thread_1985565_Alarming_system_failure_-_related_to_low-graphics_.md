---
title: "Alarming system failure - related to low-graphics mode?"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by mywinningsmile on 2012-05-23
Hi there

Just had a hairy ten minutes trying repeatedly to boot up my laptop (Aspire 5755G) and being defeated. I'm now running 12.04 LTS, since about a week ago, and have been using Ubuntu (as a first-time user) since getting this machine last November. 

I've had some periods of trouble booting before now, but nothing so sustained. In several instances I was presented with a (standard pop-up) window saying

> The system is running in low-graphics mode
Your screen, graphics card, and input deice settings could not be detected correctly. You will need to configure these yourself.
                                   |OK|
the mouse pointer was invisible, but I Entered to close this and open up a new window reading

> What would you like to do?

Run in low-graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console logon
                                          |Cancel/Ok|  
This screen would always defeat me, with no pointer visible and no buttons responsive, I would have to hard-reset it.

On another instance I got to the familiar Ubuntu purple screen but the screen quickly corrupted, recorrupting whenever I touched the tracker pad, in a hall of mirrors reflection of the mouse pointer not unlike those I experienced on dragging old windows machines before they wept.

Other times I wouldn't even get to this stage of the start-up, and would be presented with text on black-screen, before it shut down. Once I managed to capture a photo of it, which I've transcribed here:

>  [   20.065952] aga2.00 exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x6 frozen
 [   20.066003] aga2.00 cmd a0/01:00:00:00:10/00:00:00:00:00/a0 tag 0 dma 4096 in
 [   20.066004]               res 50/00:03:00:00:10/00:00:00:00:00/a0 Emask 0x4 (timeout)
 [   20.066069] ata2.00: status: { BODY }
Although I think the text was different on other occasions.

Finally, for no obvious reason, it has booted up without pain.

Any thoughts? First steps to minimise risk? Anything appreciated.

Thanks
Alex

---

### Post by mywinningsmile on 2012-05-23
I understand that the dmesg and xorg files can be useful, so I just pulled them. Had to cut them into sections to obey file rules.

dmesg:

---

### Post by mywinningsmile on 2012-05-23
and xorg files...

---

### Post by mywinningsmile on 2012-05-24
I'm now getting a pop-up once start-up completes that tells me there is a system problem and asks me to enter password. Forums tell me this is a legit technique, and moving through this I'm presented with the following screens...

[https://picasaweb.google.com/117881239745309604424/UbuntuError](https://picasaweb.google.com/117881239745309604424/UbuntuError)

If anyone has any ideas, I really appreciate it... getting pretty concerned!

Thanks
Alex

---

### Post by jyosrini on 2012-10-02
S. Madabhushi,

I too am facing this problem since the last 2 days.  I think I filled up the available space on my netbook to the maximu after which I shut it down properly.  On re-boot, I am getting the same error message as described in this thread above.

I checked on the google for any possibile solutions.  I found one which might work.  I will try it out tonight and confirm in my next post.  The recommended solutions is as follows:

"  **There is a way to reset your Desktop settings back to their defaults.** If you keep in mind that everything in Linux is a file, all of its settings are files. All of Gnome’s customizations are located in their own specific folders. And these settings are user specific; they are in your Home folder. If you would create another user and log in with that user, you wouldn’t have any of the problems you are having in your own account. If you remove all these folders, you essentially remove all the settings. **Therefore, we will remove the folders needed to reset Ubuntu/Gnome back to its defaults.**
  **UPDATE (2008.01.30):** Keep in mind that this will only reset your *Gnome-specific* settings. If you are having problems with your video card, display, x-server, etc., this WILL NOT fix your problems.
  If you don’t have access to your graphical ([GUI]("http://en.wikipedia.org/wiki/Gui")) desktop to delete these folders in [Nautilus]("http://en.wikipedia.org/wiki/Nautilus_file_manager") or you’re stuck at the login screen, drop to a terminal by hitting **CTRL + ALT + F1**, login to your account, and run this command:
  **rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
  Get back to your GUI desktop by hitting **CTRL + ALT + F7**.
  Login and VOILÀ! Just like the first time you ever logged into your Gnome desktop."


Hope this helps

---

