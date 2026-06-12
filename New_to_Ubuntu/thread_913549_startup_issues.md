---
title: "startup issues?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by jpcrow on 2008-09-07
hello! 

This morning I installed xubuntu onto my PS3. Don't let that scare you off please. Almost all of the help I've found about this install (this is my second machine to install ubunto to, other was a laptop, but i'm still a noob who knows how to copy and paste into terminal lol) has been found on general ubuntu forums not the psubuntu ones... but anyway, pretend the following is happening to you, what would you do?

I have to type 'sudo dhclient' every time that I reboot in order to get wired internet to work. Also the CD rom isn't recognizing a CD with an .avi file on it, i put the CD in and nothing happens, isn't that weird, what should I do? I haven't tried any other CDs yet but will soon, if you need more info let me know.

I'm asking here because when I installed on my laptop you guys helped me out so much so maybe you can help me here too.
Thanks,

jpcrow

*** oh, I almost forgot to ask how to install flash player, you tube won't work and it says I need flash, figured that would be a big deal for looking at web pages in the future

---

### Post by pikabuntu on 2008-09-07
for the flash plugin, type this into the terminal:

sudo apt-get install flashplugin-nonfree

I think [http://psubuntu.com/](http://psubuntu.com/) has a lot of good info about psubuntu.

---

### Post by jpcrow on 2008-09-07
I've been surfing psubuntu all day, their forums are sub-par and the advice is not as nearly as clear as the info I've gotten here.

That said, I did find some info there, its just not nearly as complete as what the people here can do for me.

---

### Post by Xiong Chiamiov on 2008-09-07
> **jpcrow said:**
>  but anyway, pretend the following is happening to you, what would you do?

I would install Arch (my current favorite distro) so that I could have some control over it.  I would then spend several weeks trying to solve a problem that really was my fault, and in the end, be smarter and have things working just the way I want.

It just seems to me that *buntu is an odd choice for something like a PS3, where you need to easily have control over all the little bits of things.  I more see people running Gentoo or Slack on it.

---

### Post by jpcrow on 2008-09-07
sudo apt-get install flashplugin-nonfree returns this line:

Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate

what have I done? Have I not opened up a repository somewhere?

---

### Post by jpcrow on 2008-09-07
Also, putting "sudo dhclient" in /etc/rc.local fixed the having to type it into terminal every reboot.

I chose xubuntu because it was simple to install, light and reasonably user friendly. I thought it was a decent choice but I guess I could see how it could garner some amount of criticism.

But its working well so far, just some small issues... I try to stick with the *buntu because seems to be about my speed, maybe after I've had some more hands on and I've learned a bit more I'll try Slackware or something a bit further up the learning curve.

---

### Post by Xiong Chiamiov on 2008-09-07
If you have access to a GUI, I think you'll have to [enable some repositories]("http://www.psychocats.net/ubuntu/nonfree").

And by no means start off with Slack.  I find it good to start with the "easy" distros, then move gradually toward the "power-user" distros as you get frustrated with not having enough control.  If you're satisfied, don't change.

---

### Post by jpcrow on 2008-09-08
Does flash not work on powerpc installs? I just read on a google search something about it not working with power PC?

Also, thanks for the add/remove tutorial, it looks like I'm going to have alot of fun with that add/remove also said something about flash not working with powerpc it wouldn't even let me check it in the check box, is there an alternative?

---

### Post by mali2297 on 2008-09-08
> **jpcrow said:**
> Does flash not work on powerpc installs? I just read on a google search something about it not working with power PC?

Also, thanks for the add/remove tutorial, it looks like I'm going to have alot of fun with that add/remove also said something about flash not working with powerpc it wouldn't even let me check it in the check box, is there an alternative?

Yes, I don't think Adobe's flash plugin works with PPC. There are two open source alternatives: [gnash](http://www.gnashdev.org/) and [swfdec](http://swfdec.freedesktop.org/wiki/).

---

### Post by jpcrow on 2008-09-08
Someone has suggested I install gnome-volume-manager and put it into my autostart apps... I'm at work so I can't try it right now, but does that sound like it will be a workable solution to my CD-rom problem? 

If so could someone give me a quick and dirty rundown on how to install gnome-volume-manager and then add it to my autostarted apps?

---also, thanks for the flash links, I'll try them out tonight!

---

### Post by mali2297 on 2008-09-08
> **jpcrow said:**
> Someone has suggested I install gnome-volume-manager and put it into my autostart apps... I'm at work so I can't try it right now, but does that sound like it will be a workable solution to my CD-rom problem?

Check first if you can see the cdrom in the file manager Thunar, it should appear in the shortcuts pane when you insert a CD.

---

