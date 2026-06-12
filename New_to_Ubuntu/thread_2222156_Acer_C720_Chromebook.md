---
title: "Acer C720 Chromebook"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by ToraxOutlaw on 2014-05-05
Hey guys, I've just installed Ubuntu 14.04 on my Chromebook, I've got the brightness, volume keys and bluetooth working, unlike my C710 which had some issues but other than that it worked. Now the issue I'm having with the C720 is that it won't connect to any open WiFi network if it requires a login page or my Galaxy S4 hotspot, it just keeps saying DNS Lookup Failed. I can connect to my home WiFi with no problems. My other devices and the Chrome OS portion of the C720 can connect to any open network and my Galaxy S4 hotspot with no issues. Any ideas on how I can remedy this?

---

### Post by TheFu on 2014-05-05
```
rfkill list
rfkill unblock {something-from-the-list}
sudo wicd-curses
```

Don't know if this will help, but it works here on my C720.

---

### Post by pdc on 2014-05-05
> ubuntu DNS Lookup Failed

is there anything here of help?

[http://askubuntu.com/questions/116408/ubuntu-10-10-dns-lookup-failed](http://askubuntu.com/questions/116408/ubuntu-10-10-dns-lookup-failed)

[http://ubuntuforums.org/showthread.php?t=1844336](http://ubuntuforums.org/showthread.php?t=1844336)

---

### Post by ToraxOutlaw on 2014-05-06
I'll try your suggestions gentlemen, and I will post back my results shortly.

EDIT: I tried both your solutions, The first one I got back was command not found for (sudo wicd-curses) and setting my own DNS servers was no help, I still can't connect to my Galaxy S4's hotspot.

---

### Post by pdc on 2014-05-06
wicd-curses - is a curses-based wicd(8) controller (so maybe the command was intended to be a command to install it .........but you might need a set of instructions)

I suggest you post anew on the wireless forum: that is the place to ask about your issues

---

### Post by ToraxOutlaw on 2014-05-06
This is why I posted here, I'm an expert when when it comes to Windows issues, but with Ubuntu I'm a greenhorn. I'd like to resolve my query, so what are these instructions that I could be looking for?

---

### Post by ToraxOutlaw on 2014-05-07
The internal microphone doesn't appear to be working. I've tried using Google+ and Skype to no avail.

---

### Post by ToraxOutlaw on 2014-05-10
Any advice guys cause I'm still stuck with the aforementioned issues.

---

### Post by TheFu on 2014-05-10
Saying you are stuck, but not telling us
a) what you have tried, "exactly"
b) what failed, "exactly"
c) which hardware has drivers loaded, but not working
d) which hardware is recognized, but not working
makes it difficult for us to be helpful.

This is just like Windows.

Also, it is best to ask 1 question at a time, to the specific sub-forum. Audio and wifi require very different expertise to troubleshoot, hence why there is a different forum for each.  We are used to seeing the exact command run AND the relevant output from that command to troubleshoot. If you don't understand what we ask for, let us know and someone should explain or provide a how-to (probably on help.ubuntu.com). Use the built-in select and paste to grab the terminal commands and output for posting here. No images, please.  I don't really care about audio at all, so cannot help troubleshoot other than to say that it is working on my C720 with the stuff I did in the link below.  Don't know if it worked before those kernel modules were added or not.  Also, after going into standby, sometimes the audio doesn't come back and a reboot is needed.  It usually takes 5+ standbys before I notice that it isn't working. Don't really use audio on that machine.

Did you figure out how to install **wicd-curses**?  When a command isn't found, that usually means it isn't installed - we would expect you to install it (10 secs) - and move on.  Just to clarify, use any package manager to install it by name from the repository. DO NOT hunt down a .deb file and install it, that will cause issues most users are not ready to address.  Package managers for Ubuntu include .... software center, synaptic, aptitude, apt-get.

So ... **sudo aptitude update; sudo aptitude upgrade; sudo aptitude install wicd-curses; **should do what you need to get the wifi controls desired.

Of course, there are 10 other wifi controller tools as well.  I prefer the wicd version specified because it works on pure servers that don't have any GUI at all too. Plus select/paste for the curses interface is easy compared to dealing with a GUI.

Don't remember if I mentioned this, but here's my C720 complaint/fix page: [http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04](http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04)  BTW - I've completely disabled the power button on my C720. It is completely ignored now for everything.  If I want to shutdown - **sudo shutdown -h now** is the command.  Standby - **sudo pm-suspend** ... you get the idea.  At least I'm not worried about hitting the DEL key anymore. ;)  Idiot designers should be shot.

BTW, many metro areas have Linux User Groups which are perfect for 1-on-1 help.  My group meets every Sunday and we usually do 1 installation weekly for someone new, and answer all sorts of questions for the other 5-8 folks who show up.  It is hard to beat in-person help.

So - good luck and ask questions if you don't understand.   .... and please, please use "code" tags.

---

### Post by ToraxOutlaw on 2014-05-28
Hey there I fixed the issues I was having. Apparently my account wasn't a full administrator, it was a custom account and this was blocking my access to everything including networking tools. I did a wipe and reinstall of Chrome OS, then did a fresh install of Ubuntu. Once Ubuntu was running, I installed Cinnamon followed by gnome-system-tools cause the cinnamon user group wasn't working. I used the gnome-system-tools user and group settings panel to give my account full admin privileges, everything's working now as it should. In regards to the microphone not working, I installed pavucontrol to manually select the working microphone before I load up Skype to make a call. So yeah, a little perseverance and some hard thinking as well as Google searching turned up some surprising results.

---

### Post by TheFu on 2014-05-28
> **ToraxOutlaw said:**
> Hey there I fixed the issues I was having. Apparently my account wasn't a full administrator, it was a custom account and this was blocking my access to everything including networking tools. I did a wipe and reinstall of Chrome OS, then did a fresh install of Ubuntu. Once Ubuntu was running, I installed Cinnamon followed by gnome-system-tools cause the cinnamon user group wasn't working. I used the gnome-system-tools user and group settings panel to give my account full admin privileges, everything's working now as it should. In regards to the microphone not working, I installed pavucontrol to manually select the working microphone before I load up Skype to make a call. So yeah, a little perseverance and some hard thinking as well as Google searching turned up some surprising results.

Either an account has appropriate sudo settings or it doesn't. Only the sudoers file controls that. There isn't any special "administrator" setting; no special "registry" to be setup.  Normal id, file, group permissions are all that determines privileges under Linux/UNIX systems. Group membership is often used to make shortcuts for higher access levels - the adm and/or wheel groups are an examples, but there are others under different distros.  These are just normal groups given extra access to directories, files, devices (which are also files).   With a strong understanding of those things, it is amazing what is possible - beyond the normal stuff.

Regardless, happy that you figured out a solution. That is the important part.

---

