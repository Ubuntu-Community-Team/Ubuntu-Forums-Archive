---
title: "nvidia"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by BrettWilkin on 2008-10-28
3 weeks ago I bought an acer amd 64 to set up as a stand alone media centre. I was sold on the idea by a friend and a video expounding the virtues of MCE. I also wanted to show the 120 computer owning students I teach there is another life other than Microsoft. I downloaded kubuntu 8.04.1 and deleted my OS. I then struck a problem with the nvidia card (9300Ge). When I tried to restart the computer it stopped and I could not get it to restart. I reloaded Kubuntu and tried with a full upgrade that took about 25 hours on my broadband connection. I then loaded the recommended graphic  driver. Restarted the computer and it stopped in the same place. I started reading linux forums and then reading google searches to understand the bits the linux techies keep forgetting to tell you. I then decided on a long shot and downloaded MCE as a cd to see if it dealt with the graphic drivers better. Cd’s corrupt. I then spent 2 days downloading the dvd. Hmm corrupt as well. 2 weeks later and several reloads, I updated to 8.1 to see if the update would deal with the graphics card. The updated package was great to look at I loaded the recommended drivers tried a movie, listened to some music and thought at last my media centre may be a reality. Switched off for the night very happy. Next day switched on and everything died at the same spot. I have tried as many of the fixes I can understand from the forums and tried everything I can think of to get the system going. I am now at the stage where I have to spend another heap of money to replace the operating system I deleted. Now I have spent a day just trying to find where I submit a post on the forums to try and get help I tried one post and it told me I was not allowed to submit, it did not tell me where to submit. So far I have only found what I am not allowed to do not what I can. The question now I ask, is this an elite project simply for computer programmers or is it a credible project to bring open source software into the realm of the non elite general public. I applaud those that do give up their time and energy to work on these types of projects and I would dearly like to be a part of something that can bring computers into the lives of those who cannot afford the expensive software available. Is there someone who is willing to assist me or do I give up and go back to writing visual basic for my databases. 
Regards from Brett Wilkin

---

### Post by roger_1960 on 2008-10-28
Hi Brett

Sorry your getting so frustrated!  This is probably the right place to get a solution.

It sounds like 8.10 may be the right way to go.  The stable release is due any day now.

In order to get some sensible help, it would be an idea to post the hardware specs for your PC and as much info as you can about where you get to when trying to boot.

Which version (exactly) are you trying to run?

---

### Post by Kellemora on 2008-10-28
Hi Brett

I have good news and bad news both!

I'll give you the bad news first, then what might work.

I also owned an ACER laptop, they leave parts off the motherboard or should I say, they only install the minimum necessary components to run the OS THEY supplied with that laptop.  In other words, I could NOT even upgrade the Windows OS as it needed things the motherboard didn't have.
Sent it into the shop and all they did was reload the original OS and added a note, "Designed for installed OS ONLY, Do Not Change or Upgrade".

My first question is, did you properly BURN the .iso file?  
You cannot COPY it to a CD or DVD, you MUST burn it as an .iso file.
If you can open the CD and see an .iso file on it, you did not burn it correctly.

Once you do get the Ubuntu version up and running, you can go to Synaptic package manager and check on EnvyNG-gtk and download it, then after it downloads, reboot, then select EnvyNG and open it, usually it will find the exact Nvidia card you have installed and install the drivers for it.

Nobody told me this before either, but I tried it, and although it appears to be the same driver as before, things work now that didn't work before, but not all the effects I had hoped for.

TTUL
Gary

---

