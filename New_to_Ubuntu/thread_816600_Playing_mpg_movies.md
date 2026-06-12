---
title: "Playing mpg movies"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Stargazer777 on 2008-06-02
Does anyone know how to play mpg movies? I click the movie I want to play and  a box comes up in totem movie player - "the playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed."
Any suggestions?

---

### Post by Maestro23 on 2008-06-02
Do you have restricted extras installed?

> sudo apt-get install ubuntu-restricted-extras

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats?highlight=(Restricted)|(Formats)#head-79bfba9a0e96d62a622a47430239a1d49454c953](https://help.ubuntu.com/community/RestrictedFormats?highlight=(Restricted)|(Formats)#head-79bfba9a0e96d62a622a47430239a1d49454c953)

---

### Post by Stargazer777 on 2008-06-02
Yes. I already have restricted extras uploaded.

---

### Post by lisati on 2008-06-02
Although aimed more at playing DVDs rather than files (DVDs commony use the mpg format), [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats]("https://help.ubuntu.com/7.04/musicvideophotos/C/video.html#video-badformats")might provide some clues. After setting up for DVDs on my Ubuntu machine (running 7.04) it can handle mpg files, including those on my HDD handycam.

---

### Post by Stargazer777 on 2008-06-02
Thank you but that didn't work. I did the commands and Its still not playing.

---

### Post by Maestro23 on 2008-06-02
Do you have win32codecs installed from the Medibuntu Repository?

[https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu))

---

### Post by Stargazer777 on 2008-06-02
I am having trouble downloading it. is there another way than through 
Application> Add/Remove...?

---

### Post by SunnyRabbiera on 2008-06-02
try using synaptic.
what is your issue with medibuntu?
what errors did it produce?

---

### Post by Stargazer777 on 2008-06-02
When I am in the Add/Remove Applications a window comes up with an error.

---

### Post by coubury on 2008-06-02
download vlc player

you can find it in synaptic

system --> Admin ---> synaptic package manager

---

### Post by lisati on 2008-06-02
> **Stargazer777 said:**
> When I am in the Add/Remove Applications a window comes up with an error.

That could be a sign that something essential is missing or damaged. Are you able to give a little bit more information on the exact error?

---

### Post by Stargazer777 on 2008-06-02
Its not playing in vlc. Could it be that I need to change some settings in it?

---

### Post by Maestro23 on 2008-06-02
> **Stargazer777 said:**
> Its not playing in vlc. Could it be that I need to change some settings in it?

Any other format play in vlc?

---

### Post by Stargazer777 on 2008-06-02
I tried to copy and past the error, but I think it just couldn't find Medibuntu.

---

### Post by Stargazer777 on 2008-06-02
I was able to play mp3's.

---

### Post by Maestro23 on 2008-06-02
> **Stargazer777 said:**
> I was able to play mp3's.

No other video format?

---

### Post by Stargazer777 on 2008-06-02
AVI's were also successful.

---

### Post by Stargazer777 on 2008-06-02
I just tried MPlayer and it came back "could not find codec for audio format  0x163".

---

### Post by Maestro23 on 2008-06-02
> **Stargazer777 said:**
> I just tried MPlayer and it came back "could not find codec for audio format  0x163".

In Mplayer, go into your Video/Audio settings.  If no Video, try "X11".  For Audio, try "Alsa".

*Just play around with the options for those two until you get video & sound.

---

### Post by Stargazer777 on 2008-06-02
They were already set to ALSA and X11. I downloaded a few players and all of them come back with a audio error.

---

### Post by Maestro23 on 2008-06-02
You still having trouble with the Medibuntu repository?

---

### Post by Stargazer777 on 2008-06-02
Yup. When I am in the website, I dont see a way (Link or otherwise) to download it. Just what its about.

---

### Post by Maestro23 on 2008-06-02
> **Stargazer777 said:**
> Yup. When I am in the website, I dont see a way (Link or otherwise) to download it. Just what its about.

You have to add the repository.  Check the section under "Adding Repository".  

Those commands need to be entered in a terminal.  Just copy and paste them.

---

### Post by cariboo on 2008-06-03
Go here and follow the instruction:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You'll have to open a terminal and then just copy the lines in the code box in to the terminal an press enter. Do each line seperately.

Once you have done this then open synaptic click the search button and enter w32codec. Once you found it right click on the package and mark it for installation. Click apply and then click apply agin on the window that opens.

Terminal is located in Applications|Accessories, and Synaptic is located in System|Administration

Good luck

Jim

---

### Post by Stargazer777 on 2008-06-03
This is what I get now.

The filename .mpg indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "ASF video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "ASF video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by Stargazer777 on 2008-06-04
Thanks for all the help but nothing worked. I am still having trouble, and I found out that dvds cannot be read.

---

