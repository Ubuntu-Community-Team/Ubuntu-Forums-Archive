---
title: "GIMP gap avi encode plugin crashes while encoding."
date: 2013-10-20
forum: New to Ubuntu
---

### Post by lou1 on 2013-10-20
Hello folks, I am in the process of doing an encode with GIMP's GAP plugin and I am having a problem with the avi encoder crashing when the encode reaches a certain set of frames. It outputs 

```
EMERGENCY in gap_movtar: The jpeg memory compression
 is limited to 256 kb/frame !
Consult gz@lysator.liu.se to fix this problem !
Output file write error --- out of disk space?



```

when running GIMP in the terminal. I'm also presented with this error dialog box:

[IMG]http://i.imgur.com/9vdxqq9.png[/IMG]

A look into this issue when I Google the exact error reveals this source code script:

[HTML]http://www.sourcecodebrowser.com/gimp-gap/2.2.2/gap__gve__jpeg_8c_source.html[/HTML],

something about the jpeg buffer being too small or something like that. Perhaps one can increase the size of the buffer or something? If I had to edit any text files, which one and what changes?

I am using the native xcf format for the images at 1920x1080 resolution.

Has anyone else had this issue when using gap?

---

