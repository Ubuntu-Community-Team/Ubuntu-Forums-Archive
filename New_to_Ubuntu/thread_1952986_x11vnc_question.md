---
title: "x11vnc question"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by eabel on 2012-04-05
i am new to ubuntu and debian linux.  i have ubuntu 11.10 running in an oracle virt. box VM ver 4.1.12.  Host OS Win7 home premium SP1.  My question is related to x11vnc.  Why can't I get x11vnc to display anything more than wallpaper with GNOME, UNITY, or Cinnamon? All works okay if I use GNOME Classic or Unity 2D.  I s this a WAD (works as designed limitation of x11vnc?

Thanks,

Ed

---

### Post by krunge on 2012-04-06
I'm not sure what is happening.  Try adding -noxdamage to the x11vnc cmdline.

---

### Post by eabel on 2012-04-08
Thanks, but that does not work. :frown:  Here is my upstart script:
 
&#9492;&#9472;(0:%)&#9472;&#9472; cat x11vnc.conf                                                                        &#9472;&#9496;
start on login-session-start
 script
 x11vnc  -rfbauth /home/eddie/.vnc/passwd -ncache_cr -xkb -fixscreen -noxdamage -norepeat -noxrecord -noxfixes -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
 end script

 
I have had the -noxdamage in since I found the script on the web, works only with 2D like Unity2d or gnome classic.    Just wallpaper and a cursor on Unity or cinnamon.
Oh ya, if you use KDE is does work, but I'd rather not.  Blew away kubuntu, running pure ubuntu 11.10 with Cinnamon 1.4 on an Oracle Vbox VM, ver 4.1.12.  Win7 is the host.
 
Regards, 
 
Ed  :-)

---

