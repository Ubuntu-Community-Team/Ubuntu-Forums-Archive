---
title: "Using nvidia proprietary graphics driver and Nvidia GPU"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by misternumberone on 2014-01-31
Hi, I'd like to use the nvidia proprietary driver so that I can access the graphics hardware settings that no open-source driver seems to be able to and use my Nvidia GPU for everything. 

The problem is, I tried to install it before in a variety of forms and ways including many different versions and through many different combinations of applications, and every time, even under absolute clean installs, things would boot normally but my x would randomly freeze every few minutes so that I couldn't do anything. The only temporary solution I found to that was to use ctrl+alt+f# to go to a tty and then use ctrl+alt+f7 to go back to x, which would unfreeze it as though nothing had happened, though processes not using x would still have been running. Then a few minutes later x would freeze and I'd have to do that again.

I tried to install bumblebee in an attempt to use only my Nvidia GPU, which is installed for Optimus, but when bumblebee was installed my x would not start; every time I'd boot ubuntu it would show just a white box with "The system is running in low-graphics mode; your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself." The cursor would also not be visible until I would move it blindly over the text; then I'd get a black X cursor with which I could click the OK button in the white box, but then after the next screen everything would just go black and I wouldn't be able to do anything from the x screen. This stopped only when I completely removed bumblebee via a tty. 

Eventually I completely purged all proprietary nvidia drivers and bumblebee because I couldn't get them to work right. However, that's left me without knowing what GPU I'm using at a given moment at all, and I'm currently having a problem with an OpenGL application that seems to tell me it's running on my Intel GPU and which crashes seemingly in some way because of that. Therefore, I want to use my Nvidia GPU with it, and preferably for everything else as well, ignoring the Intel as much as is possible with the display probably connected to it, but I don't know how.

I'm using Ubuntu 13.10 with Linux kernel 3.11.0-17-generic on an ASUS A53SV laptop with an Intel Core i7-2630QM with Intel GMA HD 2000 and an Nvidia GeForce GT 540M that's installed for Optimus (It's not connected to the display, I don't think, but on windows it can be told to run all applications through settings in the driver interface). I think I'm using the open-source i915 driver for my Intel GPU and the open-source nouveau driver for my Nvidia GPU, but I'm not sure. Please let me know how I can post any additional needed information! :-o
 
I've tried so many things to use my Nvidia GPU and only my Nvidia GPU that I can't remember all of them, but I'd really love to be able to do this. I don't know how well simply bumblebee, if it would even have worked, would do, as it seems that I'd have to use its command every time to run anything with the Nvidia GPU, and that really would be tedious. Probably the thing that bothers me the most about UNIX is the complete abscence of any unified hardware management interface. Call me a GUI junkie, but having to use many different commands with countless operands and pure text onscreen to do something that'd be very simple and efficient if a GUI application were available is painful. Just look at managing installed integrated programs with the command line vs with a package manager like synaptic and the Ubuntu Software Center. Of course, I can't expect anywhere near the levels of performance, efficiency and driver configuration that I can get with my laptop using Windows and the support manufacturers provide for it, but at the very least I'd like my hardware's performance. Graphics and audio performance is something I always have difficulty with on open-source operating systems, and I think that might be due to the things the hardware manufacturers seem to implement at higher levels.

Please feel free to tell me how silly I am or to RTFM; I'm willing to try any existing post or guide that I in my gross laziness have neglected to find so far. I'm a bit afraid to do any more of what I've tried before, such as additional drivers (jockey) and bumblebee, as I don't want to break my x and have to try to fix it through a tty again. :neutral:

---

