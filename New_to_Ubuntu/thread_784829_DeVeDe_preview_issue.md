---
title: "DeVeDe preview issue"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by DestroyMicroshaft on 2008-05-06
Ok heres the problem, I use devede regularly, I just put a fresh install of hardy on my pc, and when I go to preview a movie before I make it mplayer doesnt start to actually the movie. I can here the movie previewing, but no video nothing opens up. Any ideas here?

---

### Post by macaholic on 2008-05-06
Do any other videos work in mplayer? What is the command line output if you manually play the temporary file in mplayer? Probably a codec issue. Have you installed ubuntu-restricted-extras?

---

### Post by tjwoosta on 2008-05-06
i had the same problem with gutsy

it turned out that i cant use mplayer on my computer (dunno why)

the only movie player that i can get to work with my laptop is

GNOME Mplayer

i dont know what the difference is between gnome mplyaer and regular mplayer but everything works now 

the only thing is devede always tries to open previews with the regular mplayer Which doesnt work for me so i have to save previews to desktop and click the icon to make them open with the correct movie player

---

### Post by DestroyMicroshaft on 2008-05-06
I just tried two movies, one in avi, and one in mp4 format, and neither of the videos started, I got a message that says fatal error  error opening/initializing the selected video_out (-vo) device. Once I hit ok, the audio window disappears but the audio begins playing.

---

### Post by macaholic on 2008-05-06
> **tjwoosta said:**
> i had the same problem with gutsy

it turned out that i cant use mplayer on my computer (dunno why)

the only movie player that i can get to work with my laptop is

GNOME Mplayer

i dont know what the difference is between gnome mplyaer and regular mplayer but everything works now 

the only thing is devede always tries to open previews with the regular mplayer Which doesnt work for me so i have to save previews to desktop and click the icon to make them open with the correct movie player
Gnome-mplayer is just a GUI frontend for mplayer, it uses the mplayer backend and controls it via Dbus calls if I remember correctly. I'm not sure why mplayer would not work for you yet gnome-mplayer would, perhaps a settings issue of some sort?

---

### Post by DestroyMicroshaft on 2008-05-06
> **tjwoosta said:**
> i had the same problem with gutsy

it turned out that i cant use mplayer on my computer (dunno why)

the only movie player that i can get to work with my laptop is

GNOME Mplayer

i dont know what the difference is between gnome mplyaer and regular mplayer but everything works now 

the only thing is devede always tries to open previews with the regular mplayer Which doesnt work for me so i have to save previews to desktop and click the icon to make them open with the correct movie player

Sorry bout the double post, but mplayer has always worked on my pc, this is the fourth Ubuntu version, and only on this one am I having the problem.

---

### Post by macaholic on 2008-05-06
> **DestroyMicroshaft said:**
> I just tried two movies, one in avi, and one in mp4 format, and neither of the videos started, I got a message that says fatal error  error opening/initializing the selected video_out (-vo) device. Once I hit ok, the audio window disappears but the audio begins playing.
Try switching video devices/outputs in the mplayer settings.

---

### Post by DestroyMicroshaft on 2008-05-06
Ok I solved the problem, and Im going to post the solution, incase someone else has this problem. All I did was change the default video out driver in mplayer.conf to xll, and bam video preview in devede again. Thanx to those who tried to help.

---

### Post by tjwoosta on 2008-05-06
ha.. you know what

after you posted that i just remembered why GNOME Mplayer works for me and regular MPlayer dont

im not smart enough to find the mplayer.conf file to change the video output in Mplayer, but with GNOME Mplayer i was able to go to the preferences menu and change the video output to x11.

i wish i had remembered this in time to help


if you dont mind could you tell me where i could find the mplayer.conf file and how to change the output?

EDIT: nevermind i found it    /etc/mplayer/mplayer.conf

---

### Post by macaholic on 2008-05-07
> **DestroyMicroshaft said:**
> Ok I solved the problem, and Im going to post the solution, incase someone else has this problem. All I did was change the default video out driver in mplayer.conf to xll, and bam video preview in devede again. Thanx to those who tried to help.
Don't take this the wrong way, but I think that's exactly what I told you to do is it not?

---

