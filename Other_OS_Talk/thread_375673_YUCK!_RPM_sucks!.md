---
title: "YUCK! RPM sucks!"
date: 2007-03-04
forum: Other OS Talk
---

### Post by izanbardprince on 2007-03-04
I am playing around with Mandriva 2007 on my laptop, it's a very nice distro and performance and hardware detection are excellent.

But it uses RPM, I never recalled RPM being so bad (maybe just didn't seem so bad 10 years ago), but I get an RPM for XMMS, and it wouldn't install and kept listing dependencies for me to go fetch, so I finally added some sources to my URPMI list and installed XMMS through Add/Remove, the only problem is, that theres a separate package for every piece of it.

No wonder so many people try Linux and run back to Windows, DEB files and APT just work, RPM is terribly confusing.

---

### Post by unbuntu on 2007-03-04
RPM is like DEB in debian.  It won't sort out the dependencies for you.  Debian has apt-get and I believe RH has something called Yum(or whatever they call it) but never tried that.

Like you I don't like RPM and it was the reason I don't ever go back to RH/Fedora after I used Debian.

---

### Post by Somenoob on 2007-03-04
deb is far better.

---

### Post by Iandefor on 2007-03-04
> **unbuntu said:**
> RPM is like DEB in debian.  It won't sort out the dependencies for you.  Debian has apt-get and I believe RH has something called Yum(or whatever they call it) but never tried that.

Like you I don't like RPM and it was the reason I don't ever go back to RH/Fedora after I used Debian. dpkg does have a number of advantages over RPM, but RPM is totally in a position to not suck. To the best of my knowledge, the problems people have with RPM stem from inconsistent packaging policies across distros and not from RPM itself. 

RE Dependency resolution, you can get apt specially modified to work with RPM (it's not half bad, either) and SMART, while still under development, is still eminently usable. There are [others]("http://en.wikipedia.org/wiki/RPM_Package_Manager#Frontends") floating around out there, too.

---

### Post by Vytas on 2007-03-07
I also dropped RedHat/ Fedora because of RPM system. Maybe I just wasnt good at mastering yum wonders, dunno... Later I used Gentoo, Arch, Ubuntu etc and all these distros had some kind of decent package management... but not RPM ones.Now I settled on Ubuntu, because Arch gnome packages sometimes are (maybe only _were_?) broken, and Gentoo requires lots of time to get the most of it.

---

### Post by kazuya on 2007-03-08
for rpm-based, try pclinuxos. you would be amazed.it uses synaptic like the debian-based distros and handles installation of rpms very well.

I still favor debian-based and slack-based distros though.

---

### Post by igknighted on 2007-03-09
> **kazuya said:**
> for rpm-based, try pclinuxos. you would be amazed.it uses synaptic like the debian-based distros and handles installation of rpms very well.

I still favor debian-based and slack-based distros though.

Eww, slack packages?  Theres like 600 of them... how does that compare to 20,000 Fedora rpm's?  And Fedora handles dependencies automatically.  I still prefer portage, but debs/rpms are pretty much the same in my mind.  Deb's are quicker and a little easier at times, but rpm's handle multi arch systems which deb's cannot, so it's a wash.  I hate slack packages, they are pointless.  Slack is a neat distro, but not very useful IMO because of package issues.  I haven't tried conary or any of those fringe package managers, so I'll withhold judgment there.

---

### Post by kazuya on 2007-03-13
I disagree with slack packages being only 600. There maybe some apps on Fedora that might not be in a slack system by default, but the apps are there. Slackware by itself does not or did not have a simple package manager gui like debian or pclinuxos, but the slack-based distros like vector linux and zenwalk, etc, do. Go to linuxpackages.net or slackyit. You would see what I mean. Zenwalk and Vector linux have netpkg and gslapt respectively. In addition, you can install applications from one slack-based distro to another.

Give me some apps you run on Fedora or Debian or Ubuntu that I cannot get to run easily on slack-based system like Zenwalk or Vector Linux. I'm sure there are some. Moreover, I have never had a dependency issue that was not easily corrected compared to those from some of the bigger distros. Fedora is one of the guilty distros that used be be plaqued by dependency hell. Maybe this is changed now.

Sure Fedora may have alot more packages, slack to me has every apps and more than I can handle. Granted Ubuntu, Debian, Pclinuxos, Fedora, etc, may make them more easily accessible. The quality of slack packages are sometimes better because they are leaner and less bloaty. They do not try to pull all of kde when I just want amarok, etc.. Try it out and you may think differently. 

On another note, I know Fedora core 6 was a big step better than the previous ones. I shall experiment and may think differently. Slackware itself needs to incorporate some the package management system of its smaller derived distros.

---

### Post by Lord Illidan on 2007-03-13
> **kazuya said:**
> I disagree with slack packages being only 600. There maybe some apps on Fedora that might not be in a slack system by default, but the apps are there. Slackware by itself does not or did not have a simple package manager gui like debian or pclinuxos, but the slack-based distros like vector linux and zenwalk, etc, do. Go to linuxpackages.net or slackyit. You would see what I mean. Zenwalk and Vector linux have netpkg and gslapt respectively. In addition, you can install applications from one slack-based distro to another.

Give me some apps you run on Fedora or Debian or Ubuntu that I cannot get to run easily on slack-based system like Zenwalk or Vector Linux. I'm sure there are some. Moreover, I have never had a dependency issue that was not easily corrected compared to those from some of the bigger distros. Fedora is one of the guilty distros that used be be plaqued by dependency hell. Maybe this is changed now.

Sure Fedora may have alot more packages, slack to me has every apps and more than I can handle. Granted Ubuntu, Debian, Pclinuxos, Fedora, etc, may make them more easily accessible. The quality of slack packages are sometimes better because they are leaner and less bloaty. They do not try to pull all of kde when I just want amarok, etc.. Try it out and you may think differently. 

On another note, I know Fedora core 6 was a big step better than the previous ones. I shall experiment and may think differently. Slackware itself needs to incorporate some the package management system of its smaller derived distros.

Banshee was a bit of a nightmare to get installed, but anyway... no distro has matched Ubuntu so far on package management in my experience.

---

### Post by igknighted on 2007-03-14
> **kazuya said:**
> I disagree with slack packages being only 600. There maybe some apps on Fedora that might not be in a slack system by default, but the apps are there. Slackware by itself does not or did not have a simple package manager gui like debian or pclinuxos, but the slack-based distros like vector linux and zenwalk, etc, do. Go to linuxpackages.net or slackyit. You would see what I mean. Zenwalk and Vector linux have netpkg and gslapt respectively. In addition, you can install applications from one slack-based distro to another.

Give me some apps you run on Fedora or Debian or Ubuntu that I cannot get to run easily on slack-based system like Zenwalk or Vector Linux. I'm sure there are some. Moreover, I have never had a dependency issue that was not easily corrected compared to those from some of the bigger distros. Fedora is one of the guilty distros that used be be plaqued by dependency hell. Maybe this is changed now.

Sure Fedora may have alot more packages, slack to me has every apps and more than I can handle. Granted Ubuntu, Debian, Pclinuxos, Fedora, etc, may make them more easily accessible. The quality of slack packages are sometimes better because they are leaner and less bloaty. They do not try to pull all of kde when I just want amarok, etc.. Try it out and you may think differently. 

On another note, I know Fedora core 6 was a big step better than the previous ones. I shall experiment and may think differently. Slackware itself needs to incorporate some the package management system of its smaller derived distros.

The issue in many cases is getting the packages.  Sure, in Zenwalk I can sort through 6 different repo's, all with different software and I have to guess what each one has.  In slack, I need to browse the web to get packages... Yuck, is this windows?  And I never feel safe that Slack will help me sort out dependency issues.  Honestly I never spent enough time on it to be sure (at least time once I was skilled enough to understand dep. hell), but the overall process with Debian and RPM is much nicer.  If I wanted to do like slack and browse the web I would download source and install that way.  I really think that some central package handler is a requirement in a modern distro, be it APT or Yast2 or YUM or whatever.  As I have said before, I like Portage/Emerge.  It allows the most power over the install, leaves you with programs compiled for your system, and once you learn the basics it's easy as pie.

---

### Post by kazuya on 2007-03-14
In light of these, I cannot disagree with you guys. The packages that come with the repos work for the most part via netpkg for zenwalk. But I do agree that sometimes installing certain apps from linuxpackages may fail due to some dependency not being on that package. Most work fine. I have seen issues in the past with superkaramba, mplayer, amarok, vlc.. These are getting resolved now as these little distros are starting to contribute back to main slack package places. 

I like the other guys with excellent package managers, but most of these tend to be slower in performance than the slack-based distros. But in all, they are starting to win me over again. 
In the end, it all comes down to what the OS user requires and how much the distro caters to their needs.

---

