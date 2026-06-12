---
title: "Monitor Resolution Problem"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by curmudgeon2 on 2012-05-22
I'm afraid I treat the community as I would a Doctor:  As long as all is going well, I stay away, or I lurk and search until I find the answer I need.  While there's no valid excuse, there is a reason:  As a senior, north of 70, and a computer "user" only, I don't feel that I have the knowledge, nor skill to have anything worth while to say.  Additionally, my failing eyesight does not allow me to spend the hours needed for me to properly comb the thousands of posts here.

Suffice it to say that I've used UBUNTU for about 5 years, and I'll have to say that while I like the UNITY desktop, it has been the most problematic installation of any I've made.  This is the first time in 5 years that I've considered switching OS, and I did give Mint 12 a go, but found it as troublesome, if not more so, than the current 12.04LTS.

My problem: I have a 5 year old 17" Dell, Ultrasharp monitor-Mod #1707FP with an optimal resolution of 1280 X 1024.  I have set this resolution in the "Appearance" sys setting.  I have also activated the Nvidia (post release updated driver) in the Hardware sys setting.  However, every time I attempt to boot up, I get a screen dialog as follows: 

"Analog Input Cannot Display This Video Mode"
     "Optimum Resolution 1280 X 1024 60 HZ"

Some times the boot process will continue after 15-30 seconds, and sometimes the screen just freezes at that point.  I use "Ctrl-Alt+Del"  to cycle through the boot up process again.  Some times it boots, after a 15-30 second pause at the above stated dialog, and sometimes I have to repeat the process.  This did not happen with my former "Lucid Lynx" 10.04 LTS OS.

Would sure appreciate some help, as undeserving as I am.  In my defense, I do spread the word about UBUNTU, and offer free installation disks to all who would like to give it a try.

Thanks for any consideration, forbearance, and attention to my problem.

---

### Post by cariboo on 2012-05-22
Use the Nvidia X server Settings applet to set your resolution, you can access it by opening the Dash and typing ***nv***. See the screenshot.

---

### Post by curmudgeon2 on 2012-05-23
I gave it a try, and while it changed the resolution for the session, as soon as I signed off/restarted the resolution problem delayed the boot up process again.

So, having two HDs, I re-installed 10.04LTS on one HD, and that eliminated the problem when booting from that drive.  The problem still exists when booting from the HD containing the 12.04LTS OS, but, oddly enough, the delay at the annoying "Analog Input....." dialog lasts only a few seconds before proceeding with the boot up. With 12.04 loaded on both HDs, the delay in the boot up process was much longer and sometimes it was a complete freeze up.

While I don't even begin to try to understand what the advances in the newer Kernel, and Gnome, have done to the OS, it seems fairly obvious that newer hardware is required to get the 12.04 LTS OS to run as flawlessly as I've learned to expect from UBUNTU.  

One positive outcome from my experience is that I learned from the Nvidia X Server Applet that I'm running the GeForce 6150SE nForce 430 graphics card.

Thanks again for your time, suggestions, and consideration. It seems that the simple answer is to upgrade to a newer monitor; but that's not necessary running the 10.04LTS, and that works for me, for now.:)

---

### Post by Perfect Storm on 2012-05-23
Try making the changes as superuser;
```
gksu nvidia-settings
```
 and remember to 'save to X configuration file'.

---

### Post by curmudgeon2 on 2012-05-23
I appreciate your suggestion and will give it a go. BTW, I did remember to 'save' my settings when resetting the nvidia resolution setting on the X server applet.

While I don't pretend to understand the interaction between the OS and the hardware, other than it happens, if my "5 yr old" monitor is designed to max out at a resolution of 1280 x 1024, how can changing the settings in the software outside the limit of the hardware make any difference?:confused:

Thanks again for your tolerance. It must be extremely exasperating dealing with folks who have no concept of what's actually going on!

---

### Post by curmudgeon2 on 2012-05-23
I used the terminal as you suggested and entered your "input".  Of course, it brought up the same nvidia x server applet as the GUI, and I again changed the resolution to 1920 x 1280 and saved it.  Of course I also got a pop up dialog box telling me my monitor could not support the setting, but I ignored, saved, and exited the panel.  

Now my top panel is stretched so far to the right that my "sound, date/clock, log in/shut down applets are out of view.

To run a test to see if the boot up resolution problem has been resolved, I manually depress the tower on/off sw which gives me my on screen shut down/restart dialog box and I restart.

Unfortunately, the resolution problem, as originally stated, remains the same.  

I think I've wasted enough of your time, and rather than wear out my welcome on these boards, I'll just continue using Lucid Lynx, for the time being.  Perhaps, by the time its support ends, I'll be ready for a new, wide screen monitor with the resolution support demanded by the new OSs.

It seems  where once the OS ran unobtrusively in the background, the newer OS now set the requirements for the hardware.  Progress??

Thanks again for your patience and efforts on my behalf.):P

---

### Post by d4m1r on 2012-05-23
Offtopic, but your knowledge of latest technologies is impressive given your age....I hope I can say the same for myself in 50 odd years :lol:

---

### Post by papibe on 2012-05-23
Hi curmudgeon2.

I'm also have an 5 year old Dell (Dimension E520). I also have a similar monitor (1907FP). However, I later installed a newer graphic card.

If you don't mind, I'd like to see the content of a couple of configuration files:
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by curmudgeon2 on 2012-05-24
Papibe,

Sorry, but you've very quickly exceeded the limits of my capabilities and understanding.:confused:

I entered the code both with and without the <sudo> super user cmd, without any valuable results, that I can determine.  I did some follow up searches of the Forum and tried changing the entry as required by OS later than 10.?  To no affect that I can see??

Sorry, but I do appreciate your attempt to help me out.  

I did try installing the "gnome-session-fallback" desktop environment to see if that would make a diff, but it did not; and I continued having the stated "resolution" prob. 

I will attempt to paste the results of my efforts at the Terminal, as directed, but I've never used that function, either, and it may take me a while to research using it??

---

### Post by papibe on 2012-05-24
No problem.

Those are files that can be opened, and then paste on that website, so we all can take a look.

To open the first one run this:
```
gedit /etc/X11/xorg.conf
```
Then you select all the text by pressing Control+A, and paste it in your browser in this page: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/")

Then press the button 'Paste!'. That will generate a new page, copy the url (in the address bar) and paste it back on a new reply on the forums.

Do the same again for the other file.

If you have any doubt just let us know.
Regards.

---

### Post by curmudgeon2 on 2012-05-24
Hopefully, the following URL is that for which you asked?:

[http://paste.ubuntu.com/1005130/](http://paste.ubuntu.com/1005130/)

Terry

---

### Post by curmudgeon2 on 2012-05-24
And, with any luck, here's the second URL for the data you requested:

[http://paste.ubuntu.com/1005151/](http://paste.ubuntu.com/1005151/)

I really think that you are going well beyond the call, but I deeply appreciate your efforts on my behalf...........All Of YOU.

Terry

---

### Post by papibe on 2012-05-24
> That's it.

Now, do the same procedure for the second file.

Regards.

Oops, you already did it... too impatience on my part :(

---

### Post by papibe on 2012-05-24
Ok.

It looks like the driver tries to set the resolution to 60hz, but later reverts to 75hz.

This is in your config:
```
Option         "metamodes" "1280x1024 +0+0; 1280x1024_60 +0+0"
```
But one of the last lines of the log is:
```
[    65.144] (II) NVIDIA(0): Setting mode "1280x1024_75"
```
I would let the driver to choose the best resolution for your monitor, that is usually accomplish by using a 'meta-resoluton' called nvidia-auto-select. That is what the driver usually set when you generate your config file using it.

Let's do that:
```
sudo nvidia-xconfig
```

Now restart your machine, and see what happens.

If you experince the same problem again, please paste again those 2 files (they are going to be different now, and it is worthy to take a look again).

Regards.

---

### Post by curmudgeon2 on 2012-05-24
Papibe,

I do want to clarify: it appears to me that you may be using Lucid Lynx as your OS??

I also have Lucid Lynx on one of my two removable HDDs, and when using that system, I do not experience the resolution problem that I have when using the Precise Pangolin Hdd/sys. (I can leave both HDDs locked in place and switch  between at start up  via the BIOS boot priority.)

That being said, I'll attempt to follow your current instructions ASAP.

Terry

---

### Post by curmudgeon2 on 2012-05-24
OK,

Did what you asked, and after restart the problem still exists, so here's the first URL requested, and the second will follow ASAP:

[http://paste.ubuntu.com/1005307/](http://paste.ubuntu.com/1005307/)

Terry

---

### Post by curmudgeon2 on 2012-05-24
And,

Here's the URL of the second terminal results:

[http://paste.ubuntu.com/1005318/](http://paste.ubuntu.com/1005318/)

BTW, Couldn't I have set the "auto" mode in the nvidia X Server applet also?

Terry

---

### Post by papibe on 2012-05-24
My 1907FP monitor has a button that when is pressed allow you to set some parameters, but also shows both the current and the optimum resolution.

Does yours have that? What does it say?

Also, could you post the result of these to commands?
```
xrandr

xvidtune -show
```  
Regards.

---

### Post by curmudgeon2 on 2012-05-25
> **papibe said:**
> My 1907FP monitor has a button that when is pressed allow you to set some parameters, but also shows both the current and the optimum resolution.

Does yours have that? What does it say?

Also, could you post the result of these to commands?
```
xrandr

xvidtune -show
```Regards.

Yes, my monitor has that button:  Current Resolution = 1280 x 1024 75hz
                                                              Optimum Resolution + 1280 x 1024 60 hz

[http://paste.ubuntu.com/1005869/](http://paste.ubuntu.com/1005869/)

I'm getting a blank page when I run xrandr.   What kind of cmd should be used, and what are we trying to see??

Logically, it appears that during boot up, some part of the OS is requesting a different resolution than has been entered in the sys settings.  Once past the "hang up" and  the boot up is complete, the system functions without a burp.

Terry

---

### Post by papibe on 2012-05-25
The last ones are actually commands, no files, so just run them as they are.

Regards.

---

### Post by curmudgeon2 on 2012-05-25
Oops,  this is probably what you were looking for??:

[http://paste.ubuntu.com/1005886/](http://paste.ubuntu.com/1005886/)

Papibe,  while I very much appreciate your willingness to share your time and expertise, not to mention your tenacity and  thoroughness, I very much hope that you'll feel free bring the search to an end before burn out or frustration become an issue.  

Spoon feeding this 'infant' has to get tiresome, at some point.

Warmest Regards,

Terry

---

### Post by papibe on 2012-05-25
How about the other command?
Regards.

---

### Post by curmudgeon2 on 2012-05-25
[http://paste.ubuntu.com/1006508/](http://paste.ubuntu.com/1006508/)

[http://paste.ubuntu.com/1006514/](http://paste.ubuntu.com/1006514/)

I think that does it??

---

### Post by papibe on 2012-05-25
Thanks.

At this point I think the problem could be related to (1) some slightly corrupted EDID (in your monitor), or (2) a problem with the current driver.

We can keep trying to get it right (60Hz), or go with the flow: use what is working (75hz) and set the Nvidia driver to skip 60 and go straight to 75.

To do that we need to edit the X configuration file. To open an friendly editor run this command as is:
```
gksudo gedit /etc/X11/xorg.conf
```

Add the bold line in the Monitor Section:
```
Section "Monitor"
  ...
  **Modeline "1280x1024_75"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync**
EndSection
```
Then look for this line on the  Screen section
```
    Option         "metamodes" "1280x1024 +0+0; 1280x1024_60 +0+0"
```
and commented so it looks like this:
```
    # Option         "metamodes" "1280x1024 +0+0; 1280x1024_60 +0+0"
```
Then add the bold line inside the Display subsection inside the Screen section:
```
Section "Screen"
  ...
  SubSection "Display"
    Depth 24
    **Modes "1280x1024_75"**
  EndSubSection
EndSection
```
Save the file and restart.

Tell us how it goes.
Regards.

---

### Post by curmudgeon2 on 2012-05-25
OK, Done:

[http://paste.ubuntu.com/1007354/](http://paste.ubuntu.com/1007354/)

I believe I've followed your instructions as the new script does appear in the appropriate sections??

Unfortunately, the changes resulted in no change to the "resolution hang-up problem" during boot up.

I'd be prone to go with your first theory, that there's a problem within the monitor itself. 

Thanks again for all your time and efforts on my behalf.  While I wasn't able to follow all that you were doing, the process did provide a good learning experience for me.

Kindest Regards,

Terry

---

### Post by papibe on 2012-05-25
You missed commenting the 'metamodes' line.

Regards.

---

### Post by curmudgeon2 on 2012-05-26
Ah, yes.

The result of inattention to detail, and seeing what you expect to see.

Thanks, I went ahead and made and saved the change, but with no change in the results.

Since it appears that the problem is likely a "hardware defect", how should I close out this thread??

Best Regards!

---

