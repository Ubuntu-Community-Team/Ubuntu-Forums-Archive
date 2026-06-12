---
title: "HOWTO: Software audio mixing with ALSA"
date: 2007-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Pesho on 2007-08-31
**The Problem**: Some distros don't configure correctly the sound system out of the box. More specifically - Debian and Ubuntu/Kubuntu. If your sound card doesn't support hardware channel mixing (most onboard sound chips used in laptops don't), then only one application can play/record sound at a time.

**Background Info**: Several years ago, in an attempt to solve this problem, sound servers (or daemons) were invented - e.g. ESD/EsounD (default in GNOME) and aRts (default in KDE). The idea behind sound daemons is that applications shouldn't access the sound card directly, but rather interact with the sound server, which in turn performs software channel mixing, and plays the resulting stream through OSS or ALSA.

This approach however is fundamentally wrong, and doesn't really solve the issue. It is assumed groundlessly that every application will use the same sound server, and not the sound system directly. Even a single application accessing the sound card directly is enough to prevent the sound server from working. Besides, both ESD and aRts have latency problems, which makes them unsuitable for a number of purposes, for example watching movies.

Fortunately, for quite some time now, the ALSA sound system itself has had built-in software channel mixing through the *dmix*, *dsnoop*, and *asym* plugins. It should be used automatically when hardware mixing is unavailable. But for some unknown reason in Debian and Ubuntu this is broken and doesn't work by default.

**The Solution**: Create the file */etc/asound.conf*:

```
gksudo gedit /etc/asound.conf
```

(if in KDE, try '*kdesu kate /etc/asound.conf*' instead)

Copy/Paste the following into the text editor:

```
pcm.my_card {
   type hw
   card 0
   # mmap_emulation true
}

pcm.dmixed {
   type dmix
   ipc_key 1024
   #  ipc_key_add_uid false   # let multiple users share
   #  ipc_perm 0666           # IPC permissions for multi user sharing (octal, default 0600)
   slave {
   pcm "my_card"
   #   rate 48000
   #   period_size 512
   }
}

pcm.dsnooped {
   type dsnoop
   ipc_key 2048
   slave {
   pcm "my_card"
   #   rate 48000
   #   period_size 128
   }
}

pcm.asymed {
   type asym
   playback.pcm "dmixed"
   capture.pcm "dsnooped"
}

pcm.pasymed {
   type plug
   slave.pcm "asymed"
}

pcm.dsp0 {
   type plug
   slave.pcm "asymed"
}

pcm.!default {
   type plug
   slave.pcm "asymed"
}
```

Save the file.

Configure your applications to use ALSA directly.

Restart.

All done. Enjoy :)

**P.S.** If still having problems with some applications, you could experiment with uncommenting some of the commented lines in the file.

**P.P.S.** For detailed explanation of what we just did, refer to [this page]("http://alsa.opensrc.org/index.php/Hardware_mixing%2C_software_mixing") from the unofficial ALSA wiki.

***Source***: [http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html](http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html)

---

