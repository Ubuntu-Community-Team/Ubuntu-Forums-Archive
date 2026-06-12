---
title: "Pulseaudio control volume for single application"
date: 2010-05-03
forum: Programming Talk
---

### Post by durus on 2010-05-03
I need to control the volume for an application without affecting the other applications. Like gnome-volume-control application tab where you can change the volume for every application using pulse audio.
I have googled about this and tried to use pacmd without any success. Can you please help me?

---

### Post by ajgreeny on 2010-05-03
Install **padevchooser** from the repos.  This has the **pulseaudio-volume-control** included and should help.  I can never understand why it is not installed by default when pulse is the default sound server in ubuntu now.

---

### Post by durus on 2010-05-04
Thank you. What I ment is that I am writing an application so I need to be able to do this from my application and need to undestand how I can do this truough some API

---

### Post by P4man on 2010-05-04
Its pulseaudio that allows this. It will allow it for any application even those using alsa or oss, by creating several alsa sinks and sources for each app. You dont have to do anything special for it when writing the app.

If you dont have pulseaudio (or a similar sound server) on the system there is no way you can do this. For alsa and oss alone you'd be lucky to be able use the soundcard without muting all the other apps.

---

### Post by durus on 2010-05-04
I am using an application for music streaming that sometimes have commercials. What I want to do is to write an application that lower the volume in pulse audio for that application when the commercial is playing. I have managed to write an application that does this but for the global sound using ```
subprocess.Popen("pacmd set-sink-volume 0 " + str(HIGHERVOLUME) + " > /dev/null", shell=True);
```
I do only want to lower the sound for this single application and I know that it is possible since you can do this through the GUI in gnome-volume-control.
The reason for why I want to lover the sound and not mute is because the application is smart enough to pause the commercial if the sound is muted or to low.

---

