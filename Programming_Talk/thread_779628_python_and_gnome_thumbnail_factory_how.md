---
title: "python and gnome thumbnail factory: how?"
date: 2008-05-02
forum: Programming Talk
---

### Post by | MM | on 2008-05-02
In python am i able to utilise gnome's thumbnail factory?  

I want to, like nautilus, use the .thumbnails cache and when needed generate a thumbnail.

I cannot find much info on this, so any advice or links to examples would be much appreciated.

Cheers,
Matthew

---

### Post by Quikee on 2008-05-03
> **| MM | said:**
> In python am i able to utilise gnome's thumbnail factory?  

I want to, like nautilus, use the .thumbnails cache and when needed generate a thumbnail.

I cannot find much info on this, so any advice or links to examples would be much appreciated.

Cheers,
Matthew

Look at ThumbnailFactory documentation in gnome.ui. Or inspect gnome.ui in python/ipython ;)

Simple example:

[PHP]import gnome.ui
import gnomevfs

path = "somePicture.png"

uri = gnomevfs.get_uri_from_local_path(path)
mime = gnomevfs.get_mime_type(uri)

thumbFactory = gnome.ui.ThumbnailFactory(gnome.ui.THUMBNAIL_SIZE_LARGE)
if thumbFactory.can_thumbnail(uri ,mime, 0):
    thumbnail = thumbFactory.generate_thumbnail(uri, mime)
    if thumbnail != None:
        thumbFactory.save_thumbnail(thumbnail, uri, 0)[/PHP]

However this may change in the future because because of GVFS/GIO.

---

### Post by | MM | on 2008-05-03
Thanks mate.

---

