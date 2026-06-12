---
title: "Very strange Ubuntu 20.04 LTS audio issues"
date: 2020-05-26
forum: New to Ubuntu
---

### Post by lovo2 on 2020-05-26
I installed 20.04 as dual-boot and have both windows 10 and ubuntu working fine. At first boot; ubuntu recognised my audio output device as '**headphones**' and not speakers and so i was getting no sound. 

(NOTE: I also had this same issue on my first install of windows 10 but i performed a rollback driver from the default **'conexant cx20751/2' **to a previous driver. The rolling back of the driver caused 2 audio output device options simply labelled **'speakers'** and **'headphones' **on windows 10. after rolling back driver on win10 it defaulted the audio output device to '**headphones**'. So i had to **manually** **choose** audio output to '**speakers**' which solved it on windows)

Now, on first boot of ubuntu i had the same issue; where the **automatic audio output device selected was 'headphones****'** and therefore was getting no sound. On **'sound settings' **i couldn't change audio output device at all; the only option was **'Headphones'** .No **'speakers' **option was available.

Using Pulse Audio volume, however, it recognised a **'speakers (unavailable)' **option **AS WELL AS** the '**headphones'.**.. but still no sound when this **'speaker (unavailable)' **was selected as the **audio output device.**

I proceeded to remove, re-install, and update so many different audio options through terminal ; desperately following different peoples advices and fixes. always making sure to Re-boot ubuntu every time i made a change. 
Nothing worked and i was afraid i had messed  with way too many options. Keep in mind i have NO clue how to use ubuntu as of yet. 

So, i booted up ubuntu one more time and to my surprise; i can hear sound now! :/ 

**BUT**

I** cant hear any system sounds** at all but i can hear audio perfectly fine when  watching a youtube video for example. When i **'test speaker R L' **on  sound settings there is no sound response...

In **alsamixer** i can change the** 'sound card'** via F6 from **'Intel haswell HDMI'** to  **'conexant cx20751/2' **and vice-versa yet the sound still works no matter which one i use(?)...
I dont know how i got here and what i did... 
i would greatly appreciate what you think made the sound work (for my own future reference). i have rebooted my laptop a couple times now and it seems the sound is  still working but im not satisfied because i want to know:
1) what exactly fixed this issue?
2) how can i **undo all of the other settings** that i tinkered about with? i would like to reset all other audio settings i may have fudged up so i dont have other issues with other installations further down the road.
I did tinker with alot of terminal commands that i have no idea about as i was desperate to fix this audio issue.

System Details: Lenovo z50-70 i7 2ghz 8gb ram 500gb SSD
sound cards available: **'Intell haswell HDMI' **and** 'conexant cx20751/2'** ---

i retraced some steps and here are some of the following commands i ran to try and fix the audio. i did try a multitude of different commands and some i forgotten. 
[COLOR=#c20cb9][B]
sudo[/B][/COLOR] alsa force-reload
[COLOR=#c20cb9][B]
sudo[/B][/COLOR] apt remove [COLOR=#660033]--purge[/COLOR] alsa-base pulseaudio [COLOR=#c20cb9]**sudo**[/COLOR] apt [COLOR=#c20cb9]**install**[/COLOR] alsa-base pulseaudio

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

Honestly, i did a bunch more commands that where recommeneded on different forums; but i cant find the exact ones (sorry).


Can someone shed any light on any of this? Appreciate any feedback

---

