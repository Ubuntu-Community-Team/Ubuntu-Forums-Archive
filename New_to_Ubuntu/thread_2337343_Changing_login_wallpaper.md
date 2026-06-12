---
title: "Changing login wallpaper"
date: 2016-09-16
forum: New to Ubuntu
---

### Post by DrRus on 2016-09-16
Can anyone post a working solution as to how to change the background of the log-in screen to be different from your wallpaper?

So far, everything I've tried has changed only the background when I select "Guest", but not under my username.

Thanks!

---

### Post by yetimon_64 on 2016-09-17
> **DrRus said:**
> Can anyone post a working solution as to how to change the background of the log-in screen to be different from your wallpaper?

So far, everything I've tried has changed only the background when I select "Guest", but not under my username.

Thanks!

To set a permanent custom log in screen image I saved a file in /usr/share/backgrounds and set its ownership to root with "644" permissions. (Let me know if you need more in depth instructions to do so, that is if you want to attempt to actually change the log in screen image to a custom one).

Then on 14.04 I followed [[COLOR=#0000ff]--this--[/COLOR]]("http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-change-login-screen-background-remove-the-white-dots/") post on [noparse]ubuntuhandbook.org[/noparse], and in the dconf-editor settings set the "background" field to use my image.

This is what my custom log in screen now looks like ...
[ [IMG]https://dl.dropboxusercontent.com/u/30874719/UF/Deskshots/2_Unity-greeter_thm.jpg[/IMG]]("https://dl.dropboxusercontent.com/u/30874719/UF/Deskshots/2_Unity-greeter.jpg")

**_A word of warning_** The instructions in the [noparse]ubuntuhandbook.org[/noparse] link above are running as root user initially and then switching to the user lightdm to do the alterations in the dconf-editor. Read the instructions very carefully and fully before attempting. It is possible to totally scramble your log in screen display if you make a mistake, I did so on my previous 14.04 install. This is the second time I've used those instructions but now I've learnt to do so a bit more carefully :).

If you want to only stop the log in screen using your wallpaper and not set a custom image I'd try the command in terminal ...
```
gsettings set com.canonical.unity-greeter draw-user-backgrounds false
```

If the above command as your own user fails to change the behaviour of using your desktop image try following the link above and when you open dconf-editor as the lightdm user only change the "draw-user-backgrounds" setting by deticking it.

Let us know what version you are running, I am not sure if the process is the same on 16.04. I haven't tried to change the image there as I have set 16.04 to boot to a tty screen only and then I boot into the GUI with auto login set; as a result I don't get to see the unity greeter log in page because of my "non standard" set up.

Good luck, yeti.

---

### Post by sukanime on 2016-09-17
i just want to say thanks... i like to change the backgroud to anime related images, it's helped me... (now using Yin from Darker than black and all chara in one piece in alabasta arc)

---

### Post by DrRus on 2016-09-17
Thanks Yetimon, works perfectly!

---

