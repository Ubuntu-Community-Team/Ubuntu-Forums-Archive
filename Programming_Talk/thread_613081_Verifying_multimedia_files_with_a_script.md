---
title: "Verifying multimedia files with a script?"
date: 2007-11-14
forum: Programming Talk
---

### Post by astrashe on 2007-11-14
I did something really stupid with a large (terabyte) reiser file system and now I have lots of files that I can't trust.  I know that some of them have been corrupted, and others haven't.

I'd like to write a script that would cycle through all of the files, and separate the well formed ones from the damaged ones.  But I don't know how to tell the good for the bad, or if it's even possible.

Can anyone suggest a strategy for checking multimedia files for corruption?

I was thinking that I'd try to use lame to decode an mp3 file, and to have the script mark the file as bad if lame exits with an error.  And to do something similar with ffmpeg.

Does this seem like a viable strategy?  Or is there some better way to do it?

---

### Post by smartbei on 2007-11-14
Perhaps only the files modified/created on a certain date/time are corrupted? (The date/time of your doing something stupid :p).

That is much easier/faster to check.

---

### Post by astrashe on 2007-11-14
I'm not really sure if that would work.  I've run across MP3s in the same directory, all ripped from CD at the same time (years ago), in which some were ok and others weren't.

I did this dumb thing where I corrupted the file system, then tried to use fsch to recover it.

There's a famous series of list posts about ReiserFS:
[INDENT]
"For a very good time, create a few dozen files containing images of ReiserFS filesystems on a ReiserFS (scratch) filesystem, and force an fsck.reiser. All of ReiserFS is a single B-tree, that can be anywhere on disk. So what fsck.reiser does is to search the entire disks for blocks that look vaguely like parts of the filesystem B-tree, and stitches them all together. Whee!!!!"[/INDENT]

[http://linuxmafia.com/faq/Filesystems/reiserfs.html](http://linuxmafia.com/faq/Filesystems/reiserfs.html)

I have to stress, for anyone reading this, that Ubuntu didn't create my ReiserFS -- it was my own idea.  Ubuntu uses ext3, which is much safer.  

I had to do about four really stupid things in sequence in order to create my problem, none of which are likely to be repeated by a casual Ubuntu user.

---

### Post by kefler on 2007-11-15
One way to check though not 100% is to check the id3 tag for the length of the media file, any media file that registers the media is less than x seconds long can be filtered out. Like I said this isn't 100% but it will at least narrow down your search afterwards.

If no id3 tag is returned... I'm pretty sure you can safely count that media file as being corrupt(if it's an mp3)

as for video files, sorry but I don't know of any way of doing this through script since the meta data is optionaly included in video files.

Edit: the id3 tags can be checked in almost all programming languages as far as I know, but I used php to do my stuff as I work with mostly web.

---

### Post by astrashe on 2007-11-15
> **kefler said:**
> One way to check though not 100% is to check the id3 tag for the length of the media file, any media file that registers the media is less than x seconds long can be filtered out. Like I said this isn't 100% but it will at least narrow down your search afterwards.

If no id3 tag is returned... I'm pretty sure you can safely count that media file as being corrupt(if it's an mp3)

as for video files, sorry but I don't know of any way of doing this through script since the meta data is optionaly included in video files.

Edit: the id3 tags can be checked in almost all programming languages as far as I know, but I used php to do my stuff as I work with mostly web.

Thanks very much for the reply.

The error condition from lame isn't absolutely reliable, unfortunately.    I think that what I need to do is create a series of "sanity check" tests, along the lines of what you've described here.

This is really depressing.  I should probably just wipe it off and take my lumps.

---

### Post by stylishpants on 2008-01-11
This week my hard drive died and I barely managed to copy most of my music collection off of it in time.  Some of the files are definitely corrupt, so I'm now in the same boat as you.

What did you end up doing?

---

