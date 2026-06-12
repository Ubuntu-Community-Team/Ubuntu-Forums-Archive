---
title: "Ubuntu Desktop Convergence Updates?"
date: 2015-02-04
forum: New to Ubuntu
---

### Post by xixor2 on 2015-02-04
Fellow Ubuntu Community members,

Somewhat new ubuntu user here. Recently became interested in the concept of desktop convergence. Have become extremely confused and frustrated trying to get information regarding the subject. 

First, what I mean by "desktop convergence" - basically installing an operating system on a smartphone (I have a nexus 4, but would be willing to buy a newer model), and being able to plug the smartphone into a monitor or TV, and have a full "desktop" experience - basically using the smartphone AS a desktop PC, thus eliminating the need for separate PC hardware. I imagine something where when just using the phone, the desktop and software would be skinned to work nicely on a small screen with touch functions, but when plugging an HDMI cable into a monitor, it would automatically switch over to the standard desktop environment. Connect a keyboard and mouse via bluetooth and you have a (hopefully) fully functioning computer.

Two main problems I have been encountering:

1) When searching for information on this topic, I can't seem to find ANY information newer than about August of 2014. There seem to be a lot of articles back from early 2013 on the subject talking about something being rolled out by mid-2014, but things seem to have gone quiet in the mainstream media. I am probably just looking in the wrong places.

2) I (and others) seem to be confused about the differences between Ubuntu for Android (with supposedly the desktop convergence feature), Ubuntu Edge (some kind of concept phone with this feature), and Ubuntu Touch (confused about whether or not this is the same operating system as regular ubuntu desktop just skinned to work with smaller screens - wikipedia page says it does have the desktop convergence feature). Sometimes when I read an article mentioning desktop "convergence" or smartphone "docking", I am not quite sure what they are referring to.

So can anyone enlighten me as to the current state of this technology here in February of 2015? Does this exist yet? Is the hardware in a Nexus 4 robust enough to do this? I imagine the constraints of this type of scenario are more software based than hardware based though, correct?

Thanks!

---

### Post by ian-weisser on 2015-02-04
> **xixor2 said:**
> So can anyone enlighten me as to the current state of this technology here in February of 2015? Does this exist yet?

Yes, most of it exists.
Ubuntu for Devices and the normal desktop/server version of Ubuntu will converge during the next year. or so. The resulting converged OS will still be called 'Ubuntu'. On phones, it will look at lot like Ubuntu for Devices. On a desktop, it will look a lot like the current desktop. Phones that can handle a keyboard/large-display will show the appropriate interface on the appropriate screen.

See [https://developer.ubuntu.com/](https://developer.ubuntu.com/) for how to install Ubuntu for Devices on your Nexus.

See [https://unity.ubuntu.com/getinvolved/development/unity8/](https://unity.ubuntu.com/getinvolved/development/unity8/) for Unity 8, the converged user interface. 

See [http://www.youtube.com/user/UbuntuOnAir](http://www.youtube.com/user/UbuntuOnAir) for the twice-monthly engineering updates on convergence.

There are many other sources, but these should get you started. You won't find fancy status reports and press releases - you will find geeky details by the developers and engineers updating features and bugs for their peers.

Ubuntu on Android was a proof-of-concept project, now completed, that led to the current convergence project.

Ubuntu Edge was a demonstration of demand for the OS in mobile markets, now completed, that led to current partnerships with several handset makers. Those handset makers plan to introduce phones running Ubuntu for Devices during 2015. Future phones (or updates) will replace Ubuntu for Devices with normal (converged) Ubuntu.

---

### Post by xixor2 on 2015-02-04
Awesome information, thanks!

---

### Post by grahammechanical on 2015-02-04
There are two Original Equipment Manufacturers (OEM) who are about to bring out a Ubuntu phone. A Spanish company called BQ will be releasing a Ubuntu phone in a couple of weeks. This coming Friday there is a meeting in London, UK, where a few privileged individuals will be given pre-release samples to review in time to blog about the BQ Ubuntu phone by release day. No date given yet. And then there is a Chinese company called Meizu but we have yet to get any release dates from them. But they have been indications that the code is complete and ready for OEMs to make use of.

If you go to ubuntuonair.com there are videos demonstrating progress. Every week there is a Community Q and A where we get updates about what is happening in Ubuntu and an opportunity to ask questions. And every two weeks there is Ubuntu Engineering Live, which is similar.

The plan was to first create an OS and user interface for the phone based upon the existing Ubuntu code base. Next, to modify the code and apps to scale to tablet devices and then converge it into the desktop code so that there is one Ubuntu code base that will have a phone UI when installed on a phone, a tablet UI when installed on a tablet and our familiar desktop UI when we install it on our desktops and laptops.

This is not Ubuntu squeezed into a phone with a phone OS skin. The Ubuntu for Devices has been built from the ground up. Apps have been written for it. It runs on a new display server called Mir and Unity 7 has been re-written to run on MIr. That is why it is called Unity 8. A lot of emphasis has been put into making the phone secure. 

There are three ways to track convergence on desktop Ubuntu.

1) Install unity8-desktop-session-mir. We get a login screen options and we can see the progress being made in making the phone UI run on the desktop and eventually gett the usual Ubuntu desktop applications running alongside the phone bits and pieces.

2) Install Ubuntu Desktop Next ISO image in its own partition and dual boot into it.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/20150204/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/20150204/)

3) Install Unity 8 in an LXC container. That will also give a login option.

[https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

The biggest bug is that we cannot log out of Unity 8 in any of these three methods. We have to use the terminal to shut down or reboot. Or even power off.

Regards.

---

