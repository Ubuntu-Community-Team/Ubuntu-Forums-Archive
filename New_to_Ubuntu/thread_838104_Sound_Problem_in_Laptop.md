---
title: "Sound Problem in Laptop"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by anuraggautam on 2008-06-23
Hello All,

I am using Ubuntu Hardy Edition in Laptop Compaq 6720s which has 1 GB RAM 160 GB Hard Disk configuration.

I am getting some problems while using :

1) My Sound is not coming properly.It is coming After playing with Master volume Control and also the sound is very low.It is coming sometimes and sometimes it's not.

However my speakers are not able to speak,while using Headphones sometimes giving some sounds after playing it with Masters Volume.

Can any one tell me what the exact problem is ?

2) However i want to tell you that i have Brand New Laptop Just 10 days Old.

Now tell me why i am getting such problems due to Hardware problem or Driver problem ? and do tell me the Solutions.

Is there any way to Updates the sound drivers ?

With Regards

---

### Post by Pjotr123 on 2008-06-23
Check this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by anuraggautam on 2008-06-23
Tried Every options but same situations :(

---

### Post by ukripper on 2008-06-23
> **anuraggautam said:**
> Hello All,

I am using Ubuntu Hardy Edition in Laptop Compaq 6720s which has 1 GB RAM 160 GB Hard Disk configuration.

I am getting some problems while using :

1) My Sound is not coming properly.It is coming After playing with Master volume Control and also the sound is very low.It is coming sometimes and sometimes it's not.

However my speakers are not able to speak,while using Headphones sometimes giving some sounds after playing it with Masters Volume.

Can any one tell me what the exact problem is ?

2) However i want to tell you that i have Brand New Laptop Just 10 days Old.

Now tell me why i am getting such problems due to Hardware problem or Driver problem ? and do tell me the Solutions.

Is there any way to Updates the sound drivers ?

With Regards

in terminal could you do follwoing and post output here:
```
aplay -l
```
```
lspci | grep audio
```

---

### Post by anuraggautam on 2008-06-23
anurag@Anurag-Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
anurag@Anurag-Laptop:~$ lspci | grep audio
anurag@Anurag-Laptop:~$

---

### Post by eryksun on 2008-06-23
I am by no means an expert, but maybe I can point you to some places to learn more: Sound in Hardy is handled by 2 systems primarily: [[COLOR="Blue"]ALSA [link][/COLOR]]("http://www.alsa-project.org/main/index.php/SoundcardTesting") at the system level and [[COLOR="Blue"]PulseAudio [link][/COLOR]]("http://www.pulseaudio.org/wiki/PerfectSetup") at the user level. PulseAudio rides on top of ALSA, providing user-level services like per application volume control. Since PulseAudio runs at the user level, the drum noise you may or may not hear in the greeter is going straight through ALSA. 

You can try temporarily disabling PulseAudio:

```
pulseaudio -k
asoundconf unset-pulseaudio
cat ~/.asoundrc
```

Make sure the result of the 'cat' command contains the following line:

```
</home/YOUR_USER_NAME/.asoundrc.asoundconf>
```

Then run the command below to reload the ALSA system ('sudo' runs the command as the system superuser. You may be prompted for your password):

```
sudo alsa reload
```

Then run the ALSA mixer and make sure your master volume is set correctly:

```
alsamixer
```

Here are a couple commands to test your audio:

```
speaker-test -twav -c2 -l2
aplay -vv /usr/share/sounds/login.wav

```

Commands to reload PulseAudio:

```
asoundconf set-pulseaudio
sudo alsa reload
pulseaudio &
```

---

