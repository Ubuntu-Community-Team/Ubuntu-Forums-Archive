---
title: "feature request: ffmpeg mainline"
date: 2012-11-16
forum: Packaging and Compiling Programs
---

### Post by rogerdpack on 2012-11-16
I'm aware that ubuntu comes packaged with "libav" package providing ffmpeg (the executable).  Would it be possible to also add ffmpeg "mainline" as a package (also providing ffmpeg)? Pretty please?  Thanks :)
-r

---

### Post by evilsoup on 2012-11-16
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by FakeOutdoorsman on 2012-11-16
> **rogerdpack said:**
> I'm aware that ubuntu comes packaged with "libav" package providing ffmpeg (the executable).  Would it be possible to also add ffmpeg "mainline" as a package (also providing ffmpeg)? Pretty please?  Thanks :)
-r

I assume you mean as a package in an official Ubuntu repository. I would like to see this happen. However, I doubt the libav package maintainer in Ubuntu, as a member of libav, would allow this to happen. He was the one responsible for the switch from FFmpeg to libav in the first place.

Disregarding any libav bias by the Ubuntu overlords, for this to happen there would at least need to be a volunteer to maintain the package and a way for the package to work without conflict with libav.

---

### Post by andrew.46 on 2012-11-16
> **evilsoup said:**
> [https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

Or build your own:

Compile FFmpeg on Ubuntu 
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

But I agree, a repository version would be nice...

---

### Post by rogerdpack on 2012-11-21
Yeah something like how mplayer and mplayer 2 do it:

$ mplayer
The program 'mplayer' can be found in the following packages:
 * mplayer
 * mplayer2
Try: sudo apt-get install <selected package>


What does it mean for 2 packages to "not conflict" I assume you just mean file naming wise?

$ sudo apt-get install mplayer mplayer2 -y
The following packages have unmet dependencies:
 mplayer : Conflicts: mplayer2 but 2.0-426-gc32b3ed-2 is to be installed
 mplayer2 : Conflicts: mplayer

Maybe conflicts are alright then? Just wondering.
-roger-

---

### Post by FakeOutdoorsman on 2012-11-21
I implied two things:

[list]
[*]FFmpeg and libav share many of the same file names (assuming you want both installed at once)
[*]The issue of getting dependencies to work with both packages
[/list]

I don't think the first point would be much trouble, but I am not a maintainer. Perhaps the following *./configure* options:
```
--prefix=/usr \
--incdir=/usr/include/libav \
--libdir=/usr/lib/libav \
--shlibdir=/usr/lib/libav
```
This would put the libav's libavcodec files into "/usr/include/libav/libavcodec" while ffmpeg's, not having the additional configure options, would go to default "/usr/include/libavcodec/". I didn't look into how mplayer/mplayer2 was handled.

---

