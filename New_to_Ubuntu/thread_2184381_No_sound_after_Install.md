---
title: "No sound after Install"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by jamisonwright on 2013-10-28
I recently installed Ubuntu 12.04 LTS on my laptop, of which i am very new to. I've gone though and tried some of the basic sound checks I found after some searching to see if anything was muted and can't seem to find the problem. I have a Toshiba Satellite M115-S1061 **Sound Card is a Realtek ALC861-VD**.

I took a screenshot of alsamixer just in case it is showing something I'm not seeing:
[ATTACH=CONFIG]247346[/ATTACH]

Any ideas?

---

### Post by leeper692 on 2013-10-28
Hi I had a simuler problem with my sound after installing 13.10 . I managed to fix it by downloading  the gnome alsa mixer and enabeling the external amp. 
ps: just start turning up all the volume sliders and try enabeling the switch setings till you get sound.Hope this helps!!!

---

### Post by jamisonwright on 2013-10-29
Hey leeper thanks for the response, I downloaded the mixer but I don't see anything about an external amp. Is that something that I have to enable though the terminal?

---

### Post by leeper692 on 2013-10-29
Hi jamisonwright no you dont need the terminal be shure you have picked your sound card from the tabs at the top of the gnome alsa mixer and there will be a number of check boxes at the bottem of the mixer window one of these will say external amplifier next to the box.

---

### Post by jamisonwright on 2013-10-29
OK I made sure I had my sound card selected, I guess it's a Realtek ALC861-VD, but after selecting it there were no changes to the screen. The only check box that I have says Rec. I checked to see if there was sound with that option checked and unchecked but still nothing. :(

---

### Post by jamisonwright on 2013-10-31
Edited the OP with additional info (edit is in **bold**).
Still looking for any help I can get. :/

---

### Post by protoss96 on 2013-11-01
You can try this command:
```
pulseaudio -k
```

Then test the sound.

If you are not hearing the sound again, then you could try to fix this issue by upgrading the kernel. Every kernel release is fixing bugs, for example my touchpad didn't worked very well(constant high sensivity without working scrolling buttons) after upgrading everything is normal.
Simplest way to upgrade your kernel to latest version is to follow this [http://www.upubuntu.com/2013/10/installupgrade-to-linux-kernel-3116-in.html](http://www.upubuntu.com/2013/10/installupgrade-to-linux-kernel-3116-in.html) and everything should work.

---

### Post by jamisonwright on 2013-11-01
Thanks for the reply protoss96, 
I tried the command got nothing, did the update, still with no success, After doing a few hours of research it would seem that my sound card is unsupported at the moment. So I guess all I can do now is wait and see if it ever does get added to the supported cards.
Thanks for the help

---

### Post by protoss96 on 2013-11-02
Try to solve your problem with Kernel upgrading, there is nothing difficult about that. Follow these steps:

1. First of all go to /tmp folder:
```
cd /tmp
```
2. Download installation script for latest kernel:
```
**wget http://dl.dropboxusercontent.com/u/47950494/upubuntu/kernel-3.11.6 -O kernel-3.11.6**
```
3. Give the executable permission to installation script:
```
chmod +x kernel-3.11.6
```
4. Run the installation script file:
```
sudo sh kernel-3.11.6
```
5. Now wait script to download kernel and to install it.
6. When everything is done just reboot your system, you can do that with command too:
```
sudo reboot
```

Is your sound working now?

SOURCE: upubuntu.com

---

### Post by jamisonwright on 2013-11-02
I did that, via the link you provided with your last post, Still had no sound after that, but I've bookmarked the website so I can get the most recent kernel updates and hope my sound card eventually gets supported.

---

### Post by olli-sylvanne on 2013-11-07
I had on my ASUS eeePc and Ubuntu 12.04 many promlems with video and sound. Then I deleted Rhythmbox music player and all problems vanished. I am a beginner, so cannot be sure for all the backgrounds for problems, but to me the culprit seems to be Rhythmbox.

---

