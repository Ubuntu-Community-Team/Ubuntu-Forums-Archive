---
title: "dash preview for music lens not working properly"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by krishnan t s k on 2012-10-26
i installed quantal quetzal a few days back n now I’ve run into a small problem
when i right click any music file in my hard disk(i.e. locally) in the dash, the preview feature does not work correctly.. I’m not getting the option to open the file or the containing folder also
the file i attach should give a clearer picture
i feel this has something to do with me changing the default music player from rhythmbox to banshee but i may be wrong
is there any solution for this problem? oh and btw, the online music plays perfectly from the dash preview... its only the local music that is behaving weirdly 
thanks in advance for your comments and help :)

---

### Post by mc4man on 2012-10-26
I believe the Dash music preview only works thru RB, did you remove RB or are you filtering to only show banshee in the music lens itself?

---

### Post by krishnan t s k on 2012-10-26
no i've not removed RB... only changed the default from banshee to rhythmbox... does that mean i wont be able to preview any music files from the dash?

---

### Post by mc4man on 2012-10-26
No, at least here I can preview with both banshee & RB installed & banshee set as default but only the local files that are 'sourced' by RB (imported in to

So try this - 
Open music lens, click on the filter > Sources & set to Rhythmbox only
Then see if you can preview any of the files shown. 

So here when the music lens is set to 'Sources' > All it will often show the same track twice, once sourced by banshee (no preview), once by RB (can be previewed

---

### Post by krishnan t s k on 2012-10-26
yes that works.. now i'm able to preview it
but my question is will there be no preview at all if the file is sourced only by banshee? because i prefer and use banshee as it gives me an equaliser support which is lacking in rhythmbox... suppose i hit the music lens once in a while and i want to preview a file, i cannot do it if its sourced from banshee?
i'll mark this thread as solved for now... but please do let me know
thanks again for the help... good day :)

---

### Post by mc4man on 2012-10-26
> **krishnan t s k said:**
>  suppose i hit the music lens once in a while and i want to preview a file, i cannot do it if its sourced from banshee?
)
Correct - the music lens itself works with both, but the preview is RB only. So when using both it can become a bit of an hassle with the preview feature, if you try to preview an 'icon' produced by banshee - nothing happens.

---

