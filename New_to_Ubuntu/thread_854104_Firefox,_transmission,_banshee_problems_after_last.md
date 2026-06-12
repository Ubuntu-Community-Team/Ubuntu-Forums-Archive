---
title: "Firefox, transmission, banshee problems after last update"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by matyasfalvi on 2008-07-09
Hi!

I am new to Ubuntu. Everything was working fine until the last update I did on july 7th 2008. Since then I experience difficulties in the following fields:

1. Firefox a, the back button doesn't work b, I cannot play videos from youtube

2. Transmission gives error warning: "Failed to load torrent file:([torrent path]): not a valid torrent file"

3. Banshee just stopped  working I cannot play any songs

4. Rhythmbox is working however if used parallel with firefox (when trying to watch a video on youtube) it doesn't work either.

After I did the update I didn't restart the computer asap could that be the problem? How can it be fixed?

Thank you!

---

### Post by billgoldberg on 2008-07-09
> **matyasfalvi said:**
> Hi!

I am new to Ubuntu. Everything was working fine until the last update I did on july 7th 2008. Since then I experience difficulties in the following fields:

1. Firefox a, the back button doesn't work b, I cannot play videos from youtube

2. Transmission gives error warning: "Failed to load torrent file:([torrent path]): not a valid torrent file"

3. Banshee just stopped  working I cannot play any songs

4. Rhythmbox is working however if used parallel with firefox (when trying to watch a video on youtube) it doesn't work either.

After I did the update I didn't restart the computer asap could that be the problem? How can it be fixed?

Thank you!

1) Remove firefox and reinstall it using this command:

```
sudo apt-get autoremove firefox --purge
```

Then reinstall with the following command

```
sudo apt-get install firefox
```

It would be best at this stage to reinstall the ubuntu-restricted-extras packages to get flash working (amongst other things).

```
sudo apt-get install ubuntu-restricted-extras
```

2) I don't have an idea. Transmission seems to think it is a invalid torrent file.

If you can't fix it, remove transmission and install another client like "deluge"

```
sudo apt-get autoremove transmission --purge
```

```
sudo apt-get install deluge
```

3) Reinstall it.

```
sudo apt-get autoremove banshee --purge
```

```
sudo apt-get install banshee
```

4) This is because of PulseAudio. 

The easiest way to fix this is by removing PulseAudio and use ALSA instead.

Go to "system -> preferences -> sound" and switch everything to ALSA.

After you done so, remove pulseaudio

```
sudo apt-get autoremove pulseaudio --purge
```

It could be that you'll need to log out and back in again.

--

Hope this helped

note: these commands need to be entered in the terminal. You can find it under "applications -> accessories -> terminal".

---

### Post by matyasfalvi on 2008-07-12
Hi!

Thank you very much for the fast reply and help. I encountered some problems, during the restricted extras install however everything works fine now so thank you again.

I had some problems with my x-ttcidfont-conf package. So I tried to install it with code: sudo apt-get install x-ttcidfont-conf but some kind of error came up during the installation as well. I attached the pictures of the error message.

Thanks for all the help again.

---

