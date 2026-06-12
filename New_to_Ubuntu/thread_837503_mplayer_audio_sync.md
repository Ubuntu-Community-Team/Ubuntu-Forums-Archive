---
title: "mplayer audio sync"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by hardyheronnewb on 2008-06-22
Hello all,
I recently switched to latest release of ubuntu from windows and I like using my machine for tons of media playing and recording. However, whenever I had an issue with out of sync audio in windows I would always use media player classic. In hardy heron, I have thus far installed mplayer, smplayer (to have an interface, for some reason I thought mplayer would work better if I say the commands in a gui format, I was wrong and it screwed up the video for that particular movie and made it look tooooo saturated), and vlc. all of these play the movie and the audio, but the audio is variable, in that sometimes it seems its 4 seconds ahead and other times maybe 10. Please help me here. 

With mplayer I have tried both the + and - and the -autosync command. Maybe I am not using that one correctly, here is the syntax I use:

gmplayer -autosync (have tried 0, 1, 30 and numbers in the thousands as I did not notice a difference with any of them regardless) filename

---

### Post by hardyheronnewb on 2008-06-22
also, i asked someone who told me i need the drivers for the cards installed, i am running on the integrated audio and video cards on the dell optiplex gx520. i am unable to find any drivers for these.

---

### Post by rvm4000 on 2008-06-22
> **hardyheronnewb said:**
> In hardy heron, I have thus far installed mplayer, smplayer (to have an interface, for some reason I thought mplayer would work better if I say the commands in a gui format, I was wrong and it screwed up the video for that particular movie and made it look **tooooo saturated**), 

I think that's fixed since smplayer svn r1371.
[ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)

> **hardyheronnewb said:**
> 
and vlc. all of these play the movie and the audio, but the audio is variable, in that sometimes it seems its 4 seconds ahead and other times maybe 10. Please help me here. 

Try the framedrop option. Also be sure you're using xv and not x11.

---

### Post by hardyheronnewb on 2008-06-22
[ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)
sorry, i went to above link and did not see 1371... did i misunderstand you? also, when you say to use xv, will i have to specify that each time i play a vid?
thank you.

---

### Post by rvm4000 on 2008-06-22
> **hardyheronnewb said:**
> [ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/)
sorry, i went to above link and did not see 1371...

It was fixed in r1371, of course a newer version has that fix. You can use r1442.

> **hardyheronnewb said:**
>  did i misunderstand you? also, when you say to use xv, will i have to specify that each time i play a vid?
thank you.

In smplayer, open the preferences dialog, and be sure you've got xv selected as video output driver. It's much faster than x11. I would also recommend to use alsa as audio driver instead of pulse.

If that doesn't fix the sync problem, go to the performance section in preferences and check the "framedrop" option. That would make mplayer to drop frames from time to time to keep A-V synchronization.

---

### Post by hardyheronnewb on 2008-06-22
> **rvm4000 said:**
> It was fixed in r1371, of course a newer version has that fix. You can use r1442.

I already had that version installed. It seems, when I play the video through mplayer and in command line insert video codec as gl, it fixes the saturation issue, but in smplayer when i set it to gl, video stops all together, will not restart when I reopen file. 

> **rvm4000 said:**
> In smplayer, open the preferences dialog, and be sure you've got xv selected as video output driver. It's much faster than x11. I would also recommend to use alsa as audio driver instead of pulse.

Same thing here, I was using alsa with mplayer and it does not fix sync issue in either smplayer or mplayer.


> **rvm4000 said:**
> If that doesn't fix the sync problem, go to the performance section in preferences and check the "framedrop" option. That would make mplayer to drop frames from time to time to keep A-V synchronization.

I also had this option checked from beginning and it did not help. I am thinking it is this video only that is the issue, maybe I will find a different version of it and then I will not have to jump around trying to watch just this single vid.

---

### Post by rvm4000 on 2008-06-22
> **hardyheronnewb said:**
> I already had that version installed. It seems, when I play the video through mplayer and in command line insert video codec as gl, it fixes the saturation issue, but in smplayer when i set it to gl, video stops all together, will not restart when I reopen file. 

If you take a look at the mplayer log (Options->View logs) you'll probably see there an error message telling why gl is not working.

Anyway I think the saturation problem could be fixed using the video equalizer.

> **hardyheronnewb said:**
> 
I also had this option checked from beginning and it did not help. I am thinking it is this video only that is the issue, maybe I will find a different version of it and then I will not have to jump around trying to watch just this single vid.

If you see that the audio delay is constant, you can use then Delay+ and Delay- options in the Audio menu to fix the sync problem in that video.

---

### Post by hardyheronnewb on 2008-06-22
> **rvm4000 said:**
> 
Anyway I think the saturation problem could be fixed using the video equalizer.

I don't think that it is only saturation is affected, it seems that I would have to mess around with the equalizer quite a bit to get it to fix the issue, it does it for all other vids as well (the audio is fine in those).



> **rvm4000 said:**
> If you see that the audio delay is constant, you can use then Delay+ and Delay- options in the Audio menu to fix the sync problem in that video.

Thats the thing, the delay is not constant, hence, I will take a look at the log to see what the error message is and post here. Thank you.

---

### Post by hardyheronnewb on 2008-06-27
I got a different version of the video. I believe that there was some original audio encoding issue. Thank you for the help tho.

---

