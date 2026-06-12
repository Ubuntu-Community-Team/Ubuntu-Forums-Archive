---
title: "c++ and webcam"
date: 2007-11-21
forum: Programming Talk
---

### Post by patmalcolm91 on 2007-11-21
i was just searching around and i've seen a few videos on youtube of people who have taken a webcam (adjusted to capture infrared) or wiimote as an input device.
   basically, there is an IR source by the camera, and the camera tracks any ir reflected, say, from reflective tape on your fingers. The image is then parsed and used to do things like move the mouse, recognize gestures, rotate cube in CF, etc.

anyway, i want to try this as a project, but i don't know where to start, i've tried searching around, but nothing. I've been programming in C++ for a couple years now, but have never done anything quite to this scale (especially as far as hardware interaction).

Can anyone tell me where i can learn how to fetch an image from a webcam, give suggestions on how to parse the image, such as algorithms i should read up on, etc. Linux-specific information would be great. Or, if there is already a program that does this i could try, please let me know.

---

### Post by smartbei on 2007-11-22
Well, there is a somewhat-platform-independant library called openCV (available from the repos as libcv I believe) that I am using extensively on windows (so I don't know how easy it is to use on Linux) which offers ways to capture from cameras, etc. There are also many processing functions included - perhaps some might be able to do what you want.

---

### Post by loell on 2007-11-22
i think you can also use, pwlib (Portable Windows Library) **libpt-dev** 

wherein you can use two plugin libs to access webcam

**libpt-plugins-v4l **

**libpt-plugins-v42 **

---

### Post by patmalcolm91 on 2007-11-22
thanks for the tips guys, I'll look into these. anyone else with suggestions, keep them coming!

---

### Post by pall.e on 2008-06-19
bump partly, but thinking about this and how it should be possible but doesn't seem to have been done yet, I wanted to add these things: [http://linux.die.net/man/4/ur98](http://linux.die.net/man/4/ur98) a driver for the UR98 head tracker to be used as a pointing device, the UR98 was basically a pair of glasses with 2 led's on it and a camera so I assume it could maybe be altered to suit this purpose, [http://live.gnome.org/CamTrack#head-7549423c92cbd1ea2ced26b8904918a3510db457](http://live.gnome.org/CamTrack#head-7549423c92cbd1ea2ced26b8904918a3510db457) which is camtrack a headtracking open source program that is used as an input device and maybe could be altered to detect IR as opposed to Hue.  Sorry that I am not any help on this as I have no programming experience but thought I would try and add some input.

---

### Post by escapee on 2008-06-20
Check out touchlib.  It's pretty complete and comes with a configuration/calibration tools and testing apps.  I haven't tested it under Linux yet, but that's what I'm using for my research at school so I'm going to be moving the library there soon.  [http://nuigroup.com/touchlib](http://nuigroup.com/touchlib) has information on it in the wiki.  Really helpful tool - I've tested it with a quick prototype under windows with a crappy webcam and it worked really well as both a mouse cursor (with windows driver) and under the Smoke test app.  

Whoops, this is an old topic...
Still leaving this here incase anyone else stumbles upon it

---

### Post by pooper on 2008-11-19
Hi all, was searching google for information and stumbled across this forum.
For my uni project im researching gaming with body gestures. I'm aware its not breaking news but a pretty cool project. 

I'm thinking of using c++, opencv to gain input from a webcam and then using opengl to create the game which the input from the webcam interacts with. I'm not entirely sure how this will all work out so if any one knows any help or can suggest a better alternative (if exists?) I'd be very grateful. Also just to mention I run xubuntu and apple os x.

thanks

---

### Post by escapee on 2008-11-19
May as well drop in on this again.  

Check out [www.nuigroup.com](www.nuigroup.com).  The community over there specializes in multi-touch and other human interaction so you'll likely get a lot of help over there.

---

