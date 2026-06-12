---
title: "Blender"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by Yinepu on 2012-01-03
Hi, I can't get Blender and other 3D programs to run properly. In Blender, I can only subdivide and object once; any more it crashes, in both the Linux Blender and the exe running under Wine. And other 3D programs don't open in the first place. Is there a driver or a package I need to install to get these to work?

---

### Post by mcduck on 2012-01-03
Are you using the Blender version from Ubuntu's repositories, or the latest one from the website?

And since Blender runs it's whole user interface using OpenGL, what kind of graphics card you have, and what drivers are you using for it? And of course the specs of the rest of the system?

Finally, have you tried to start Blender from a terminal? That should at least give you an error message when blender crashes so you'd have a bit more information about what went wrong...

---

### Post by Yinepu on 2012-01-03
I'm using the one from the repository. I'm running integrated Intel graphics, but I'm not entirely sure what type, or what driver I have. My other specs are: (IBM Thinkcentre a58 ); 2.8GHz P4, 1GB DDR(1) RAM. I don't think it's the hardware as it ran fine when I was using XP (though that was Blender 2.49b which I can't find for Linux/Ubuntu)....

---

### Post by mcduck on 2012-01-03
The perhaps you could try the latest Blender version (2.61) form the web site? That's what I'm using currently and it seems to be working perfectly. It's rather easy to install, just download the package, extract where ever you want and run it from there.

Of course it could just be related to the graphics card, especially if you had problems with other 3D apps as well. While I know Intel cards should be enough to at least run Blender, I also know that many people are having performance problems with the Intel drivers. Trying the latest drivers from the x-swat or xorg-edgrs PPA repositories might help.

---

### Post by Yinepu on 2012-01-03
No, I've downloaded the new version and it still has the same problem in more than one subdivision, and there's no message in the terminal when run from that. I'll try getting a new driver....

---

### Post by Yinepu on 2012-01-03
So how do I update the drivers?

---

### Post by mcduck on 2012-01-03
> **Yinepu said:**
> So how do I update the drivers?

If you are using either one of the PPA repositories I mentioned, just add the repository (using the add-apt-repository command found on their web sites) and run normal system updates. The updates will pick the new driver version from the PPA repository automatically.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric")
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

---

### Post by Yinepu on 2012-01-04
No, that's not done anything.

---

### Post by mcduck on 2012-01-04
Which repository did you enable? Did you actually get any updates? Which ones, and did they install correctly?

"It didn't work" sadly doesn't provide any information that would help further troubleshooting the problem... ;)

Anyway, apart from the generic guidance of checking your system logs and ~/.xsession_errors for any error reports when the program crashes, this was pretty much all the help I can provide with the available information.

---

### Post by thepreecher on 2012-06-17
i was using blender ppa svn whatever and it was working great.  please excuse me if i'm hard to understand kinda new.  i upgraded to 12.04 lts auto it asked me auto when i was using 11.04 or whatever it was anyway i wish i'd left it alone and not upgraded.  i thought this was suppose to be a good final product.  nothing is running right after i upgraded.  i had to uninstall and reinstall synfig studio to get it to work.   gimp gave me all kinds of wierd error msgs but seems to be working now, as did inkscape but then i guess they upgraded blender recently and now it opens and takes up the whole screen i can't make that bar on the left go away.  before blender open beside the bar and worked perfectly now it opens and actually see part of the interface UNDER the bar and i can't even access it also since the upgrade i have spent countless hours trying to get HYDROGEN my other favourite ubuntu app to have sound...it opens up but no sound...it is very strange.  i can watch videos and play music ect...it's just HYDROGEN has no sound and i've tried loaded and reloading alsa and all this crap and before i upgraded to lts 12.04 i think it was using JACK but now JACK shows no device.  i have gotten it to work a few times with sound on 12.04lts but then it crashes and goes back to NO SOUND just on Hydrogen...  this is getting frustrating to me and i want to use ubuntu but the hassle is discouraging me.  i have a dell 670 precision workstation with nvidia fx1400 vid card and a great sound card.  it is very strange to me just hydrogen is affected with the sound so its something to do with alsa...i opened the mixer and unmuted turned up this that and the other and nothing is working...can someone please tell me an EASY solution to this and the blender problem.  i'm gonna have to completely diss ubuntu if i can't get these to work and i know i should have loaded studio for what i do but it was an auto upgrade and it upgraded me to precise pangolin or whatever it is lts 12.04.  please any help with these 2 main issues would be greatly appreciated....
 
kindest regards...

---

### Post by thepreecher on 2012-06-17
also i would like to subscribe to a thread and get email if someone responds...how do i do that i can't seem to find it...help please

---

### Post by thepreecher on 2012-06-17
ok i see it now..sorry..

---

