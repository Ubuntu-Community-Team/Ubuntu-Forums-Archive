---
title: "file types and mime types don't match for OpenOffice.org Drawings"
date: 2010-05-09
forum: Programming Talk
---

### Post by Flimm on 2010-05-09
This one has been puzzling me for an hour now, so I thought I'd pick your brains on this one.

```
david@david-laptop:~$ file *.odt
document1.odt: OpenDocument Text
document2.odt: OpenDocument Text
document3.odt: OpenDocument Text

david@david-laptop:~$ file *.odt -i
document1.odt: application/vnd.oasis.opendocument.text; charset=binary
document2.odt: application/vnd.oasis.opendocument.text; charset=binary
document3.odt: application/vnd.oasis.opendocument.text; charset=binary

david@david-laptop:~$ file *.odg
drawing1.odg: OpenDocument Drawing
drawing2.odg: OpenDocument Drawing
drawing3.odg: OpenDocument Drawing

david@david-laptop:~$ file *.odg -i
drawing1.odg: application/octet-stream; charset=binary
drawing2.odg: application/octet-stream; charset=binary
drawing3.odg: application/octet-stream; charset=binary

david@david-laptop:~$ 
```

Why is the mime-type for the OpenOffice.org documents _application/vnd.oasis.opendocument.text_, while for the drawings it's _application/octet-stream_?

Why does file recognise the file type but not the mime type?

Nautilus gives me "ODG drawing (application/vnd.oasis.opendocument.graphics)" in the properties dialog of one of the drawing files.

I've looked at the files in a hex editor and it does contain "application/vnd.oasis.opendocument.graphics" at offset 38.

First person to solve the problem gets my sincere admiration. (For what that's worth [img]http://ubuntuforums.org/images/icons/icon12.gif[/img])

---

### Post by Flimm on 2010-05-13
Bump. I'm getting the same results for PowerPoint files.

---

