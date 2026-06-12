---
title: "HOWTO: Script - Set the default &quot;Open with&quot; application"
date: 2005-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jiyuu0 on 2005-06-22
These instructions will set the default "Open with" application:
All Graphics -> gthumb
All Multimedia -> XINE
mp3,wma,wav,m3u -> XMMS

01) You need to install XINE and XMMS first, read:
[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)
[http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)

02) **gedit $HOME/associate.sh**

03) Copy and paste the code below into new file:
```

rm $HOME/.local/share/applications/* 2>/dev/null

# associate XMMS for mp3 files
mv /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup 2>/dev/null
sed -e 's/audio\/mpeg=totem.desktop/audio\/mpeg=XMMS.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list

# associate XMMS for m3u files
mv /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup 2>/dev/null
sed -e 's/audio\/x-mpegurl=totem.desktop/audio\/x-mpegurl=XMMS.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list

# associate XMMS for wav files
mv /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup 2>/dev/null
sed -e 's/audio\/x-wav=totem.desktop/audio\/x-wav=XMMS.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list

# associate XMMS for wma files
if [ "$(grep wma /usr/share/applications/mimeinfo.cache)" == "" ]; then
  echo "application/x-extension-wma=XMMS.desktop" >> /usr/share/applications/mimeinfo.cache
fi

# associate XINE for all multimedia files
rm -fr /usr/share/applnk/Multimedia/xine.desktop
ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
mv /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup 2>/dev/null
sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list

# associate gthumb for all graphic files
mv /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup 2>/dev/null
sed -e 's/eog.desktop/gthumb.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
mv /tmp/defaults.list /usr/share/applications/defaults.list

killall nautilus

```

04) Save and close the new file

05) **sudo sh $HOME/associate.sh**

This should do the trick :-)

---

### Post by bunced on 2005-06-22
Very useful, thank you

---

### Post by Sionide on 2005-06-23
Useful, except I somehow broke my XMMS :(

---

