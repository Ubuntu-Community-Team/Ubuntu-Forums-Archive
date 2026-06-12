---
title: "GoboLinux"
date: 2007-07-29
forum: Other OS Talk
---

### Post by fistfullofroses on 2007-07-29
Polished Linux distros get boring (for me) very quickly, and I generally dislike them for the amount of complexity and bloat they tend to come with. Slackware has a special place in my heart for that reason. Very little bloat if you so wish, and extemely simple. I use Ubuntu on and off, but everytime just get frustrated with it. It does have it's partition though. Recently in a bout of boredom, I decided to try Gobo.

The install was easy enough. Different from most, but nicely put together. After the install, when I rebooted... dismay. Nothing seemed to work properly except for the command line.

So, that is where I started (obviously). During boot alsa said it failed. No amount of tinkering seemed to get it working. Whatever. Just to make sure the beast was not functioning I kicked it... err... tried to play an ogg with ogg123. Failure. Ok whatever. I put it on the back burner. I then decided to try and get X working. First I tried that Ati card. No luck. Both the ati driver, and fglrx driver would not function. Then I tried the Nvidia card. No luck as well. So, I commented out half of the xorg.conf file, and switched the driver to vesa, and set the resolution down to 800x600 and voila KDE loaded... with sound. Hmm, ok. So then I decided it was time to install udev, HAL and everything else. This all worked well enough, and reminded me quite a bit of Slackware. The package manager "Compile" was about as good as netpkg or slapt-get. It would get you the most common packages, but occasionally fail on a dependency. That wasn't all that bad really. Used to it. So then you can use compile to install that specific package. That works sometime too. If it doesn't hunt down the source do a ./configure - make - make install and poof re-run Compile for the original package and keep on truckin'. The best thing about Gobo was speed. Gobo was by far the fastest Operating System I have ever seen. Vector (which touts about being fastest) was a turtle in comparison. Over all it isn't a bad system. 

Good points:
Easy to find anything and everything because the directory hierarchy is sweet.
Fast as lightning.
Extremely simple configuration files and scripts that are well commented.

Bad Points:
Buggy.
I hate KDE.
zsh instead of bash for a default shell.
I hate KDE.
Perl-XML-Parser is wunky.
I hate KDE.

---

