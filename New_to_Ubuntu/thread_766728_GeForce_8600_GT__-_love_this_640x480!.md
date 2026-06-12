---
title: "GeForce 8600 GT  - love this 640x480!"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by mpls1 on 2008-04-25
Hi,
This is the second machine I've tried to get screen resolution on to no avail.  For this current machine (8600 GT): First I installed the NVIDIA driver through Envy.  After reboot my screen resolution dropped down to 640x480.  There is actually an NVIDIA server settings option on the administration menu but I just touch it with the pointer and it blows up to an impossible size.  I then uninstalled the driver, rebooted (got me back to an almost tolerable screen resolution(except for all the purple polka dots )), reinstalled the driver using the restricted drivers choice, rebooted, and back to 640x480!  I then tried using the sudo dpkg-reconfigure xserver-xorg command and rebooted. No change.  Frankly, I didn't understand what all the questions about my keyboard had to do with anything (probably revealing the depths of my ignorance).  I've read about manually installing the driver, but I have no idea how to do that.  Fortunately, I see one of the moderators, sloggerkhan, seems to be using this particular video card, so I have some hope.  On the first machine on which I experienced failure (e-Geforce 7600 GT)(also used Envy), there seemed to be some issue with detecting the monitor, so I mention it is a Viewsonic VX 2025 WM.  Thanks for any help you can give.

---

### Post by PmDematagoda on 2008-04-25
First uninstall the nvidia-glx-new package with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

Then use Envy and reinstall the driver, once that is done, do these changes:-
1) Open a modules file for editing with:-
```
sudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia"
```
and save the file.

Then reboot and see if the problem is solved.

---

### Post by nge on 2008-04-25
I think the manual install is the best option. Never had luck with Envy; I;m using the 7900 GS.

* hint: download the script/package (the NVIDIA-blah-blah-blah.RUN file) from nVidia DIRECTLY !!

[https://help.ubuntu.com/community/NvidiaManual?action=fullsearch&value=linkto%3A%22NvidiaManual%22&context=180](https://help.ubuntu.com/community/NvidiaManual?action=fullsearch&value=linkto%3A%22NvidiaManual%22&context=180)

---

### Post by muteXe on 2008-04-25
Envy has been the solution of my screen resolution problems for two releases now.  If i have problems with screen res problems in 8.04 tonight (my beer and installation evening :) ), it's the first thing I'll be trying.

---

### Post by joshsmith on 2008-04-25
why didnt you install from the hardware-drivers menu first?

---

### Post by muteXe on 2008-04-25
As i remember, i tried that and it went horribly wrong.  I reinstalled linux (which looking back, wasn't necessary in hindsight).  No matter what I installed, or how many times I manually changed my xorg, i still had loads of problems.  Someone suggested Envy, and that just worked.

---

### Post by howlingmadhowie on 2008-04-25
you could try installing nvidia-settings and starting it as root.

---

### Post by rajeev1204 on 2008-04-25
> **PmDematagoda said:**
> First uninstall the nvidia-glx-new package with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

Then use Envy and reinstall the driver, once that is done, do these changes:-
1) Open a modules file for editing with:-
```
sudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia"
```
and save the file.

Then reboot and see if the problem is solved.


Ok, as a mod, why u advice envy?

Isnt restricted driver manager just as good or bad?

---

### Post by bijeeshvs on 2008-04-25
I am not sure it will work or not, but me too have a similar problem about the screen refresh rate. every time i changed the settings in the nvidia settings at no avail. every time the machine reboots the refresh rate will go back finally i changed it in the system->screen resolution an it did worked may be this could help you also as you didnt mentioned about changing the same , i too installed driver with envy

---

### Post by mpls1 on 2008-04-25
Hi again,
     I purged the NVIDIA driver (them maybe mistakenly auto-removed some additional files at apt-get's suggestion), edited the restricted modules files as directed, reinstalled the driver with Envy, rebooted, and now, upon every reboot it seems to hang on "running scripts" and then gives me a warning dialogue box that ubuntu is running in low graphics mode (same unresolved problem I was having on the first machine).  When I go into administration>hardware drivers there is now not even an option to use the restricted driver.  I went to the NVIDIA site, downloaded the proper driver, and issued the command to install from the terminal.  The file decompressed but then I was told I must exit the xserver to install the file.  I know this is some simple thing to do, but I don't know how to do that.  I read somewhere that you hit cntrl,alt,break; which I did, but this just takes me back to the login screen.  Sorry for the stupid question, but how do I exit the xserver?  Thanks again.  You guys are astoundingly busy today.

---

### Post by stchman on 2008-04-25
> **mpls1 said:**
> Hi,
This is the second machine I've tried to get screen resolution on to no avail.  For this current machine (8600 GT): First I installed the NVIDIA driver through Envy.  After reboot my screen resolution dropped down to 640x480.  There is actually an NVIDIA server settings option on the administration menu but I just touch it with the pointer and it blows up to an impossible size.  I then uninstalled the driver, rebooted (got me back to an almost tolerable screen resolution(except for all the purple polka dots )), reinstalled the driver using the restricted drivers choice, rebooted, and back to 640x480!  I then tried using the sudo dpkg-reconfigure xserver-xorg command and rebooted. No change.  Frankly, I didn't understand what all the questions about my keyboard had to do with anything (probably revealing the depths of my ignorance).  I've read about manually installing the driver, but I have no idea how to do that.  Fortunately, I see one of the moderators, sloggerkhan, seems to be using this particular video card, so I have some hope.  On the first machine on which I experienced failure (e-Geforce 7600 GT)(also used Envy), there seemed to be some issue with detecting the monitor, so I mention it is a Viewsonic VX 2025 WM.  Thanks for any help you can give.

You need to install the nvidia 169.12 driver for the 8xxx series cards.

If you run Gutsy or earlier then download Envy 0.9.10 and first remove the nvidia driver and then select manual install of the 169.12.  Hit apply and let it go.  Let it mod the xorg.conf and reboot the PC.

If you have Hardy you will need to get EnvyNG.  I assume it has a similar process as I have never used it.  Envy is awesome for nvidia and ATI cards.

Now for your resolution problem.  I experienced this in Feisty and I simply put:

"1920x1200"

as the first res in the lines of resolutions in my xorg.conf.  Of course sub the res you want for what I did.

I rebooted the workspace (CTRL-ALT-BKSP) and viola.

---

### Post by mpls1 on 2008-04-25
Neither Envy or the Restricted Drivers manager are working for me (I'm using Hardy by the way, sorry I forgot to mention it).  I'd like to try a manual install next, if I could just figure out how to stop the x server.
Thanks again.

---

### Post by stchman on 2008-04-25
> **mpls1 said:**
> Neither Envy or the Restricted Drivers manager are working for me (I'm using Hardy by the way, sorry I forgot to mention it).  I'd like to try a manual install next, if I could just figure out how to stop the x server.
Thanks again.

Did you install EnvyNG?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Envy 0.9.10 is for legacy OS like Gutsy and earlier.

EnvyNG is in the Hardy repos, that is how good the program is.

---

### Post by philinux on 2008-04-25
No help from me sorry but my new base unit arrives tomorrow and guess which graphics card it's got. No kidding.

---

### Post by mpls1 on 2008-04-25
Yes, I did install ENVYng, the correct one for Hardy.  Sure would like to know how to stop that Xserver though :)   Thanks again.

---

### Post by philinux on 2008-04-25
xrandr is the new gui in hardy. System prefs > screen res.

What option on resolution does it give.

---

### Post by mpls1 on 2008-04-25
It give me a choice of 800x600 or 640x480.

---

### Post by rajeev1204 on 2008-04-25
restart x server with ctrl alt backspace

---

### Post by starcannon on 2008-04-25
I have 1 Desktop running an Nvidia 6600gt, 1 Desktop running twin 7950gt's in sli mode, and 1 laptop running an 8400m gs. All of them work perfectly and heres how I do mine.

[http://ubuntuforums.org/showthread.php?p=4784232#post4784232](http://ubuntuforums.org/showthread.php?p=4784232#post4784232)

Hope that helps, post back and let us know

P.S. The method I use does require you to download the driver for your card from [http://www.nvidia.com](http://www.nvidia.com)

---

