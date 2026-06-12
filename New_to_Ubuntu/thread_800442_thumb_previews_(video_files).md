---
title: "thumb previews (video files)"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-19
I've read all the tutorials on this forum and others describing how to get nautilus to display a thumbnail preview for video files.

I have xine-movie player and totem-xine installed, but I use gnome-mplayer to play the movies.


any ideas? :confused:

---

### Post by m_ad on 2008-05-20
bump, anyone know how to do this?

---

### Post by m_ad on 2008-05-20
weird. I'm trying to enable the video previews on an external hd (WD Passport), but when I moved the video files over to my /home/me folder, the preview worked :confused:

this is really starting to annoy me :mad:


any ideas on how to enable Nautilus to show thumbnail preview on an external hd? all options are the same in Edit->Preferences.

---

### Post by tszanon on 2008-05-20
I'm not at home right now, so I can't help much.
But, if I recall correctly, what you need is under Preferences. There's a tab where you specify these things, like if nautilus should show a preview thumbnail of files in remote drives. Maybe it's treating your external drive as a remote drive?

As i said before, I'm not at home, so I don't remember all details about it. But I believe I'm not far from being correct.

---

### Post by m_ad on 2008-05-20
thanks for the reply. I'm not seeing anything other than "Show thumbnails: " under "Preview" tab in Preferences. I set that to "Always" rather than "Local files Only."

---

### Post by m_ad on 2008-05-20
problem solved. after I enabled "Always" for preview movie files, I had to remove my .thumbnails folder :lolflag:

---

### Post by themunkee on 2008-05-20
I had this problem once I upgraded to Hardy. I now have it working - I realised that the codecs for Totem were not installed for the video files.

* Try and play the video files in Totem, install any codecs it says you may need.
* Delete ~/.thumbnails
* Refresh

---

### Post by Jenga-kun on 2008-06-01
I'm in Gutsy and I've installed the necessary codecs for totem but I don't know how to delete .thumbnails.

---

### Post by unutbu on 2008-06-01
Click on Applications>Accessories>Terminal. Type
```
cd
mv .thumbnails .thumbnails-bak
```

This will move the .thumbnails directory to one called .thumbnails-bak. This is effectively the same as deleting .thumbnails, but safer. Once you get things working the way you want, you can remove the .thumbnails-bak directory by typing

```

rm -rf ~/.thumbnails-bak
```

---

