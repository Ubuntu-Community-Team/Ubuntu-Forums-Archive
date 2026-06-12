---
title: "Failed to install Pantheon DE on Ubuntu 18, screwed up along the way"
date: 2018-05-14
forum: New to Ubuntu
---

### Post by bad-and-ugly on 2018-05-14
Hi everyone [=

I just got this old Macbook (from 2010) and installed Ubuntu 18 (single boot). I wanted to use Pantheon desktop environment (from elementary OS, based on Ubuntu). I followed several different instructions online, none of which worked - they were basically adding repos and installing things I guess? (and when I say it didn't work I mean I can't find the button to switch DE at login screen).

But that attempt messed with my repos. I thought they would just add a bunch of repos but they might have replaced some of the default ones. And I might have fixed that actually (how do I even check?). But now this computer thinks I'm running elementary OS 5.0 Juno. Look, this is what it said before:

> 
##### release ########################### Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, nomodeset, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

And now look what it says

> ##### release ###########################

  

 Distributor ID: elementary
 Description:    elementary OS 5.0 Juno
 Release:    5.0

 Codename:   juno

  
 ##### kernel ############################
  
 Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
  
 Parameters: ro, nomodeset, quiet, splash, vt.handoff=1

  

 ##### desktop ###########################

  

 Ubuntu

Now I'm having problems installing things. When I try to install Ruby (by running $ rvm install 2.3) look at some of the things I get:

> No binary rubies available for: elementary/5.0/x86_64/ruby-2.3.4.
Continuing with compilation. Please read 'rvm help mount' to get more information on binary rubies.

and this error here:

> 
There has been an error while updating your system using `apt-get`.
It seems that there are some 404 Not Found errors for repositories listed in:

    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list

Make sure that all repositories are available from your system and verify your setup by running manually:

    sudo apt-get update

Make sure that it works correctly before proceeding with RVM.

If you are working from the GUI instead of the terminal, you might want to verify and fix broken
repositories using "Software & Updates" application.

.......
Error running 'requirements_debian_update_system ruby-2.3.4',
please read /home/ministrador/.rvm/log/1526270790_ruby-2.3.4/update_system.log
Requirements installation failed with status: 100.

It's terrible. I feel like reinstalling everything, or going back to Mint xfce because I think it looks better, but it was such a hassle getting WiFi to work in this computer (thanks to wildmanne39, I managed that today! after a week) that I'm afraid it'll happen again. Do you know a way to fix repos/system information so I can install the things I need and move on with my life? I'm installing Ruby and this stuff because of webdev course called Odin Project, it's wonderful. ):

---

