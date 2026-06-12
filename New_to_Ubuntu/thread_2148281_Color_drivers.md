---
title: "Color drivers?"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by gaitedlady on 2013-05-24
Hi everyone! 

I have a question.... After successfully upgrading my system the other night, from 11.10 to 12.04LTS, I think I might be missing something.... a color driver?

Let me explain. My color covers are not appearing properly on my screen when I open the file. The cover of the current release is my background, and it looks fine. All the thumbnails appear fine. If I click on that thumbnail to open the cover, what appears is a red-gray-black scale image of my cover.

I hope that made sense. Is there something I need to add or fix to correct this image problem

I'm working with a graphics designer who is a dragon and I have to go over the details on the upcoming covers for the series and need to see the right colors before I can make a list for her. Before I poke that dragon I want make absolutely certain of the corrections I want her to make.

Did that make sense? Can someone talk me through this?

Thanks!

Sandy

---

### Post by Frogs Hair on 2013-05-24
> I hope that made sense.

Not to me, I don't know what a color driver is. Do you mean Graphics driver ?    


> My color covers are not appearing properly on my screen when I open the file.

What are color covers ? 

> [COLOR=#000000]I'm working with a graphics designer who is a dragon[/COLOR]

 :confused:

---

### Post by gaitedlady on 2013-05-24
I'm sorry I wasn't clearer.

Color covers for my novels. I write fiction.

The color on the images of the covers are not coming through. I don't know what's causing it, because the thumbnails are perfectly nice, as is the cover I'm using as a screensaver/background. When I open the folder containing the covers for this series, the thumbnail images appear normal. When I click on those thumbnails the image that opens is various shades of red and gray. Something isn't registering or working correctly since the upgrade to 12.04LTS.

If there's something else I need to download or adjust, in order for the covers to appear correctly, could someone please tell me? I have to have to get back with my graphics designer soon to finalize the cover for the third book in this series which is scheduled for release in late July. She isn't exactly the easiest graphics artist I've worked with, but she is damn near the best at what she does and that's why I continue to deal with her. 

Sandy

---

### Post by Frogs Hair on 2013-05-24
It reads like the file thumbnails are fine , but when  opened in image viewer they are distorted . Is this correct ?  Is this an upgrade or clean installation ? I ask because people interchange the term.

---

### Post by gaitedlady on 2013-05-24
Yes. That's it.

It was an upgrade from 11.10 to 12.04LTS.

I was wondering about something and not sure if this might be the problem.... Could there be something wrong with the .jpeg viewer?

---

### Post by Frogs Hair on 2013-05-24
I was about to suggest re-installing the image viewer / eye of gnome. Open the terminal and copy paste and enter the following. I think the images are fine and the viewer is not. See how they look in Shotrwell the default photo manager.    

```
sudo apt-get install --reinstall eog 
```

---

### Post by gaitedlady on 2013-05-24
(Please don't laugh, but....) How do I open the terminal?

---

### Post by deadflowr on 2013-05-24
ctrl + alt + T should open a terminal.
Or open the dash with the windows-icon-looking key on your keyboard and type 'terminal'.

---

### Post by gaitedlady on 2013-05-24
WOW! I found it..... It looks great in Shotwell and in Firefox. Is there a way to fix the .jpg or is the Shotwell my new image viewer?

---

### Post by Frogs Hair on 2013-05-24
> **gaitedlady said:**
> WOW! I found it..... It looks great in Shotwell and in Firefox. Is there a way to fix the .jpg or is the Shotwell my new image viewer?

Open the details application and under default applications > photos select Shotwell from the drop-down menu .

---

### Post by gaitedlady on 2013-05-24
How do I get to that screen?

---

### Post by Frogs Hair on 2013-05-24
Type the word details into dash or use the gear icon on the top right panel and select system settings from the menu .

---

### Post by gaitedlady on 2013-05-24
Frogs Hair,
Thank you so very much. It worked, and I very much appreciate your assistance.
Sandy

---

### Post by Frogs Hair on 2013-05-24
Your'e Welcome ! The dragon comment was pretty funny ! :D

This may come in handy ! [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)

---

