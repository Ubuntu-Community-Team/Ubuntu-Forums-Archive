---
title: "create flv video (for youtube) with a pic and mp3 file in ubuntu"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by arai on 2013-03-10
Is it possible to create a flv video in Ubuntu with a picture and an mp3 file. I want to make a video and upload to youtube. 

How to make this happen? I am having ubuntu 12.04. I don't have windows in my system.

thanks in advance.

---

### Post by rocketfish201 on 2013-03-10
You could try OpenShot ```
sudo apt-get install openshot
```

---

### Post by Laobi on 2013-03-10
Besides OpenShot, you can do it with PhotoFilmStrip and even Avidemux, too. All these applications are in the repositories so you can easily install them.

---

### Post by arai on 2013-03-10
Sorry for asking this. I installed openshot. created a new project. added an mp3 file and a pic from the import files. How to make the mp3 file play with the image in the background displayed throughout the song. 

thanks again for suggesting the tools and the workaround.

---

### Post by Laobi on 2013-03-10
Did you put the audio and image on the timeline? If you didn't, grab the audio file in the import panel and drag it to the timeline - to Track 1, aligning it at the beginning. Do the same for image file, except drag this one to Track 2.

 Now right click at the audio part (track 1) on the timeline and select 'Properties', click the 'Length' tab and see what is the length of the audio and close the dialog. Then right click at the image part on the timeline (track 2), select 'Properties' then select the 'Length' tab and in the 'Out' field enter the number of seconds your audio file was long and close the dialog.

 You should now have audio and video part be of the same length, so go to 'Export video', choose the encoding you want and you're done.

---

