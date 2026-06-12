---
title: "Lots of problems - Some help to a beginer?"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by nahuelarg86 on 2012-07-09
Hi, I just installed ubuntu for first time. I always ran windows in my computers, and one day (yesterday) I decided to give Linux a try.
First off, I installed ubuntu through wubi, so it is "inside" my windows 7. I gave it 30 gb of space.
Now my problem is that everything in ubuntu seems to be super slow! I don't know if this is normal or not, since I have zero experience with linux. But I don't know, downloading something from the app store takes like 10 min. Firefox is kind of slow too, not a lot, but slower than windows. The system itself is all laggy. The windows and applications freeze/unfreeze all the time.
Besides the performance, I have a zillion issues with drivers. I cannot make ubuntu recognize my nvidia card. I just was able to install java (after HOURS of researching) and found it at a random post here in the forum. The brightness level keeps going to the top every time I reboot (I'm trying to fix that right now). The volume has like an "invisible" top. I mean, I use the buttons from the keyboard on my laptop and I rise the volume to the top, but it feels somewhat quiet. Then I go to the "Sound" on the "control panel" and it shows that there is a bit more to rise that I cannot get with the keyboard.
My laptop details:
Asus X53S
Intel Core i7-2670QM CPU @ 2.20GHz
Ram 8 Gb
nVidia GT 540m / Intel Graphics Card 300

I hope somebody with some experience can show up and give me a hand.
Thank you,

Nahuel

---

### Post by afixane on 2012-07-09
Hi, welcome to Ubuntu Forum! :D

For the slow/lagg, i can't help you. Maybe someone with more skill on linux than me can help you. For the driver, you can run "Additional Driver" (click "Dash" (The big ubuntu logo) and then type "Additional Driver", or you can type "jockey-gtk" on terminal) "Additional Driver" will search the "non-free" (free in freedom, or non-open source) driver for your hardware.

---

### Post by nahuelarg86 on 2012-07-09
> **afixane said:**
> Hi, welcome to Ubuntu Forum! :D

For the slow/lagg, i can't help you. Maybe someone with more skill on linux than me can help you. For the driver, you can run "Additional Driver" (click "Dash" (The big ubuntu logo) and then type "Additional Driver", or you can type "jockey-gtk" on terminal) "Additional Driver" will search the "non-free" (free in freedom, or non-open source) driver for your hardware.

Thanks for your reply. Yes, I have done that and the windows doesn't show any drivers. It says that it couldn't find drivers.

---

### Post by ronnysingh on 2012-07-09
Ubuntu 12.04 does not even require so good configuration. I guess the problem should be related with compatibility of your computer with Ubuntu.

---

### Post by nahuelarg86 on 2012-07-09
> **ronnysingh said:**
> Ubuntu 12.04 does not even require so good configuration. I guess the problem should be related with compatibility of your computer with Ubuntu.

So you say that I cannot run ubuntu/linux on certain computers? I thought that linux was supposed to be better than the regular windows...:?

---

### Post by Curtis6767 on 2012-07-09
For the sound issues, try this.

Hit Ctrl + Alt + T to open a terminal. At the prompt type alsamixer and then hit enter.

Use your arrow keys to move sideways to each of the choices and then hit your up arrow key to raise the volume.

If you see MM in one of the choices, move to it and hit 'm' on your keyboard to unmute it.

If you do all that and you're still having sound problems, then it's something else.

---

### Post by afixane on 2012-07-09
> **nahuelarg86 said:**
> Thanks for your reply. Yes, I have done that and the windows doesn't show any drivers. It says that it couldn't find drivers.

Make sure you're connected to internet. If you're connected via wireless, try to connect via wired. And, try to uninstall ubuntu via windows control panel, then try dualboot. From my experiences, Dualboot is faster than wubi.

---

### Post by nahuelarg86 on 2012-07-09
> **Curtis6767 said:**
> For the sound issues, try this.

Hit Ctrl + Alt + T to open a terminal. At the prompt type alsamixer and then hit enter.

Use your arrow keys to move sideways to each of the choices and then hit your up arrow key to raise the volume.

If you see MM in one of the choices, move to it and hit 'm' on your keyboard to unmute it.

If you do all that and you're still having sound problems, then it's something else.

Thanks for the reply. I tried that, all the bars were at their maximum. But still, when I go to Sound, the 100% is not the full bar. Here, I attached a screen shot so you can see what I mean.

---

### Post by nahuelarg86 on 2012-07-09
> **afixane said:**
> Make sure you're connected to internet. If you're connected via wireless, try to connect via wired. And, try to uninstall ubuntu via windows control panel, then try dualboot. From my experiences, Dualboot is faster than wubi.

So you mean to create a partition for ubuntu? I'm a little worried of doing that since I have so many problems with the drivers and everything right now that I don't know if I feel like partitioning and doing such big work if at the end I will have all these same problems...

---

### Post by Curtis6767 on 2012-07-09
> **nahuelarg86 said:**
> So you mean to create a partition for ubuntu? I'm a little worried of doing that since I have so many problems with the drivers and everything right now that I don't know if I feel like partitioning and doing such big work if at the end I will have all these same problems...

Hey, not so fast. Good thing about WUBI is that you can test drive Ubuntu to make sure everything works before doing a dual boot or something else.

Right now you have a couple of issues that need to be resolved before moving ahead to an install.

For the sound, you might want to go to the Software Center and install Pulse Audio Volume Control. That will give you a little bit more control over the sound, however, installing Pulse and getting it running is another thing. I suggest you google it after you've got it installed.

---

### Post by nahuelarg86 on 2012-07-09
> **Curtis6767 said:**
> Hey, not so fast. Good thing about WUBI is that you can test drive Ubuntu to make sure everything works before doing a dual boot or something else.

Right now you have a couple of issues that need to be resolved before moving ahead to an install.

For the sound, you might want to go to the Software Center and install Pulse Audio Volume Control. That will give you a little bit more control over the sound, however, installing Pulse and getting it running is another thing. I suggest you google it after you've got it installed.

Thanks. I'll try to see what can I find.

This ubuntu thing is driving me crazy! I spent most of the day yesterday and today trying to solve stuff. I want to like this OS, I always was at the verge of trying out linux and playing with it, in fact my first impression was very positive for the GUI and the arrangements. Then digging around a little more I found out all these issues...

---

### Post by S2UIRR3L on 2012-07-09
Were you having the same problems when using it as a live disc? I understand that using Ubuntu as a live disc is a little slower than a full install (because it had to read everything from the actual disc and your RAM), but are you having the same problems with the brightness and not being able to move the volume past 100% (all the way to the right)?

-Leo in Massachusetts (us)

---

### Post by nahuelarg86 on 2012-07-09
> **S2UIRR3L said:**
> Were you having the same problems when using it as a live disc? I understand that using Ubuntu as a live disc is a little slower than a full install (because it had to read everything from the actual disc and your RAM), but are you having the same problems with the brightness and not being able to move the volume past 100% (all the way to the right)?

-Leo in Massachusetts (us)

Yes, I tried using the live disc. That was my first try at ubuntu, then, since I liked how it looked, I decided to do the wubi. I didn't do much from the cd, it was horribly slow (and I have little patience), so I didn't test much of anything using the live disc.

---

### Post by nahuelarg86 on 2012-07-09
@[Curtis6767]("http://ubuntuforums.org/member.php?u=1534479"): I installed PulseAudio Volume Control, and it didn't help much. I couldn't go past that 100% that is half way from the end of the line. I attached an image so you can see. The red shows the "half-way 100%"

---

### Post by z3nhakr on 2012-07-09
im assuming you have one of those new switchable graphics cards? i have on on my lenovo u400 except it is amd instead of nvidia but it has this weird bug that causes a low fps. i was able to switch to the intel card by manually installing the amd software and drivers through software center and then switching to the intell card which runs smoother but only works with unity 2d. hope that helps :)

---

### Post by S2UIRR3L on 2012-07-09
I'm some what of a newbie too... and I can't lie, that does sound like a graphics card issue and maybe having to search for alternate drivers or perhaps patch the ones you have right now... Possibly do some sort of work around?

Have you had this problem with any other Linux distributions? Did you try Kubuntu or Xubuntu or Lubuntu? For all we know (and I can be totally wrong here) Ubuntu 12.04 Precise Pangolin hasn't made it to your drivers yet.

-Leo in Massachusetts (us)

---

### Post by Curtis6767 on 2012-07-09
> **nahuelarg86 said:**
> @[Curtis6767]("http://ubuntuforums.org/member.php?u=1534479"): I installed PulseAudio Volume Control, and it didn't help much. I couldn't go past that 100% that is half way from the end of the line. I attached an image so you can see. The red shows the "half-way 100%"

What happens if you click on the Playback tab and then play some audio? Can you move the slider to the right and adjust volume that way?

---

### Post by nahuelarg86 on 2012-07-10
> **Curtis6767 said:**
> What happens if you click on the Playback tab and then play some audio? Can you move the slider to the right and adjust volume that way?

So I have audio, that is not the problem. And I can move the slider past that 100 point. I can doit with the mouse. The problem is that I cannot do it with the keyboard, nor if I click on the little speaker icon to the left of the time. Both will show that the volume is at its top. But going to the sound settings shows that it's only at the 100 mark. It reminds me of an ipod setting, where you can lock the volume to a certain volume, so you can't go over that point you set up. I'm explaining myself? Sorry for so much mess.

---

### Post by nahuelarg86 on 2012-07-10
> **S2UIRR3L said:**
> I'm some what of a newbie too... and I can't lie, that does sound like a graphics card issue and maybe having to search for alternate drivers or perhaps patch the ones you have right now... Possibly do some sort of work around?

Have you had this problem with any other Linux distributions? Did you try Kubuntu or Xubuntu or Lubuntu? For all we know (and I can be totally wrong here) Ubuntu 12.04 Precise Pangolin hasn't made it to your drivers yet.

-Leo in Massachusetts (us)

I don't know, I'm not having many issues with the graphics right now. Everything (graphics related) seems to work well, the only thing is that in "details" it says unknown for the graphics card. Also, I don't know if I will have troubles because of that. Right know I'm testing ubuntu, so I didn't try any games or anything like that yet.

I didn't try any other distribution either. Maybe I should, but I thought that plain vanilla ubuntu should be more than enough. Maybe I should try. It's just I don't want to delete this ubuntu that I just installed, mostly because the time I spent trying to get it together.

---

### Post by madjr on 2012-07-10
sadly your hardware is not fully compatible yet (is coming but not there yet). Nvidia has not released full support for your dual video card.

Better explanation here (the famous finger from Linus tovalds himself):

[http://youtu.be/MShbP3OpASA?t=48m14s](http://youtu.be/MShbP3OpASA?t=48m14s)


Also after that particular incident, nvidia seems to be more cooperative:
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyNTk](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNTk)

---

### Post by nahuelarg86 on 2012-07-10
> **madjr said:**
> sadly your hardware is not fully compatible yet (is coming but not there yet). Nvidia has not released full support for your dual video card.

Better explanation here (the famous finger from Linus tovalds himself):

[http://youtu.be/MShbP3OpASA?t=48m14s](http://youtu.be/MShbP3OpASA?t=48m14s)


Also after that particular incident, nvidia seems to be more cooperative:
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyNTk](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNTk)


Thanks, interesting and funny video. Any idea about why I have a very laggy/sluggish experience with this ubuntu? On another note, I have ubuntu x64, I read that it's not as good as x32, but wubi decided to install x64 anyways. Also, I thought that my hardware would be more than enough to run anything, maybe I was wrong. If I want to pass to x32, do I have to uninstal the whole ubuntu and do all over again?

---

### Post by madjr on 2012-07-10
> **nahuelarg86 said:**
> Thanks, interesting and funny video. Any idea about why I have a very laggy/sluggish experience with this ubuntu? On another note, I have ubuntu x64, I read that it's not as good as x32, but wubi decided to install x64 anyways. Also, I thought that my hardware would be more than enough to run anything, maybe I was wrong. If I want to pass to x32, do I have to uninstal the whole ubuntu and do all over again?

I find it weird that is sluggish.

lets see if its the video card.

can you try the "2d" desktop for a minute and see if the sluggishness is the same (should be as smooth as in the video):


[http://askubuntu.com/questions/74300/how-to-login-into-unity-2d](http://askubuntu.com/questions/74300/how-to-login-into-unity-2d)

[http://www.youtube.com/watch?v=KuFZ8DuDRpU](http://www.youtube.com/watch?v=KuFZ8DuDRpU)


if it's still the same, I would try x32.

Uninstalling will just take 1 sec (so move/backup any important file you may have), then reinstalling usually takes about 30 min, just skip any "downloading" updates, language files, etc..

---

### Post by Paqman on 2012-07-10
> **nahuelarg86 said:**
> On another note, I have ubuntu x64, I read that it's not as good as x32

Nope, that's not correct. 64-bit is loads better than 32-bit. It's faster, can use more RAM and is just as widely supported on Linux. The only reason 32-bit still exists and is the default recommendation is that there is still some 32-bit only hardware. If you have a 64-bit chip, you should be running 64-bit. 32-bit will be getting phased out completely in a few years time.

The general slowness of your machine will be down to lacking graphics drivers. If you have Nvidia Optimus graphics you can try using [Bumblebee ]("http://bumblebee-project.org/")to get it working, but it's a bit of a kludge. In the meantime I would back madjr up and say step down to 2D graphics for your desktop to make things a bit more usable.

---

### Post by Kain000 on 2012-07-10
as far as the sound bar issue you were talking about goes, the 100% line that the keyboard controls are limited to is the "recomended" highest output. you can (as you see) overdrive the speakers and push out more wattage but the block there is a saftey of sorts to keep you from acidently ramping up your volume and destroying your speakers via the physical buttons.

---

### Post by nahuelarg86 on 2012-07-10
> **madjr said:**
> I find it weird that is sluggish.

lets see if its the video card.

can you try the "2d" desktop for a minute and see if the sluggishness is the same (should be as smooth as in the video):


[http://askubuntu.com/questions/74300/how-to-login-into-unity-2d](http://askubuntu.com/questions/74300/how-to-login-into-unity-2d)

[http://www.youtube.com/watch?v=KuFZ8DuDRpU](http://www.youtube.com/watch?v=KuFZ8DuDRpU)


if it's still the same, I would try x32.

Uninstalling will just take 1 sec (so move/backup any important file you may have), then reinstalling usually takes about 30 min, just skip any "downloading" updates, language files, etc..

I'm using ubuntu 2d right now. As I'm writing this, the text freezes every 3 seconds, so I'm typing and the text doesn't appear until seconds later all in a bunch. I couldn't test the apps overall with 2d yet. I was with the 3d a few minutes ago and installed Gnome, and Firefox was impossible to use (froze every 10 seconds). 

> **Paqman said:**
> Nope, that's not correct. 64-bit is loads better than 32-bit. It's faster, can use more RAM and is just as widely supported on Linux. The only reason 32-bit still exists and is the default recommendation is that there is still some 32-bit only hardware. If you have a 64-bit chip, you should be running 64-bit. 32-bit will be getting phased out completely in a few years time.

The general slowness of your machine will be down to lacking graphics drivers. If you have Nvidia Optimus graphics you can try using [Bumblebee ]("http://bumblebee-project.org/")to get it working, but it's a bit of a kludge. In the meantime I would back madjr up and say step down to 2D graphics for your desktop to make things a bit more usable.

Thanks, I'm trying 2d right now. I installed Bumblebee but it didn't seem to help much. Same with 2d, seems a tiny bit better, but nothing compared at the speeds I get in Windows...

> **Kain000 said:**
> as far as the sound bar issue you were talking about goes, the 100% line that the keyboard controls are limited to is the "recomended" highest output. you can (as you see) overdrive the speakers and push out more wattage but the block there is a saftey of sorts to keep you from acidently ramping up your volume and destroying your speakers via the physical buttons.

Ok, got it. But I have the feeling that the maximum or that 100% isn't the maximum I used to hear when I used Windows. I feel it's lower. That's why it's driving me crazy.

---

### Post by madjr on 2012-07-10
> **Paqman said:**
> Nope, that's not correct. 64-bit is loads better than 32-bit. It's faster, can use more RAM and is just as widely supported on Linux. The only reason 32-bit still exists and is the default recommendation is that there is still some 32-bit only hardware. If you have a 64-bit chip, you should be running 64-bit. 32-bit will be getting phased out completely in a few years time.


actually 64 and 32 bit will be merging soon:

[http://www.phoronix.com/scan.php?page=news_item&px=MTA1OTY](http://www.phoronix.com/scan.php?page=news_item&px=MTA1OTY)

---

### Post by madjr on 2012-07-10
> **nahuelarg86 said:**
> I'm using ubuntu 2d right now. As I'm writing this, the text freezes every 3 seconds, so I'm typing and the text doesn't appear until seconds later all in a bunch. I couldn't test the apps overall with 2d yet. I was with the 3d a few minutes ago and installed Gnome, and Firefox was impossible to use (froze every 10 seconds). 



Thanks, I'm trying 2d right now. I installed Bumblebee but it didn't seem to help much. Same with 2d, seems a tiny bit better, but nothing compared at the speeds I get in Windows...



Ok, got it. But I have the feeling that the maximum or that 100% isn't the maximum I used to hear when I used Windows. I feel it's lower. That's why it's driving me crazy.

I had that slowness on one of my computers with the 64 bit image, maybe you can try now the 32 bit and see if there is any difference.

as far as the "max" volume, A developer told me that there are plans to redesign that element so is more efficient and you can choose your max without having to open that dialogue.

Anyway I usually get the same volume in windows and ubuntu, but in ubuntu sometimes I can raise it higher. In what case particular do you feel the volume is low, maybe is a particular youtube video or something? maybe we can help confirm the problem in our own machines.

---

### Post by nahuelarg86 on 2012-07-10
> **madjr said:**
> I had that slowness on one of my computers with the 64 bit image, maybe you can try now the 32 bit and see if there is any difference.

as far as the "max" volume, A developer told me that there are plans to redesign that element so is more efficient and you can choose your max without having to open that dialogue.

Anyway I usually get the same volume in windows and ubuntu, but in ubuntu sometimes I can raise it higher. In what case particular do you feel the volume is low, maybe is a particular youtube video or something? maybe we can help confirm the problem in our own machines.

That sounds good, I feel the system needs a lot of improvement. For the sound, it is not a particular video or song, I have an overall feeling that it is quieter than Windows. But, perhaps it's just me. It's weird, I think that my laptop should handle better a 64-bit system...

---

### Post by madjr on 2012-07-10
> **nahuelarg86 said:**
> That sounds good, I feel the system needs a lot of improvement. For the sound, it is not a particular video or song, I have an overall feeling that it is quieter than Windows. But, perhaps it's just me. It's weird, I think that my laptop should handle better a 64-bit system...

A little more digging about your hardware (Asus *53s)  brought me here:

ubuntu 11.04:
[http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081)


ubuntu 11.10:
[http://ubuntuforums.org/showthread.php?t=1875982](http://ubuntuforums.org/showthread.php?t=1875982)


It seems things keep improving with your hardware every 6 months and there seems to be workarounds for many stuff, but like I mentioned is one of the those cases of hardware that is still not fully compatible.

While most hardware I tried works, more people are opting for [Ubuntu preinstalled]("http://www.omgubuntu.co.uk/2012/06/hands-on-with-the-system76-lemur-ultra-ubuntu-laptop"). This is why apple only allows mac OSX preinstalled in a small amount of computers to verify things work. But linux is open so it works with an ever increasing range of hardware/[devices]("http://www.linuxfordevices.com/").

for now, till the issues are fixed, you may want to try ubuntu in **Virtual-box**:

[http://www.youtube.com/watch?v=hK-oggHEetc&feature=related](http://www.youtube.com/watch?v=hK-oggHEetc&feature=related)
[http://www.wikihow.com/Install-Ubuntu-on-VirtualBox](http://www.wikihow.com/Install-Ubuntu-on-VirtualBox)

However If you like to play around and maybe try to fix some of the stuff, check the links above. You're not alone, so Might be a learning experience. :)

Cheers !

---

### Post by nahuelarg86 on 2012-07-10
Well, I installed the 32-bit version of ubuntu and seems running much better than the last version. I still have the issue of the graphic card not appearing on details, but, oh well...
It still very annoying the fact that the brightness goes all the way up every time I reboot or the screen goes to sleep.
Any idea on how to solve this? (Maybe is related to the graphics card?)

---

### Post by ub07 on 2012-07-11
I noticed that volume issue on my laptop too. It's generally louder in Windows than in Ubuntu.

I also want to mention that what you are thinking is the halfway mark is actually the 100% mark. When you move beyond that mark, the computer is supplying additional amplification.

---

