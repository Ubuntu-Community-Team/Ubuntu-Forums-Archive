---
title: "HOWTO: Fix Flash sound in Firefox"
date: 2006-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Kimm on 2006-07-16
**Note: This has only been tried in KDE, but it should work in Gnome as well**

Open up a terminal window and type:

**KDE**:
```
sudo kate /usr/bin/firefox
```

**Gnome**:
```
sudo gedit /usr/bin/firefox
```

Then find this line (line 42):
```

MOZ_PROGRAM="${MOZ_DIST_BIN}/firefox-bin"

```

Change it to this:

**KDE**:
```

MOZ_PROGRAM="artsdsp ${MOZ_DIST_BIN}/firefox-bin"

```

**Gnome**:
```

MOZ_PROGRAM="esddsp ${MOZ_DIST_BIN}/firefox-bin"

```

This will redirect Flash Sound to Artsd/ESD when it tries to access OSS Audio. You can now play other sounds while watching Flash movies in Firefox!

---

### Post by pantadeusz on 2006-07-16
When I do this on the up-to-date Dapper Gnome, my Firefox doesn't start.

However, this fix works for me: [http://www.ubuntuforums.org/showthread.php?t=204022](http://www.ubuntuforums.org/showthread.php?t=204022)

---

### Post by remusus on 2006-07-16
If you have ALSA set up correctly (either have hardware mixing or have .asoundrc set up for software mixing), you can install the alsa-oss package and just use "aoss" for even better results... the sound will actually be in sync!

---

