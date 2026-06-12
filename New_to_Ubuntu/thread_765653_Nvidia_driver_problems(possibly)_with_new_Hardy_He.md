---
title: "Nvidia driver problems(possibly) with new Hardy Heron"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Motif31G on 2008-04-24
Ive installed the new LTS of hardy heron but cant get Compiz to work.

I go to system>preferences>appearance>visual effects click "extra" and I get "desktop effects could not be enabled"

now... ive used gutsy gibbon before and it worked fine but i admint i am new to linux.

I thought installing my nvidia driver would help(duh), so i went to nvidia site and downloaded to the latest drivers that correspond with my card (8800GTS), ran "sh NVIDIA-Linux-x86-169.12-pkg1.run" in terminal and get a " Can't open NVIDIA-Linux-x86-169.12-pkg1.run" 

in administration>hardware drivers "nvidia_new" is enabled with a red "not in use" showing...

help :(

---

### Post by glennric on 2008-04-24
Are you not able to enable the nvidia-new driver from System->Administration->Hardware Drivers?  There should be a check box you can check.

---

### Post by Joeb454 on 2008-04-24
Try moving to the directory it's saved in using the **cd** command and then typing (or copying) ```
./NVIDIA-Linux-x86-169.12-pkg1.run
```

---

### Post by glennric on 2008-04-24
I see.  I didn't read close enough.  You will have to add the line
```
option nvidia
```
to the Section "Device" part of the file /etc/X11/xorg.conf

---

### Post by Motif31G on 2008-04-24
> **Joeb454 said:**
> Try moving to the directory it's saved in using the **cd** command and then typing (or copying) ```
./NVIDIA-Linux-x86-169.12-pkg1.run
```

what is "CD"

please excuse me im a bit new

---

### Post by glennric on 2008-04-24
> **Joeb454 said:**
> Try moving to the directory it's saved in using the **cd** command and then typing (or copying) ```
./NVIDIA-Linux-x86-169.12-pkg1.run
```

You shouldn't install the drivers downloaded from nvidia.  If installed correctly they will work, but they are the same as the nvidia-glx-new drivers in the repositories (for Hardy that is).

---

### Post by mgchan on 2008-04-24
> **glennric said:**
> I see.  I didn't read close enough.  You will have to add the line
```
option nvidia
```
to the Section "Device" part of the file /etc/X11/xorg.conf

Had the same issue.  "Nvidia new" driver was Enabled (checked), but not in use, after installation.  Perhaps a restart right away would have worked, I'm not sure, but I installed the nvidia-glx-new driver from Synaptic, restarted, and compiz worked then.

---

### Post by Zralou on 2008-04-24
> **Motif31G said:**
> what is "CD"

please excuse me im a bit new

Current Directory.  i.e. the folder where the file is located.

Sara Lou

---

### Post by Motif31G on 2008-04-24
> **glennric said:**
> I see.  I didn't read close enough.  You will have to add the line
```
option nvidia
```
to the Section "Device" part of the file /etc/X11/xorg.conf

ok going to need a better example
i see

"Section "Device"
	Identifier	"option nvidia"


where exactly do i add?

---

### Post by Motif31G on 2008-04-24
it seems im having trouble installing other things as well

in terminal when ever I try to install i get

E: Couldn't find package blah

---

### Post by jtrink on 2008-04-24
how exactly do you install the: 

"nvidia-glx-new driver from Synaptic"

I know what the synaptic package manager is, but I am new to linux and am having the same driver problems with my 7600GT. They are "enabled" but "not in use", can anyone help me please?! :confused:

---

### Post by jtrink on 2008-04-24
anyone? When i search for "nvidia" in synaptic, like only 3 things come up?

---

### Post by doodio on 2008-04-24
I had the same problem on my Dell M1330 laptop with nvidia 8400M GS card.

Fixed it by downloading envy-NG, works great now, and is enabled after installation.

---

### Post by jtrink on 2008-04-24
soudns like a stupid question, but how do i install envy-NG?

---

### Post by YonyonJohn on 2008-04-24
I'm having the same problem. no amount of enabling / disabling / rebooting will fix it. here is a screen shot of the problem:

[IMG]http://i31.tinypic.com/13z1bp.png[/IMG]

---

### Post by jtrink on 2008-04-24
haha yeh man, I'm getting the exact same thing and have no idea what to do. Someone please help us!!! lol.

---

### Post by oldsoundguy on 2008-04-24
most likely you need to activate the repositories under system> administration> software sources.

---

### Post by jtrink on 2008-04-24
jsut all the "universe" ones?

---

### Post by doodio on 2008-04-24
ok guys, from what I can tell, that's the exact same problem I had!!!!

All I needed to do to fix it was make sure repositories were turned on in Synaptic, and mine were turned on by default.

Make sure you select a server that's working properly, a lot of them are being hammered, the Canadian ones seem to be working.

guide is here:
[http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)


Brief summary:
Open Terminal, and type:
sudo apt-get install envyng-gtk

If the servers are working correctly and you're connected to the internet it will download and install all automatically and let you know when it's done.

Then:
4) Launch EnvyNG's GUI (inside a Desktop Environment such as GNOME,KDE, etc.) by selecting it in the "Applications/System Tools" menu

From there, select Nvidia and install, It'll reboot for you and desktop effects will be working!
You'll notice an immediate difference.

good luck!

---

### Post by Victormd on 2008-04-24
> **jtrink said:**
> soudns like a stupid question, but how do i install envy-NG?

If you're using Hardy (8.04), go to System>Administration>Synaptics Package Manager

In Synaptics, go to Settings>Repositories and open the Updates tab. There, mark the first four options (Important Sec... Recomended... Pre-releas... Unsupported...) close and click on the Reload button

Then, search for envyng and 3 options should come up. If you're using Ubuntu, install the envyng-gtk. If you're using Kubuntu, install the envyng-qt. Once installed, the program will show under Applications>System Tools.
Run the program and it should install the driver properly.

Another option, is, if you don't want to use Envy-NG, you can search for nvidia-glx-new in Synaptics and install from there, it's the same driver.

If you're using Gutsy, then you can download Envy-NG from
[http://linux.softpedia.com/get/System/Software-Distribution/EnvyNG-36961.shtml](http://linux.softpedia.com/get/System/Software-Distribution/EnvyNG-36961.shtml)

---

### Post by QUEEN HIPPOLYTA on 2008-04-24
Try installing Envy from the repositories. I had issues with the nvidia driver and this cleared it right up.

---

### Post by grover66 on 2008-04-24
Installing the nvidia-glx-new driver worked for me;

```
sudo apt-get install nvidia-glx-new
```

Reboot after installing it, then you can enable it correctly.

Mike :)

---

### Post by bobbybobington on 2008-04-24
installing the nvidia-glx-new driver from synaptic fixed the problem. THANK YOU!!!1 :guitar:

---

### Post by YonyonJohn on 2008-04-24
hey everyone, I figured it out!

here's how to get it working:

1) enable all the repositories
     * go to system > administration > software sources
     * check all boxes under downloadable from the internet
     * go to the third - party software tab and check both boxes (this step may not be necessary)
     * click close and reboot

2) update repositories
     * go to system -> administration -> synaptic package manager
     * click reload in the top left (this will take a while, make sure you let it finish)
     * close close synaptic package manager and reboot

3) install drivers
     * go to system -> administration -> hardware drivers
     * the enabled check box should now be un-checked
     * check the enabled check box next to the driver you are having problems with
     * click enabled on the window that will come up
     * reboot


that should fix it, not bad for a linux noob huh? :)

---

### Post by jtrink on 2008-04-24
I'm trying to reload the repositories in the synapic package manager and some file is listed as failed. "translation...file"

---

### Post by djowtlawz on 2008-04-24
Here is what worked for me

sudo /etc/init.d/gdm stop
cd /<nvidia driver directory>
sh NVIDIA-Linux-x(version here)- pkg1.run
sudo /etc/init.d/gdm start

And you should be okay

---

### Post by jtrink on 2008-04-24
nm yonyonjohn's method worked for me, thanks dude. Thanks everyone that has replied to this thread! As I was browsing for a solution I saw a lot of people were in need of this solution... Someone needs to mark this thread as solved!

---

### Post by Ch3F on 2008-04-25
Hello All.  I am a completely new user to ubuntu (8.04) and linux in general.  I installed ubuntu on a seperate partition, am able to select it in the boot menu and i can only get as far as a command prompt.  The graphical ubuntu loading screen will end up spitting hardware errors back at me, same for video safe mode and all the other options too.  I have an 8800gts (G92) and I have been told by a local linux guru that this is my main problem.  Note i need to fix this from command prompt (to start).  Any suggestions?  He wants me to setup my box so he can log in remotely and literally do it for me while he's at his box but I really want to troubleshoot this from my end initially so I can learn :)  Thanks for any replies.

---

### Post by slugg0 on 2008-04-27
Hey Ch3f, I personally would never ever give anyone access to any of my computers.. Just not a good idea from a security standpoint. Not even my close friends who who I trust and have been using Linux for years with me. 
My suggestion is to paste the errors in a thread here somewhere or search the forum for your video card to see if others are having the same problem or if there is a fix for it. Also you might want to check out the forums at NVidia as they will have help as well. Good luck! :)

---

### Post by slugg0 on 2008-04-27
Ch3f, something that I thought of.. I am not sure if your problem is a NVidia driver issue from what you have said. Does Linux try to start X and then drop back to the command prompt after failing or does it not get that far? If it doesn't get that far, then it isn't a NVidia problem. If it does, and spits out errors like (E) NVidia blah blah then it is a NVidia problem. Either way, I would post your errors here. It will help us help you and then you can do it yourself and learn something like you want to! :) Have a great day!

---

