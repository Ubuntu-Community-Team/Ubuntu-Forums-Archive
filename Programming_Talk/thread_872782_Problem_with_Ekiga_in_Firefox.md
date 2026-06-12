---
title: "Problem with Ekiga in Firefox"
date: 2008-07-28
forum: Programming Talk
---

### Post by ankushjain79 on 2008-07-28
Hi,

I am trying to develop a plugin for the video to be displayed in Firefox window. When I try to set the input device there I receive NULL. I am modifying ekiga code. The code which fails is:
grabber = PVideoInputDevice::CreateOpenedDevice (video_manager,
					       video_recorder,
					       FALSE); 
This piece of code works when I build a standalone application. 
Is there anything specific like loading the library for Video Plugin(V4L) has to be done or something else in the firefox plugin. For the firefox plugin I am building a shared object library.

Thanks in advance.

Ankush

---

