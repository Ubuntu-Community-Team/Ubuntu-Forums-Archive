---
title: "Cairo, hoto display webcam images?"
date: 2006-11-10
forum: Programming Talk
---

### Post by mdurham on 2006-11-10
G'day
Can anyone please advise me on how to constantly display the output from a webcam using Ruby & Cairo?
I can operate the webcam, write images to disk etc and I can display a Gdk::Pixbuf  okay. It's just the updating of an image on the screen that I'm missing.

The data returned from V4l is a ruby 'string' but how do I display it? At first I thought to display a blank Gdk::Pixbuf of correct size (640x480) and constantly modify it's buffer but I think this might not be possible from within Ruby???

From the Ruby-Gnome2 site it says:
> Gdk::Pixbuf.new(colorspace, has_alpha, bits_per_sample, width, height)
    Creates a new Gdk::Pixbuf and allocates a buffer for it. The buffer has an optimal rowstride. Note that the buffer is not cleared; you will have to fill it completely yourself. Raises an...


note "you will have to fill it completely yourself" how is this achieved in Ruby?

Any help would be most welcome.

Cheers, Mike

--edit--
problem solved
Cheers

---

