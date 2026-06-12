---
title: "Internal error with apport-gpu-error-intel.py"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by cellorules on 2012-09-05
Turned on my computer this morning and Ubuntu 12.04 said it had experienced an error, referring to /usr/share/apport/apport-gpu-error-intel.py

I'm getting this over and over... :| and I have no idea how to go about fixing this.

in addition, a strange picture appeared right smack in the middle of my desktop, on top of my desktop. It looks like a battery that is half full.

Any ideas?

---

### Post by cellorules on 2012-09-05
Haha! when I click on the picture, Compiz instantaneously crashes :)

---

### Post by cellorules on 2012-09-05
Oh, just so you know, I've been experimenting with using additional displays lately and the dialog prompts acted funny whenever I had another display plugged in - like most of the letters on prompts were not displayed. Could this have attributed to the problem?

---

### Post by NikTh on 2012-09-05
Hello , 

sometimes seems strange but apport error for apport itself ? 

If you have no problems with your system then you can disable apport's reports . 

For one session only 
```
sudo service apport stop
``` 

Permanent
```
gksudo gedit /etc/default/approt
``` 

and change the enabled from "1" to "0"  

save the document  , and no more apport. 

Thanks

---

### Post by cellorules on 2012-09-05
Thank you for showing me how to disable the notifications; however, I would like to know how to fix problems like this if possible. I haven't noticed any problems with the system as of yet, but the notifications are getting a little frustrating.

---

### Post by NikTh on 2012-09-05
> **cellorules said:**
> Thank you for showing me how to disable the notifications; however, I would like to know how to fix problems like this if possible. I haven't noticed any problems with the system as of yet, but the notifications are getting a little frustrating.

If you get multiple errors - notifications , then is good to report them , here first and then search for an existing bug in launchpad.net 

If the only error you receive is this > /usr/share/apport/apport-gpu-error-intel.py then probably apport has a problem . 

As I said above , it is strange but sometimes happens , apport report an error for itself. 

The workaround is to disable apport permanent and wait for an update (apport update) and then you can re-enable it. 

Thanks

---

### Post by cellorules on 2012-09-05
Oh sweet haha I thought it was odd when you said just to disable the notifications... it sounded like having your house on fire and turning off the smoke alarm because the beeping was annoying. :)

Thank you for your help!

---

### Post by rstribrn on 2013-01-14
I've got the very same problem with /usr/share/apport/apport-gpu-error-intel.py.

GPU hang a few days ago and since then apport is asking me over and over to send the report. However, if I do so, it wants reporting it again after the next reboot. The same behaviour is also when  I cancel or close it forcibly.

It is pretty annoying and I agree that disabling the notification completely is not a solution.

Some details:
- Ubuntu 12.10
- Lenovo T530 (Intel + nVidia graphics cards .... with Bumblebee installed  for handling nVidia Optimus technology)
    - It started when I tried running one game under WINE with bumblebee's "optirun"command. On the other hand, mentioned game worked fine...strange, really strange.
- Similar bug could be found here:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/723624](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/723624)

---

### Post by cellorules on 2013-01-14
I actually never took the time to turn off the notification and I just dealt with it - I updated to Ubuntu 12.10, didn't really like Quantal Quetzel, and reinstalled 12.04 - I've kept it updated and I haven't had a problem with it since. It's not a bad fix if you haven't really customized your ubuntu with libraries and such. Ever since I've just run all my operating systems in virtual machines.

---

### Post by sbyrnes321 on 2013-01-31
I suggest downloading xdiagnose and unchecking "Enable automatic crash bug reporting". A Canonical employee suggests that this is different and better than directly disabling apport:

[http://askubuntu.com/a/153480/95361](http://askubuntu.com/a/153480/95361)

My experience was that my computer was sometimes showing apport-gpu-error-intel.py but much more often just completely freezing / crashing. But after following that advice with xdiagnose, it hasn't been crashing at all.

(I have Ubuntu 12.04 on a Dell Inspiron 14Z Ultrabook.)

---

### Post by Dabo Ross on 2013-03-07
My system did have a gpu hang (I think). It froze for around 1 second, then was fine. Except for having multiple (like, over 10) windows pop up about an internal error which had to do with appot-gpu-error-intel.py. It also had multiple windows saying that apport has detected a possible GPU hang. I took this screenshot after I had closed the first few windows.
This is what my screen looks like right now:
[ATTACH=CONFIG]239860[/ATTACH]

---

### Post by surffle on 2013-03-07
I am experiencing this "internal error" as well and none of the programs on AWN will launch.

---

### Post by carl4926 on 2013-03-07
I get the error sometimes
But everything seems to be working normally.
FYI: It only happens in Unity - If I install Xubuntu or Kubuntu, never a problem. 12.04 or 12.10 both produce like results under test.
Reproducible on different machines with Intel graphics.

---

### Post by Dabo Ross on 2013-03-07
I should note that I also have optimus and am using Bumblebee, though the error didn't happen when I was using it...
Also I have had this happen once before, when I didn't have a GPU hang.
Also when I just booted up my computer, it said that "drive /tmp is not ready yet." and then some prompts about what to do to skip mounting it. I am not sure if that has anything to do with this problem, but it hasn't happened before.

And I also get an error about apport check resume crashing every time I reboot my computer.

---

### Post by layolayo on 2013-03-14
I keep getting this.

Running htop when it happens I see that Python is taking up 100% cpu power, the fan port on my laptop gets super hot and the following is reported in /var/log/syslog

Mar 14 16:49:49 lemur kernel: [13871.223190] CPU6: Package power limit notification (total events = 2385)
Mar 14 16:49:49 lemur kernel: [13871.223193] CPU4: Package power limit notification (total events = 2387)
Mar 14 16:49:49 lemur kernel: [13871.223196] CPU5: Package power limit notification (total events = 2386)
Mar 14 16:49:49 lemur kernel: [13871.223199] CPU1: Package power limit notification (total events = 2386)
Mar 14 16:49:49 lemur kernel: [13871.223201] CPU0: Package power limit notification (total events = 2385)
Mar 14 16:49:49 lemur kernel: [13871.223202] CPU2: Package power limit notification (total events = 2385)
Mar 14 16:49:49 lemur kernel: [13871.223205] CPU3: Package power limit notification (total events = 2384)
Mar 14 16:49:49 lemur kernel: [13871.223207] CPU7: Package power limit notification (total events = 2385)
Mar 14 16:49:49 lemur kernel: [13871.224183] CPU4: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224185] CPU6: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224186] CPU5: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224188] CPU1: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224189] CPU0: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224190] CPU2: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224198] CPU7: Package power limit normal
Mar 14 16:49:49 lemur kernel: [13871.224199] CPU3: Package power limit normal

Is this apport or something else???

---

### Post by jlsjonas on 2013-03-22
having similar issue, very annoying.
^subscription

---

### Post by sheoly on 2013-03-24
Same problem here. Very annoying.

```

Mar 24 11:43:30 fermi kernel: [ 1804.438559] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 24 11:43:30 fermi kernel: [ 1804.438564] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Mar 24 11:43:30 fermi kernel: [ 1804.448232] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Mar 24 11:48:57 fermi kernel: [ 2131.794114] CPU3: Package power limit notification (total events = 1)
Mar 24 11:48:57 fermi kernel: [ 2131.794116] CPU1: Package power limit notification (total events = 1)
Mar 24 11:48:57 fermi kernel: [ 2131.794118] CPU2: Package power limit notification (total events = 1)
Mar 24 11:48:57 fermi kernel: [ 2131.794120] CPU0: Package power limit notification (total events = 1)
Mar 24 11:48:57 fermi kernel: [ 2131.797172] CPU2: Package power limit normal
Mar 24 11:48:57 fermi kernel: [ 2131.797173] CPU3: Package power limit normal
Mar 24 11:48:57 fermi kernel: [ 2131.797175] CPU1: Package power limit normal
Mar 24 11:48:57 fermi kernel: [ 2131.797177] CPU0: Package power limit normal

```

---

### Post by SWGraphics291 on 2013-03-24
I get this with 12.04 LTS every now and again, i dont think there is actually a problem though, so...

---

### Post by ondra_spa on 2013-03-25
Same error here on Dell 15r 5110 i7.

---

### Post by AlmogBaku on 2013-03-28
I have the same error too: Dell Inspiron N4050

---

### Post by DanielVasicek on 2013-03-28
I continue to get the internal [h=2]apport-gpu-error-intel.py error[COLOR=#222222].  As my system boots up, the screen blinks a couple of times and then the system becomes inert.  The mouse reacts to manipulation.  But I cannot open a terminal window or other application.  I am using Ubuntu 12.04LTS. This problem began to show up a few weeks ago when I updated the system.  [/COLOR][/h]

---

### Post by CamPsych on 2013-03-29
Hey all. I have been having this exact problem as well and it seems that it stems from my Sandy Bridges chipset being incompatible and making the GPU fail. If anyone has a solution it would be greatly appreciated. 

I am running a new install of 12.10 Ubuntu. 

Fingers crossed for a solution. 

Cheers
Cam

---

### Post by CamPsych on 2013-03-29
Everything that I have read indicates for me at least, that the issues is with the Sandy Bridges, I have stopped apport at this stage to see how that effects things, however there have been some real system hangs. I will report back in the next day or so to say how this solution worked for me.

---

### Post by Slixt on 2013-03-30
I have this issue too.  I might disable it if it keeps happening. The same error and I get the impression apport opens its self to report it's self and yet again crashes causing an indefinite loop. Maybe a coincidence but, i first noticed it when  I added a new ppa source by mistake. (copied the wrong one.). I never installed anything from it and disabled it as soon asI realized it since it wasn't what I wanted. maybe an auto-update on something that was backgrounded after I enabled? It literally ran perfect up to that point in time and about 3 minutes later apport went off.

---

### Post by Slixt on 2013-03-30
if it helps, i'm running ubuntu on a toshiba satellite L755. I also installed kubuntu dekstop because i'm not fond of unity.

---

### Post by CamPsych on 2013-03-31
Hi all, 

THis current thread is marked as SOLVED, so probably won't get any further attention. If you want a further assist I would recommend starting another thread...HOWEVER, I was having the same problem and followed the instructions towards the end of this thread [http://ubuntuforums.org/showthread.php?t=2127593&page=6](http://ubuntuforums.org/showthread.php?t=2127593&page=6) which involves updating to Kernel 3.8. I also installed the PPAs which were recommended and not having any issues anymore. 

Cheers

---

### Post by wildmanne39 on 2013-03-31
What PPA'S do you mean the actual kernel PPA? or some other PPA?
Thanks

---

### Post by juanovic on 2013-04-02
Hi there. I am a NOOB, and I don't get what should I do. Should I change the kernel? use xdiagnose?(which I don't know how to use it btw:D)

---

### Post by CamPsych on 2013-04-02
Sorry Wild Man, forgot to write them altogether, linuxisfast recommended to install x-swat and ppa glasen/intel-drivers which I did and seemed to have solved the issue. 

@juanovic - read through [http://ubuntuforums.org/showthread.php?t=2127593&page=6](http://ubuntuforums.org/showthread.php?t=2127593&page=6)  as it seems that this is the best fix for the problem. Wild man may be able to let you know better than I on how to obtain the official new kernel.

---

### Post by wildmanne39 on 2013-04-02
This is where I got my kernel from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/)

You have to install linux-image-extra now as well as the usual three to get wired and wirless to work at least in my case using the ath9k driver for wireless.

---

### Post by Brendonbe on 2013-04-11
> **Wild Man said:**
> This is where I got my kernel from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/)

You have to install linux-image-extra now as well as the usual three to get wired and wirless to work at least in my case using the ath9k driver for wireless.

hi, as I never installed a kernel before further instructions how to do it would be appreciated.

---

### Post by Brendonbe on 2013-04-11
I finally managed to install the kernel, following the instructions on [http://askubuntu.com/questions/253546/how-to-update-to-kernel-3-8-rc7-ubuntu-12-10](http://askubuntu.com/questions/253546/how-to-update-to-kernel-3-8-rc7-ubuntu-12-10)
However, the error is still appearing!?

---

### Post by Nesaskewatch on 2013-04-11
I had the exact problem on my Intel/Nvidia optimus system. Installing Bumblebee worked for me but I still kept forgetting to use optirun or an update would come along and the apport messages would resume, even after reinstalling BB. Graphics performance after a crash would drop substantially, so something was truly borked. I have a separate /home drive so I simply reinstalled the / drive and the problem went away. Kind of a shotgun fix but it works. I see there are some new Nvidia drivers in today's update (and new OpenGL yesterday) but I am not getting any answers as to whether they work with optimus so I am sticking with Bumblebee until I am sure.

---

### Post by jimafternoon on 2013-04-11
I'm having the same issues now after getting an update last night. Additionally, sometimes I can't even boot up, the screen stays black and says I'm in 'low graphics mode', and I have to reboot. My wireless has now slowed to a crawl. My machine is basically unuseable in this state.

---

### Post by Dabo Ross on 2013-04-11
I usually am optirunning at least one application, and using the sandy bridge mobile for a few others when I get a GPU hang. I actually can't remember a time that I got  GPU hang and then the error when I wasn't using both graphics cards.

I would also suggest to NEVER use nividia drivers with Optimus, they completely break your system and only way to fix it is to reinstall Ubuntu. When u first installed the nividia drivers without knowing this I was stuck with a 640*480 screen, unity 2D,and my system ALWAYS running in  'Low graphics mode'. The only way I fixed that was by re installing Ubuntu. 

Also after having this error I tried re installing again, and it hasn't fixed it. It made the errors go away for a while, but they came back. 

Also more detail into when I get the error, I am usually running Netbeans without optirun, chromium with YouTube without optirun, and mine craft in the background running in optirun with pretty high graphics settings. Also I sometimes have a non-optirun terminal running ssh into a server.

---

### Post by jimafternoon on 2013-04-11
I just installed the latest version of 13.04 and so far so good. I've downloaded updates and rebooted several times, no issues so far.   Keeping fingers crossed.

---

### Post by Dabo Ross on 2013-04-11
I would try 13.04, but I don't think BumbleBee has support for it. Correct me if I'm wrong.

---

### Post by Brendonbe on 2013-04-11
Upgrading to 13.04 works fine for me too - no error messages any more!

---

### Post by jimafternoon on 2013-04-11
Cool. Mine is still running well also. 

I just got an update with a few 'apport' files in it, hopefully it holds up.  :D

---

### Post by Dabo Ross on 2013-04-11
Just got another apport-check-resume error, when I hadn't even hiberanted/suspended before. I had shutdown my computer, and when I booted up I got a apport-check-resume.py crash. (the apport-check-resume.py program crashed), when I don't think it even needed to be running.

---

### Post by jimafternoon on 2013-04-12
I just found this, it's a post from just 2 days ago. 

[http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)

Anybody know if this might legitimately help some of these graphics issues?

---

### Post by Dabo Ross on 2013-04-12
I think that this might be a problem with sandybridge graphics cards?

Who else having this problem has a sandybridge intel graphics card?

I personally have optimus with sandybridge mobile and gforce.

Also it would be helpful if people would post more details on the "apport error" by clicking view details, and pasting some info here

---

### Post by Dabo Ross on 2013-04-14
> **jimafternoon said:**
> I just found this, it's a post from just 2 days ago. 

[http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html](http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html)

Anybody know if this might legitimately help some of these graphics issues?

I doubt it, I don't think this is a problem with ATI/AMD Catalyst.

Also, is there anyone running 13.04 who doesn't have this fixed?

EDIT: Sorry about double-post, somehow I missed that I had made the last post. I haven't been very aware recently.

---

### Post by jimafternoon on 2013-04-14
13.04 has solved all my problems. I haven't had any issues at all since upgrading.

---

### Post by Dabo Ross on 2013-04-14
> **jimafternoon said:**
> 13.04 has solved all my problems. I haven't had any issues at all since upgrading.

Ok!
I will upgrade soon and test. W/ backups in case other things are broken with 13.04.

Just as a question, do you have an optimus laptop?
And what graphics card do you have?

---

### Post by jimafternoon on 2013-04-14
No, I have a Lenovo. 

I have the switchable graphics.  So its the Intel HD 3000 / AMD Radeon HD 6470M for me.

---

### Post by marisdembovskis on 2013-04-23
I had Apport-gpu-error-intel.py crash every 10 minutes!
Updated today, everything is fine! 
SOLVED for me! (Toshiba Portege Z830 )

---

### Post by Tyguy7 on 2013-04-26
I have a Samsung rc512 with the Optimus video card, intel AND nvidia GPUs.  I'm running 12.04 with bumblebee and getting the exact same repetitive apport error messages.  Sometimes the text in the error messages are garbled as well.  I'm going to run an update to the lastest 13.04 and see what happens.

---

### Post by Tyguy7 on 2013-04-26
Well, I had to install 12.10 before I could go to 13.04, and I thought I'd give it a whirl before I went all the way to 13.04, and it seems like the problem is fixed.... I'll post again if things destabilize.

---

### Post by Dabo Ross on 2013-04-26
It hasn't happened to me at all since I updated to 13.04!

---

### Post by Tyguy7 on 2013-04-26
I take back my previous comment about it working in 12.11, I started seeing the errors about 30 minutes into my session.  I'm now upgrading to 13.04...:confused:

---

