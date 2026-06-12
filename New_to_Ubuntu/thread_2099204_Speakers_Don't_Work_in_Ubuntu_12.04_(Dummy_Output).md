---
title: "Speakers Don't Work in Ubuntu 12.04 (Dummy Output)"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Kariotaki on 2012-12-28
Hi friends,

Just installed Ubuntu 12.04 on an old Compaq Desktop and my speakers don't work. In fact, I don't think it detects the sound card at all. When I go to Sound Settings, all it shows is "Dummy Output." 

I believe I am using an nVidia Corporation MCP51 High Definition Audio sound card

Appreciate any advice.

---

### Post by 2F4U on 2012-12-28
Can you provide the output of 

```
cat /proc/asound/cards
```

and 

```
lspci | grep -i audio
```

so that we can determine what sound card(s) you have in the system?

---

### Post by Kariotaki on 2012-12-29
Hi, Here is the output:

xristaras@xristaras-linux:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe024000 irq 42
xristaras@xristaras-linux:~$ lspci | grep -i audio
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)

---

### Post by Kariotaki on 2013-01-03
I entered this script and it worked:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

Found it here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Aide9aic on 2013-01-30
A cautionary note for anyone who stumbles across this thread. The long string of commands above includes installing -- and then immediately reinstalling (why? dunno) -- the entire Ubuntu desktop. A member of the Kubuntu Forums found this thread and ran the command string in an attempt to fix sound problems, and then wondered why his desktop changed.

(Re)installing an entire desktop just to fix a sound problem doesn't appear to be a reasonable troubleshooting step. Especially when the suggestion is to install the full Ubuntu desktop package, immediately followed by a second command to perform the exact same steps.

In looking through the edit history of the linked Wiki page, I can see that a previous editor added a warning, which was subsequently removed. I will put one back.

---

### Post by sdowney717 on 2013-04-16
On Raring 13.04, sound was not playing
tried this and now have sound?
**I ALSO HAD TO** slide the volume slider from the middle position up to hear the sound. so I had not moved the slider earlier. Maybe that was it?
I would have thought the middle slider position would have yielded sound?

YET, there is still no microphone available under input, so still not correct?
However slide the slider up some more, and it responds as a microphone, so who knows. Just does not say microphone.
Called 'Analog input'

what is whoami??

---

