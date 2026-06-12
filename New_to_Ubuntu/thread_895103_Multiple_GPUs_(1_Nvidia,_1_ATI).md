---
title: "Multiple GPUs (1 Nvidia, 1 ATI)"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-08-19
I built a system as a htpc and am having trouble with the integrated graphics. It's the 780g chipset which has a ATI HD3200 integrated, which should be able to play all sorts of HD video, but I'm having frame-rate problems. One of my friends is letting me test his Nvidia 8600GTS to verify that it is a GPU problem. I am trying to run some benchmarks, but am having trouble switching between the cards. I would like to use the proprietary drivers and be able to switch between cards (w/o rebooting would be nice). Both cards are recognized, but when I try to install the drivers for the ATI card (installed the 8600gts with no problems first), I get an error that says> There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages.

Thanks.

---

### Post by nicedude on 2008-08-19
I don't think you can switch between graphics cards while running without a reboot, but I could be wrong. Even if I was and there is some way to do it, I would say it still wouldn't be the best way to benchmark as that would be to disable your onboard graphics in the BIOS and boot with the Nvidia and test and then remove the Nvidia card and turn your onboard back on in your BIOS and test it. That way you insure you get results that in no way are effected by the other adapter. 

As far as your ATI onboard graphics what graphics driver are you using? If it is the one automatically loaded by Ubuntu then it might not be the best one. For an easy attempt at a better driver I would recommend using envyng to do it for you, and for a little harder way would be to get the newest ATI linux driver package and install it. Below I will list the command to install envyng and a GUI frontend for it in one command that if you paste into a terminal window and run will install it. Then go to Applications -> System Tools -> Envyng to start it up and then pick ATI and install driver and it will do it all for you, When it asks if envy should configure your xorg.conf file for you hit yes and let it.

HERE IS THE COMMAND TO INSTALL IT
sudo apt-get install envyng-gtk

Hope that helps you out, and good luck

---

### Post by jbrown96 on 2008-08-20
Thanks for the suggestion. The problem is that the ATI driver will not install. It seems that the problem is caused by an error in removing the nvidia-glx-new package, but I don't want to remove that package. I want to find a way to add graphics cards, so that I don't have to remove any drivers to reinstall the other card.

---

### Post by nicedude on 2008-08-20
Why would you need nvidia-glx-new if you use a ATI onboard video chipset? If you had a proper ATI driver installed and working you should be able to watch HD video and have 3D desktop & compiz fusion as well. You shouldn't have jerky playback or any other troubles such as you describe and I think this is due to not using the best driver. The standard Ubuntu Nvidia driver worked like crap for my card and once I installed the latest one direct from Nvidia all problems with my graphics were solved. Hell I can open 4 movies at once and stick them one each on the 4 faces of my compiz cube effect and spin it around and they don't stutter, with the original driver I couldn't even enable desktop effects.

---

