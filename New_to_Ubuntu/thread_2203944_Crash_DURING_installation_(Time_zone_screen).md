---
title: "Crash DURING installation (Time zone screen)"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by maazmahmood on 2014-02-06
[COLOR=#000000]The following happened when I'm trying to choose my time zone (after I hit install):

 Installer Crashed. We're sorry; the installer crashed. After you close this window we'll allow you to file a bug report using the integrated bug reporting tool. This will gather information about your system and your installation process. The details will be sent to our bug tracker and a developer will attend to the problem as soon as possible.[/COLOR]

[COLOR=#000000]I also tried hitting Ctrl+alt+F1, then type in sudo service lightdm start, it's just a black screen, then when i hit ctrl+alt+f1 again, it takes me back to command line and says "start: job failed to start" (although, when I tried this again, it didn't have same result, (I know kind of inconsistent). [/COLOR]

---

### Post by xeonix on 2014-02-06
How are you trying to install? USB/liveCD ?

---

### Post by mörgæs on 2014-02-06
Please begin with a complete hardware description.

---

### Post by maazmahmood on 2014-02-06
Installing via USB
Full specs can be found here:
[https://support.gateway.com/s/PC/R/1014737R/1014737Rsp3.shtml](https://support.gateway.com/s/PC/R/1014737R/1014737Rsp3.shtml)

slight changes to specs, I do have an Nvidia 9800GTX+, it is not yet enabled in BIOS as the video config yet, using the integrated VGA for right now.
And yes I'm able to load up "Try ubunutu"

---

### Post by grahammechanical on 2014-02-06
When we install Ubuntu while we are filling in our user details and stuff the installer is working. This speeds up install times. So, the crash most proabely has nothing much to do with setting the time zone. You are still holding back on giving us information. What version of ubuntu? What other operating systems are on the machine?

Something tripped up the installer and at the moment it is impossible to even guess at what happened. What kind of user experience do you get when you run the Try Ubuntu live session? 

This could be (just guessing) a video driver issue. Try installing without ticking "Install Third Party Software." Then the installer will not try to install a third party (proprietary) video driver.

Regards.

---

### Post by maazmahmood on 2014-02-06
No other OS installed, it's xubuntu 13.10. When I run "Try Ubuntu" everything works fine. Yeah I tried unchecking the "third party software". 

Now I have another problem, I tried to change boot options for video from BIOS to the graphics card (didn't work before just wanted to see), but then I get nothing on both, so I tried factory resetting the motherboard (CMOS battery trick) and now the fan just gets really loud

just took out 2 ram sticks, alhamdulillah working so far. But fan is still loud. And another question, when everything is installed, how do I switch between my integrated graphics to my nvidia graphics?

Have been able to isolate the problem to 2 of my 4 RAM sticks. But I've already installed the OS, and when it came time to restart, it says that OS file not found.

---

