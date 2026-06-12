---
title: "Detecting Advertisements in Flash Videos?"
date: 2010-01-14
forum: Programming Talk
---

### Post by beagler on 2010-01-14
Hey everyone.

I was just wondering about the feasibility of a program that detects when a flash video is playing an advertisement and then mutes the computer until the end of the advertisement. Ideally it would play some music and darken the screen too.

Is this possible? It seems that if its possible to do the detection, the other stuff would be possible.

Does anyone know what language would be best to do such a thing in? I mostly program in php but can do some java too. Is java capable of it? I'm assuming so, but I dont know how.

Thoughts?

---

### Post by ronniestamps on 2010-01-14
Flash is embedded media. There is nothing that determines whether it is an advertisement or actual content. You either block Flash, or you allow it. Not selectively filter what lies on the time line of the swf file.

But then again, I am not the Flash authority. That's just how I see it with my web development experience.

---

### Post by beagler on 2010-01-14
Yea. So basically what I was thinking is that if it were possible to analyze the audio stream before it was sent to the soundcard, maybe certain websites would have trends that could be recognized.

For instance, I've noticed that advertisements sometime seem louder than streaming video. Maybe if we determined that the overall volume was increasing during ads, or if we could find any other pattern that recognizes trends in ads that dont occur in other video (im not sure if there are any) then we could use that as a flag and adjust system volume down until real video resumed.

I guess im wondering if theres any way to get a computers audio output as a stream and then analyze it? I know audacity used to let me record whatever the output of my speakers was.

---

### Post by ssam on 2010-01-14
maybe you could add this into one of the open source flash players, gnash or swfdec. they could make decisions based on the source of the stream.

---

### Post by J V on 2010-01-14
If you find an ad server, you can block it with a hosts file, I did this and now I only see ads on the newest ad systems, and it will block the ones inside too ;P

Also, if you rig an apache server at localhost to find out weather you are on a normal page or a video page (regex ftw!) it can automatically darken the contents of the webpage too...

Win lose situation, the way its supposed to be :)

---

### Post by beagler on 2010-01-14
Thanks for the info. I used to block ads by configuring the hosts file when i used windows, and I found that it only blocked about half of the ads on hulu, assumedly because i needed to update it, but i never came across a simple way to keep it updated. It also blocked some of the content I wanted, like from CBS when I wanted to watch a show on there.

Do you know of a good way to keep the file updated without manually finding out the address of the ad server and then entering it into the hosts file? Perhaps a web browser extension? It could work like: You see an ad. You click a button to list the last 5 or 10 requests. You find the ad server from the list and click it. It would then update your hosts file and optionally re-load the page. 

I wonder if a similar thing exists or if a browser extension has access to the hosts file?

Originally I thought the hosts file wasnt a good solution, but on second thought i was probably just doing a bad job at it. It seems far easier and more reliable than the crazy method i originally thought of.

Anyways, thanks for helping me entertain this little idea.

---

### Post by lavinog on 2010-01-14
Many ad videos get stored in /tmp as Flashblahblah
you could do a check for an existing video file (use file to verify it is a flash video)
determine the length of the file, and do your thing for that length.

---

