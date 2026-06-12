---
title: "No HDMI Sound when connected to external monitor"
date: 2017-05-05
forum: New to Ubuntu
---

### Post by gil80 on 2017-05-05
Hi all,

Using ubuntu for about a month now, I was able to update drivers so this laptop would use it's discrete nVidia GPU, however I do not have HDMI sound.

What should I post here in order to get some help and resolve this issue?

The laptop is connected to my LG TV and I use it sometimes as a media streamer, therefore I would like to have the sound working via HDMI.

Thanks!

EDIT: According to this link [http://forum.notebookreview.com/threads/m11x-r3-internal-sound-card.583615/](http://forum.notebookreview.com/threads/m11x-r3-internal-sound-card.583615/) I might have Waves Maxx audio board.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC665 Analog [ALC665 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

EDIT2: Upgraded to 17.04 in hope to resolve this issue, but still the same.

---

### Post by Autodave on 2017-05-05
Have you looked in sound settings to make sure that the Nvidia HDMI has sound enabled? Secondly, do you know for a fact that the HDMI cable supports sound and has it been tried on another machine to make sure it works?

---

### Post by Geoffrey_Arndt on 2017-05-05
And selected hdmi output from the sound programs via "Settings" . . . . are you not seeing a second audio output on that screen?

---

### Post by gil80 on 2017-05-06
> **Autodave said:**
> Have you looked in sound settings to make sure that the Nvidia HDMI has sound enabled? Secondly, do you know for a fact that the HDMI cable supports sound and has it been tried on another machine to make sure it works?

> **Geoffrey_Arndt said:**
> And selected hdmi output from the sound programs via "Settings" . . . . are you not seeing a second audio output on that screen?

I do not see another option in the sound menu. Only 'internal speakers'.

Of course I test it when the HDMI cable is connected to the TV and the TV is on and set to the same HDMI port.

There is no option for HDMI sound anywhere in menus.

I know for a fact it's working because I have dual boot with windows 10 and I use this laptop with Kodi with the same cable.

---

### Post by lammert-nijhof on 2017-05-07
I would install 'pulse audio volume control'. It is another more detailed way of managing pulse audio sound. In the configuration tab you should see HDMI and "Built in Audio". If you don't see HDMI, you have a driver problem, but I see the HDMI from my old NVidia card in that tab. In my case it is not used (vga monitor) and has the status 'unplugged'. If you have that HDMI device, you have to make sure it is used. I assume you want to stream sound to the TV. I that case go to the 'play back' tab and when you are streaming, change the device that is used by your streaming application. If you want to use sound from the TV, go to the recording tab and change the device that is used by your streaming application. In both tabs the currently used device will be displayed in the button on the right of your application name. The pulse audio will remember your selections for the days and weeks to come.

---

### Post by gil80 on 2017-05-08
> **lammert-nijhof said:**
> I would install 'pulse audio volume control'. It is another more detailed way of managing pulse audio sound. In the configuration tab you should see HDMI and "Built in Audio". If you don't see HDMI, you have a driver problem, but I see the HDMI from my old NVidia card in that tab. In my case it is not used (vga monitor) and has the status 'unplugged'. If you have that HDMI device, you have to make sure it is used. I assume you want to stream sound to the TV. I that case go to the 'play back' tab and when you are streaming, change the device that is used by your streaming application. If you want to use sound from the TV, go to the recording tab and change the device that is used by your streaming application. In both tabs the currently used device will be displayed in the button on the right of your application name. The pulse audio will remember your selections for the days and weeks to come.

do you mean that only when I stream something, I should then see the HDMI out sound option? If this is the case, I will try it. But it's a very dumb implementation of HDMI sound feature.


Otherwise, I think it's a driver issue, because I do check for the sound menu when the HDMI cable is connected and the TV is on and is set to the HDMI input source.
But when I play a youtube video, I can't hear anything.


I did install pulse audio, it didn't show the HDMI option.

---

### Post by Autodave on 2017-05-08
The sound for the HDMI comes through the video card. What video card are you running? Did you enable the sound on the card? What Nvidia driver are you using and from where did you obtain it?

---

### Post by Geoffrey_Arndt on 2017-05-08
OK, at our PC club, we turn on the TV and set it hdmi3, the specific port we have the cabled plugged into.   Then, with my laptop running, I connect the  other end of hdmi cable to hdmi port on laptop.   

After about 3 or 4 seconds, we get hdmi video on the TV but no sound.   So then, I go to the audio option via the standard "settings" app in ubuntu, and change the sound source to hdmi from internal speakers.   Voila - - we have sound and video!

PS:   By the way, all our Club systems run all Intel machines (Intel cpu, Intel Wireless, Intel Video and Intel Sound) - - - makes things extremely simple (but I would still think procedure is similar for nvidia - perhaps requiring a tweak via the nVidia console).

EDIT:    re your soundcard . . . yes . . .  it seems the realtek wave is not well supported bt realtek for any unix/linux device.    See my sig, below for best solution . . . .

---

### Post by lammert-nijhof on 2017-05-08
You can use the standard sound indicator, if you want to change the audio source each time manually. You use 'pulse audio volume control', if you want the system to automatically select the audio source based on the program that is running or if you want to use both audio sources at the same time for different applications, e.g. you want to Skype or chat while watching TV. 

Another important difference is, that the "standard settings" in my case does not display my HDMI sound from the Video card anywhere. When I'm in 'pulse audio volume control', it does show the HDMI audio in the configuration tab.

If your HDMI is not displayed in the mentioned configuration tab you probably have a driver problem. You could try one of the other drivers in the 'software & updates' settings.
In my 'software & updates' I have a choice between 3 drivers, 2 binary drivers from nvidia and the default Linux nouveau driver. I have chosen the newest nvidia driver. If you already have selected the best nvidia driver, my knowledge is finished, but you could try to google and find pages with the same problem like this one:  [https://h30434.www3.hp.com/t5/Notebook-Audio/Nvidia-HDMI-Output-quot-Not-plugged-in-quot-Audio-not-going/td-p/981923](https://h30434.www3.hp.com/t5/Notebook-Audio/Nvidia-HDMI-Output-quot-Not-plugged-in-quot-Audio-not-going/td-p/981923)

---

### Post by gil80 on 2017-05-08
> **Autodave said:**
> The sound for the HDMI comes through the video card. What video card are you running? Did you enable the sound on the card? What Nvidia driver are you using and from where did you obtain it?

It's an [B]Nvidia GeForce GT 540M
[/B]
I installed its drivers via the setting panel > additional drivers or something like that name. I selected the propriety, tested, also labeled as (recommended).

---

