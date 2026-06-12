---
title: "[SOLVED] Can't hear music"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Rohbart on 2008-07-15
Hello,
When I go to youtube and want to hear music there is no problem.
But when I want to hear some songs on my computer or watch a film I have no sound. What can I do to fix this problem? I have tested several music players but none of them has worked. They all display that music is playing but I get nothing to listen to.

---

### Post by sharks on 2008-07-15
have u turned on ur speaker?

---

### Post by Rohbart on 2008-07-15
I think so.
As I wrote I can hear music from youtube. But not from my drive.

---

### Post by bobnutfield on 2008-07-15
Do you have more than one sound device on your computer?  For example, a modem with sound, or USB headphones?  The sound from Flash (Youtube) will automatically choose the correct output device, but your internal apps will not.

Bob

---

### Post by Dedoimedo on 2008-07-15
Hi,
Can you hear the sound when you do other things? Like Ubuntu login?
Can you hear the drums?
Dedoimedo

---

### Post by Rohbart on 2008-07-15
Yes.

---

### Post by sharks on 2008-07-15
go to system---preferences and sound. go there and check whether u have sound enabled or not. slide that bar to full.

---

### Post by bobnutfield on 2008-07-15
Try opening System>Preferences>Sound.  Look to make sure the correct sound device is shown in the box toward the bottom.

Bob

---

### Post by Ryadt on 2008-07-15
Do you mean that you don't get sound when you got youtube and a movie playing together? If so, do you get sound close the browser and try playing some music and see if you get any sound.

---

### Post by Rohbart on 2008-07-15
do you mean "enable software sound mixing", sharks?
How do I know if it's the right sound device? I bought an used computer. Do I have to open it?

No I mean if I just have a movie playing I get no sound. Youtube is the only source I get sound from.

---

### Post by sharks on 2008-07-15
just right click on panel and add to panel---volume control. then check whether the volume slider is full.

---

### Post by kdm on 2008-07-15
I don't think this is anything you are doing.

And you are not the only one to have this problem 
e.g.[http://ubuntuforums.org/showthread.php?t=859067]("http://ubuntuforums.org/showthread.php?t=859067")

But before we file a bug report, I wonder if it is a Ubuntu or Firefox problem (or both !)

---

### Post by bobnutfield on 2008-07-15
There is a dropdown list in the Default Mixer dialogue box.  Look to see what other devices are shown and try them all.  Many times, you will have on-board sound as well as a PCI sound card installed and only one can be the default.

Bob

---

### Post by rushikesh988 on 2008-07-15
I think you should check that you have proper codecs or not ??
And yes try using another player for  playing music ...


Try VLC player

---

### Post by Rohbart on 2008-07-15
sorry for my late answer, I havent seen that we are already on page 2.
@sharks: volume control is ok.
@kdm: My problem is a little different. I cannot even hear music if there is no browser running.
@bobnutfield: Can I try them while the music is playing or do I have to restart the program each time I change them?
@rushikesh988: how can I check the codecs?

---

### Post by sharks on 2008-07-15
just go to synaptic and install ubuntu-restricted-extras

---

### Post by bobnutfield on 2008-07-15
Try each device one at a time, opening a music player with each device.  If one does not work, close the music app and try the next device.  Your best bet is with ALSA as the default device.

Bob

---

### Post by Rohbart on 2008-07-15
yes it is alsa.
Thanks to all of you.

---

### Post by bobnutfield on 2008-07-15
Please edit your post as SOLVED to help other looking to fix a problem like this.

Bob

---

### Post by sharks on 2008-07-15
thank the person who helped u by pressing the star button under his post and please mark the thread solved.

---

### Post by Rohbart on 2008-07-15
how do I edit threadtitles?

---

### Post by sharks on 2008-07-15
u cant edit thread titles. u can press the report button under ur profile name and ask the mod to change ur thread title. to mark ur thread as solved "click on thread tools and mark the thread solved"

---

### Post by Rohbart on 2008-07-15
ok thanks

---

