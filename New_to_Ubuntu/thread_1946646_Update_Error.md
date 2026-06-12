---
title: "Update Error"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-03-25
I am getting the following error while updating. What is going wrong ?

"checkbox checkbox-gtk chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg gstreamer0.10-gconf gstreamer0.10-plugins-good gstreamer0.10-pulseaudio language-pack-gnome-zh-hans language-pack-gnome-zh-hans-base language-pack-zh-hans language-pack-zh-hans-base libfreetype6 libpng12-0 midori software-center thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-zh-cn thunderbird-locale-zh-hans xserver-xorg-video-openchrome"

---

### Post by Elfy on 2012-03-25
What error - that's just a list of packages?

Post the whole thing.

---

### Post by 3dmatrix on 2012-03-25
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

"checkbox checkbox-gtk chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg gstreamer0.10-gconf gstreamer0.10-plugins-good gstreamer0.10-pulseaudio language-pack-gnome-zh-hans language-pack-gnome-zh-hans-base language-pack-zh-hans language-pack-zh-hans-base libfreetype6 libpng12-0 midori software-center thunderbird thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-zh-cn thunderbird-locale-zh-hans xserver-xorg-video-openchrome"

---

### Post by matt_symes on 2012-03-25
Hi

Close update manager.

Open a terminal and type

```
sudo apt-get update
```

Post the output back here between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

That should give a better idea of the key problem.

Kind regards

---

