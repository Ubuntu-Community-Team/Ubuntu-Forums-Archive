---
title: "Script for .nautilus/python-extensions read ID3 OGG MP3"
date: 2008-12-19
forum: Programming Talk
---

### Post by podestafox on 2008-12-19
Hello, I have this script for the .nautilus / python-extensions

Also how to display information from id3 "ogg" too?

```

#!/usr/bin/python

# bsc.py

import os
import urllib
import nautilus
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
 def __init__(self):
  pass

 def get_columns(self):
  return (nautilus.Column("NautilusPython::title_column","title","Title","Song title"),
  nautilus.Column("NautilusPython::album_column",
    "album",
    "Album",
    "Album"),
  nautilus.Column("NautilusPython::artist_column",
    "artist",
    "Artist",
    "Artist"),
  nautilus.Column("NautilusPython::bitrate_column",
    "bitrate",
    "Bitrate",
    "Bitrate"),)

 def update_file_info(self, file):
  if file.get_uri_scheme() != 'file':
   return
  if file.is_mime_type('audio/mpeg'):
   filename = urllib.unquote(file.get_uri()[7:])
   audio = EasyID3(filename)

  if (os.path.isfile (filename) and (not os.path.isdir (filename))):
   mpfile = open (filename)
   mpinfo = MPEGInfo (mpfile)
   br = str(mpinfo.bitrate/1000) + " Kbps"
  else:
   br = ""

  file.add_string_attribute('title', audio["title"][0])
  file.add_string_attribute('album', audio["album"][0])
  file.add_string_attribute('artist', audio["artist"][0])
  file.add_string_attribute('bitrate', br)
  self.get_columns()


```

---

