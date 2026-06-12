---
title: "Installed Hardy Heron and appear to have lost all sound.  Any ideas?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Beaker Boy on 2008-06-02
All

As you may have seen from other threads, I have just installed Hardy Heron and have come across a couple of problems.   Firstly, I don't seem to able to hear any sound from CDs/Flash streams/anything.  Secondly my DVD Read Writer seems incabable of actually playing DVDs.  Any ideas or obvious things I should look at?

Many thanks

Beakerboy

---

### Post by jeffus_il on 2008-06-02
Do you have system sounds e.g. when you log on etc...???

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-02
Try going to Master Volume preferences for you're configs to see if you accidentally disabled it. Happened to me once:oops:

If you haven't installed anything special you could just try reinstalling Hardy manually. Sometimes something goes wrong with the GUI install. If you still don't get any sound check the Live CD for defects or problems.

Hope this helps,
Armageddon

---

### Post by rraj.be on 2008-06-02
The first point that you should note is 

```
No multi session disc will be mounted in ubuntu

Ubuntu defaultly wont support Mp3
```

You should install codecs and plugins to play media.

Mp3 is not defaultly suported by ubunt.

The best way is to install Vlc player[Known to play most media formates including Mp3]

 and 

All available GSTREMERS codecs and plugins.

Use synaptic package manager to install.

---

### Post by kpkeerthi on 2008-06-02
> **rraj.be said:**
> The first point that you should note is 

```
No multi session disc will be mounted in ubuntu
```


That is incorrect. Ubuntu mounts multi-session discs. Hardy comes with Brasero that can burn multi-session discs.

---

### Post by kpkeerthi on 2008-06-02
> **Beaker Boy said:**
> All

As you may have seen from other threads, I have just installed Hardy Heron and have come across a couple of problems.   Firstly, I don't seem to able to hear any sound from CDs/Flash streams/anything.  Secondly my DVD Read Writer seems incabable of actually playing DVDs.  Any ideas or obvious things I should look at?

Many thanks

Beakerboy

To get the commercial DVD playable in ubuntu, see this [tip]("http://www.ubuntux.org/how-to-play-restricted-formats-with-ubuntu-multimedia-codecs")

To fix the sound problem, see this [post]("http://ubuntuforums.org/showthread.php?t=776739")

---

### Post by rraj.be on 2008-06-02
I know ubuntu can burn multisession but is it possible to mount a multisession disc in ubuntu.

If possible could you please give me a little more  detail about  that.

And if i have provided wrong information i am sorry for that.

---

### Post by kpkeerthi on 2008-06-02
> **rraj.be said:**
> I know ubuntu can burn multisession but is it possible to mount a multisession disc in ubuntu.

If possible could you please give me a little more  detail about  that.

And if i have provided wrong information i am sorry for that.

I don't have any trouble having ubuntu auto-mount my multi-session discs (containing music). 

What happens when you pop in multi-session disc? (Please open a new thread if you are having trouble here. Let us not hijack this thread. Thanks.)

---

### Post by 7raTEYdCql on 2008-06-02
I had a similar problem with no sound on my laptop even after installing the gstreamer codecs.

in terminal tye the command 
```
alsamixer
```

The surround option may not have anything to it by default. Increase it.

---

### Post by Sirchristopher on 2008-06-02
Check your kernal.  You may have installed an old one.  This could br keeping your sound from working.

---

### Post by Beaker Boy on 2008-06-02
No I don't.

---

### Post by Beaker Boy on 2008-06-02
Sorry, not sure what you mean by this.

---

### Post by Beaker Boy on 2008-06-02
> **jeffus_il said:**
> Do you have system sounds e.g. when you log on etc...???

No I don't

---

### Post by Beaker Boy on 2008-06-02
> **Sirchristopher said:**
> Check your kernal.  You may have installed an old one.  This could br keeping your sound from working.

Sorry, not sure what you mean by this.

---

### Post by jeffus_il on 2008-06-02
Like "too many cooks spoil the broth", it seems that "too many responses spoil the thread".

We need some fact like try looking at the system logs to see if there are some warnings or errors regarding sound, audio etc.
```
Menu: System->Administration->System Log
```

look at the output of ```
dmesg
``` in a terminal and try to identifiy your audio device and the relevant lines of text.

Try ```
lshw
``` in a terminal and post the paragraph describing your Audio/Multimedia device, we can then figure out what kernel module should be loaded and check if it is being loaded by using something like>  lsmod | grep myaudiomodule

---

### Post by Beaker Boy on 2008-06-03
> **jeffus_il said:**
> Like "too many cooks spoil the broth", it seems that "too many responses spoil the thread".

We need some fact like try looking at the system logs to see if there are some warnings or errors regarding sound, audio etc.
```
Menu: System->Administration->System Log
```

look at the output of ```
dmesg
``` in a terminal and try to identifiy your audio device and the relevant lines of text.

Try ```
lshw
``` in a terminal and post the paragraph describing your Audio/Multimedia device, we can then figure out what kernel module should be loaded and check if it is being loaded by using something like

The only thing I found with the lshw command was the following:

 *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

Is this what you were talking about?

Beaker Boy

---

### Post by jeffus_il on 2008-06-03
I think your device needs the snd-hda-intel kernel module loaded.
doing ```
lsmod | grep intel 
```
should show the driver in the result iof it is loaded.

---

### Post by mde123 on 2008-06-03
smae problem

---

### Post by almabeck on 2008-06-03
I, too, lost all sound on my laptop when I upgraded. I finally went back and did a clean install, and that solved all my problems.

---

