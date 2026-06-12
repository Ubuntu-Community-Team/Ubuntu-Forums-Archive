---
title: "[SOLVED] Media Players and zooming"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by spidermagicat on 2008-10-03
I have had a niggling annoyance with linux which very occasionally reminds me of it's presence. 

The zooming in media players, (to avoid confusion this is when you can step change the size of the picture like in Media Player Classic, not just making things full screen)

I currently use mplayer without GUI and I like it very much but occasionally I get a movie with black bars across the top and bottom and it seems to be stumped, even if I start it with GUI there is no option. I also have totem installed so I can have thumbnails for videos but the feature is missing here too.

Ideally I would love to add this feature to MPlayer somehow although I haven't seen any easy way to add features to MPlayer. Adding it to Totem would also be ok. At the very least does anyone know of a separate player which has this feature.

Of course If I have been a total noob and missed this feature out please virtually slap me and then help.

Thankyou

---

### Post by jpkotta on 2008-10-03
> **spidermagicat said:**
> I have had a niggling annoyance with linux which very occasionally reminds me of it's presence. 

The zooming in media players, (to avoid confusion this is when you can step change the size of the picture like in Media Player Classic, not just making things full screen)

I currently use mplayer without GUI and I like it very much but occasionally I get a movie with black bars across the top and bottom and it seems to be stumped, even if I start it with GUI there is no option. I also have totem installed so I can have thumbnails for videos but the feature is missing here too.

Ideally I would love to add this feature to MPlayer somehow although I haven't seen any easy way to add features to MPlayer. Adding it to Totem would also be ok. At the very least does anyone know of a separate player which has this feature.

Of course If I have been a total noob and missed this feature out please virtually slap me and then help.

Thankyou

Try smplayer.  It uses mplayer as a backend, so can play anything that mplayer can, and has a zoom feature (called pan and scan).  The default keybindings are 'w' and 'e'.  Since smplayer is really just a frontend for mplayer, there must be a way to do this there too, but I see nothing in the man page.

---

### Post by spidermagicat on 2008-10-03
pan & scan is something I've found to zoom into wide screen movies (where there are gaps at the top and bottom) and the keys are still W & E in mplayer as well 

but...

 with 4:3 files with (black bars at the top and bottom and gaps at the side) and a wide screen picture there is no way to zoom in. The bar just goes from empty to full with no effect on the actual video

This is mainly a problem because I have a wide screen laptop and no way to view the files full screen when this is the case.

Thank you for the reply, and you are definitely correct. But the panscan feature is incomplete if your files have black bars.

---

### Post by lovinglinux on 2008-10-03
Open smplayer and hit CTRL+P to show the "Preferences" window. Then select "Advanced" in the preferences list, Look for "Monitor aspect" drop-down list and select 16:9 or whichever proper resolution for your monitor. Click OK.

Open the video which has 4:3 aspect ratio and try zooming in and out with "w" and "e" and see if works.

---

### Post by rvm4000 on 2008-10-03
> **spidermagicat said:**
> pan & scan is something I've found to zoom into wide screen movies (where there are gaps at the top and bottom) and the keys are still W & E in mplayer as well 

but...

 with 4:3 files with (black bars at the top and bottom and gaps at the side) and a wide screen picture there is no way to zoom in. The bar just goes from empty to full with no effect on the actual video

This is mainly a problem because I have a wide screen laptop and no way to view the files full screen when this is the case.

Thank you for the reply, and you are definitely correct. But the panscan feature is incomplete if your files have black bars.

SMPlayer uses its own routine for zooming. It should work even if the videos have black bars.

---

### Post by spidermagicat on 2008-10-03
Thankyou all. SMPlayer does indeed pan and scan or zoom how I'd expect a media player should.

Problem solved :-)

---

### Post by lovinglinux on 2008-10-03
> **spidermagicat said:**
> Thankyou all. SMPlayer does indeed pan and scan or zoom how I'd expect a media player should.

Problem solved :-)

Nice. Please don't forget to mark the thread as solved using the thread tools menu.

---

