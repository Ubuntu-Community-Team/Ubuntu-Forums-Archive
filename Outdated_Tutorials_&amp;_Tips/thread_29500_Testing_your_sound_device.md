---
title: "Testing your sound device"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by crazybill on 2005-04-24
If you can't hear sound coming from your Ubuntu Linux computer,  you might wonder if  the problem  is a hardware problem (the sound card) a kernal problem (perhaps a bad kernal driver) or a software problem, such as mplayer if that is what you were trying to use.  Before blaming software setup, it is good to check the sound devise to see if it is really working properly, that your speakers are powered on, and that they are plugged in properly to the computer box. It is usually the simple things that cause problems.

Ubuntu Linux has a neat way to check out to see if the sound devise is working properly.

First find a wav file. To do that, open a terminal and type
**find /usr -name *.wav -print** 
to find where some wav files are stored on your computer.
If  you took the default setup of Hoary Hedgehog Ubuntu Linux, you don't even need to search. Simply to to the the sounds sub-directory of the  library directory of openoffice: 
 ***/usr/lib/openoffice/share/gallery/sounds***
Then type:
 **cd /usr/lib/openoffice/share/gallery/sounds** to move to that directory
In that directory is a file called train.wav (You can find that or other wav files with the command **ls** )
Type 
**cat train.wav > /dev/dsp**
If you did not change your directory, type the following instead:
**cat  /usr/lib/openoffice/share/gallery/sounds/train.wav > /dev/dsp**
_RESULTS:_
If you hear a train sound, the sound card is working properly.
If not, you know that your problem is that your speakers are not working, not turned on, or not plugged in correctly --- or that your sound card is bad, not making good contact to your motherboard, or without the correct driver.
[B]
_How this works:_[/B]
In this example ***cat** *reads the file*** train.wav ***
If you only  type cat train.wav , the output of the file would have printed gobble-de-gook to your LCD or CRT computer screen. That is because a wav file was not meant to be displayed as a text file on a computer monitor! However by adding the*** > /dev/dsc* ** to the end of the command, it transferred the standard output from the computer monitor to the registered sound devise. 

When you hear the train sound (from the above example), you know  that  your sound card is functioning correctly with the correct kernal driver. Thus, it eliminates hardware as the cause of the problem.

---

### Post by crazybill on 2005-04-24
As a tanget to this, here is something fun you can do... 

From a networked computer, logon to your ubuntu computer where a friend is.
Move a wav file that you made saying something like "What are you doing here?"
Lets say it is saved at **/home/yourname/mysound.wav**

Type into the terminal:   **cat /home/yourname/mysound.wav > /dev/dsp**
The computer will blurt out with your voice though you are not in the room.

Or need an alarm clock?
Make a file called **/home/yourname/wakeup.wav **
Then type in: **00 06 * * * cat /home/yourname/wakeup.wav > /dev/dsp**

At 6 AM, the computer will blurt out for you to wake up!

---

### Post by XplOzIOn on 2005-04-25
[QUOTE=crazybill]As a tanget to this, here is something fun you can do... 

From a networked computer, logon to your ubuntu computer where a friend is.
Move a wav file that you made saying something like "What are you doing here?"
Lets say it is saved at **/home/yourname/mysound.wav**

Type into the terminal:   **cat /home/yourname/mysound.wav > /dev/dsp**
The computer will blurt out with your voice though you are not in the room.

Or need an alarm clock?
Make a file called **/home/yourname/wakeup.wav **
Then type in: **00 06 * * * cat /home/yourname/wakeup.wav > /dev/dsp**

At 6 AM, the computer will blurt out for you to wake up![/QUOTE]
 Hey the alarm clock idea its pretty cool!:. Nice and thank you!

---

### Post by Poul on 2005-05-23
wow
 like the idea of remote playback. wonder if it's possible to do some sort of life streaming with a mic this way That could really scare someone i need to try this
Any ideas??
( Edit: when it comes to think about it it's obviou that it's possible - it's linux)

---

### Post by JonahRowley on 2005-05-23
[QUOTE=Poul]wow
 like the idea of remote playback. wonder if it's possible to do some sort of life streaming with a mic this way That could really scare someone i need to try this
Any ideas??
( Edit: when it comes to think about it it's obviou that it's possible - it's linux)[/QUOTE]

You could use netcat for that ;)  But if you're pushing raw audio, it had better be on a local network, and netcat won't do any buffering really..  Could work though.

---

### Post by JonahRowley on 2005-05-23
This is actually not a very good idea.  wav files are not raw PCM, they have header information, may be in any number of sample rates, and will probably not sound very nice piping directly to the sound card.  Some may work, but all will not.

Also, **/dev/dsp** is ALSA's OSS emulation device.  To use ALSA directly, **/dev/audio** is what you're looking for.  Also, **/dev/snd/** holds a number of devices to control the sound card.

---

### Post by RastaMahata on 2005-05-24
excellent tips! :)

---

### Post by kudu on 2005-12-31
I'm just getting white noise. What's the deal ?

Sound seems to be working fine but when I ran this test for the heck of it I got white noise.

Should I be concerned ??

---

### Post by Liz.nogan on 2009-12-09
Well dude, the best thing i can tell u is, look up your computer, like type in the name in google. then the site for your computer will show up, after that, go to something like install sound drivers for this computer. download the sound drivers and restart your computer. hopefully this works dude. it did for me. also remember that your computer has its own distinguished driver so download the proper one for it....

---

### Post by gradinaruvasile on 2009-12-09
Just use

```
speaker-test -c 2 -t wav
```

---

