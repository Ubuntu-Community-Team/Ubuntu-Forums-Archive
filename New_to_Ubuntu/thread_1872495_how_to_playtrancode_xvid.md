---
title: "how to play/trancode xvid"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by nnjond on 2011-10-30
Hi,
I seem to have dl everything relevant to play/compose some xvid files but cant figure out how to do it?

Is there any guides you know of, or a line of Bash code?

Thanks

---

### Post by little_penguin on 2011-10-30
Here are some GUI programs:

To play the xvid files, you can use vlc.
To convert them to another format, there's avidemux, arista or winff, among others.
To convert them to DVD format to play on a standard DVD player, I like devede.

All of these can be installed from the repositories using the Ubuntu Software Centre or Synaptic.

---

### Post by nnjond on 2011-10-30
Thanks for your interest. I have these apps. Such as vlc. but can not figure out how to load them successfully?

---

### Post by Paqman on 2011-10-30
To play a file: either right-click on the file and "open with" > VLC, or hit the windows button and type VLC then click on the icon, then go to "file" and "open" in VLC.

To transcode a file, hit the windows button and type Arista and click. Likewise for Devede.

---

### Post by little_penguin on 2011-10-31
Certain codecs are not installed by default, so you might need to install ubuntu-restricted-extras.

In a terminal, you can install them with this command:

```
sudo apt-get install ubuntu-restricted-extras
```

Once they are installed, you can double-click the file and it should open with the default Movie Player (usually Totem).

---

