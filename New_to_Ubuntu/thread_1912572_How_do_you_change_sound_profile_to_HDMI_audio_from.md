---
title: "How do you change sound profile to HDMI audio from terminal?"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by WongFuChu on 2012-01-20
Is there a way to change the sound profile from the terminal and works under udev? I noticed that whenever my hdmi cable is plugged in, it doesn't change automatically, unlike the display. I found and tried something like:

```
pacmd "set-card-profile 0 output:hdmi-surround"
```

That worked in the terminal, but it didn't work in my script linked to my udev rules. Are there any other ways, particularly one that works under udev?

---

### Post by WongFuChu on 2012-01-21
Okay... I think I may have solved my own problem. Using something like this at the top of my script to set a variable for the username (something I found online):
```

USER="$(who | grep :0\) | cut -f 1 -d ' ')"
export XAUTHORITY=/home/$USER/.Xauthority

```

I used:
```

sudo -u $USER pactl set-card-profile 0 output:analog-stereo+input:analog-stereo

```

This worked to toggle between my HDMI audio profile and my laptop speakers. This also worked under my udev rules, which I was mostly happy about. However, I'm not sure about things that use sudo. I know when I'm using a terminal, it prompts for a password. Is "sudo -u" safe to use in scripts?

---

