---
title: "Totem error -"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-19
Thought I had the issue solved with K9Copy & K3b copy routines to backup a couple of movies... I'm not certain what I did, but now when I try to play the orginal or the copy I get an error in Totem:'Could not play DVD:///media/cdrom0' I tried going in add/remove & tried active variations of GStreamer, without any success. Does anyone have any ideas. Thanks, Cal

---

### Post by KenBW2 on 2008-05-19
It might be that you don't have DVD codecs installed. try this in Terminal:

> 
sudo apt-get install ubuntu-restricted-extras


and DVD codecs will be installed (along wih a load of others)

---

### Post by CoCoKnots on 2008-05-19
Thanks Ken,
I tried that & received the same error. When I try to play a movie, it states that 'Totem could not play 'dvd///media/cdromO' & 'there is no plugin to handle this movie. Do you think I need to start over & re-install Ubuntu ?

---

### Post by spiderbatdad on 2008-05-19
this may work:[http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback](http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback)
seems I have seen a lot of issue regarding dvd playback, as the digital rights are restricted. You may want to look into medibuntu also:[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by FuturePilot on 2008-05-19
You need to install libdvdcss2 from the Mediabuntu repositories. You can find out how to add the repos from the link in spiderbatdad's post.

---

### Post by CoCoKnots on 2008-05-19
We're on the right track... The links Spiderbatdad offered worked to get the movie up & running... However, it's in Black & white. Is there someway to toggle on the color or perhaps another terminal command ?

---

### Post by CoCoKnots on 2008-05-19
Hello Again,
Found the problem...
Somehow the color tabs defaulted to an off position.

While the movie was playing in B&W I had to go into EDIT then Preferences & reste the Encoding on the General tab. Then the Color Balance on the Display tab. Thanks for the help... I couldn't have figured that out without being in the Black & white mode first... The Forum is a great place to work this stuff out as a team. Thanks Again.

---

