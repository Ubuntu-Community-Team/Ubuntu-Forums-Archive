---
title: "low graphics mode alert"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by zirgut on 2012-06-08
Hi,
I attempted to disable the guest log-in on ubuntu 12 .04 and seem to have caused more problems as I am now getting this message coming up that says something to the effect "Ubuntu is running in low graphics mode. You will need to configure them yourself. " This is then followed by a box that lists 4 possible options and a cancel and ok box at the bottom. None of these are functional as the mouse and keyboard are not working at this point. I have tried restarting the system in recovery mode but end up getting the same messages.
Your help would be greatly appreciated. I am on a dell computer with I believe a Nvidia graphics card

---

### Post by zirgut on 2012-06-08
Oh and I am now using my super slow windows 7 to make contact

---

### Post by fantab on 2012-06-09
If you are using any proprietary graphics drivers then try reinstall them. 

Tell us what did you do after which you got those errors? Was Ubuntu working properly before?

---

### Post by zirgut on 2012-06-09
Hi,
I really appreciate you getting back to me.
The situation has changed somewhat because my partner came down this  morning and successfully used ubuntu. It appears that if ubuntu is  started up without entering any keys to select the mode i.e recovery or  whatever then the mouse will work. So I still got the same message with  low graphics mode and could not detect graphics card. After clicking in  the ok box the next box with the 4 options appeared and I was able to  click on the option to operate for this session in the low graphics  mode. I can let you know what the other options are in the box if  necessary.
Ok what I did to disable the guest log-in , which has been successful by the way, was to enter in the terminal 
gksudo gedit /etc/lightdm/lightdm.conf

and then in a new box enter allow-guest=false

I was following instructions from papibe.
Now i did this once and then realised that I had not saved it so went  back and did it again and saved the file but was a bit confused as to  where to save it.
In the end saved it in the option that came up which I cannot remember what it was. Sorry for being so novice.

Before this Ubuntu was working ok although on occasions a message  appears saying that an internal fault has been detected and I send an  error report and carry on as normal.

Do you have suggestions on how to reinstall the proprietary graphics drivers.
Kind regards

---

### Post by Lyfang on 2012-06-09
Could you post the output of the lspci command? Copy & paste into the Terminal:
```
lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
```

---

### Post by zirgut on 2012-06-10
Hi,
Thanks once again for your help.
This is what came up.

01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
Regards

---

### Post by deadflowr on 2012-06-10
> **zirgut said:**
> 
Do you have suggestions on how to reinstall the proprietary graphics drivers.
Kind regards

Open up the dash, or the cog on the top-rightside(at the cog click system-settings) go to Additional Drivers. If the Nvidia drivers are active it will be marked green, if not check it and activate. When it is done installing the computer will need to be reboot. I don't foresee any graphics issues for you, as I have that same card on another system, and it runs smoothly. This is assuming you've cleared up your keyboard and mouse issues.

---

### Post by zirgut on 2012-06-11
Thanks deadflowr,
Went to additional drivers and clicked on it and it started searching for additional drivers and after 10 minutes of watching a little red line going back and forth I got bored and stopped it. The logo for the additional drivers is green however so I don't know whether that means it is installed ok. I did restart the machine but the same message occurs. The mouse and keyboard are working but only work if I do not use the keyboard to enter anything before the mouse cursor has appeared on the screen.
What I am going to do is get some more info from the second warning screen that gives the 4 options , one of which is troubleshooting the problem. I will put that in another message in a short while.
Thanks

---

### Post by zirgut on 2012-06-11
Ok when I go to trouble shoot problem in the second box with the four choices I am presented with another four options  the first of which is review xserver log file. In this there is a huge amount of data which because I am not logged into my account I can't copy in the copy  and paste mode. But within all that data are lines about not being able to open nividia.
Such as [20.829] (WW) Warning, couldn't open module nividia
and a few lines later
Failed to load module"nouveau" (already loaded,o)

Another option under the trouble shooting is Review start up errors and in this category it says Fatal Server error
Server is already active for display O followed by a bit more stuff
Under the option Edit configuration file there is not much
And in the final option Archive configuration logs is included this line 
/var/log/failsafe X-backup-120611230750.tar

From the second box apart from the trouble shoot option is the option to Reconfigure graphics and this allows 2 options which are  Use default (generic) configuration
or  Use your backed up configuration.
I have not tried either as I don't know what I am doing and it feels like Russian roulette with only a fifty fifty chance or less.
When I try the other option which is Exit to console login I only get the ubuntu symbol and the five continual flashing dots but no login screen until I get bored and switch the machine off at the on off button. The other option which gets me started is to use the machine in low graphics mode for this one session. I have to say that I have not noticed any difference with the graphics but heh I am not sure what I should be looking for. 
Let me know if there is any further info that I might be able to post that might be useful to help solve the issue.
In gratitude for your support.

Thanks

---

### Post by zirgut on 2012-06-15
Hi,
My problem seems to have evaporated after downloading the latest batch of ubuntu updates. Although the guest log-in has been reinstated, which in my attempt to remove it was the cause of the problem. So I may just live with it for the time being and allow my partners daughter free access to facebook and to leave the computer on all night. Ho ho a small price to pay!!

---

### Post by fantab on 2012-06-17
You can remove the GUEST LOGIN 'entry' by editing /etc/lightdm/lightdm.conf

```
sudo gedit /etc/lightdm/lightdm.conf
```add or edit line:

**allow-guest=false**

and save the file. logout-login.

This only removes the Guest Login entry... I think it is as good as disabling Guest Login.

---

### Post by zirgut on 2012-07-03
I hope I might reopen this thread as I have got myself into the same situation for the same reasons. Thinking that I was now wiser I tried once again to remove the guest login with the same result. I have also been working on another issue which is that I cannot get sound when I play videos. I do not know whether the 2 problems are linked. I have another thread going for ther loss of sound but I am hoping to come at the problems from 2 sides so to speak. At the moment I cannot access ubuntu 12.04 from the start up as the log-in screen does not come up.It is only when I go to a previous version of linux that I eventually get success. I have the pink screen for about 2 minutes and then it goes black and then 5-10 seconds later the low graphics mode warning notice comes up and I am able to log-in via the operating in low graphics mode for the one session.
I would be very grateful for any advice to solve this problem.
zirgut

---

