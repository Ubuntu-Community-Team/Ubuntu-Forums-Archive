---
title: "Media streaming + login http page"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by Gasric on 2014-03-18
Hi all,

Well I'm semi new to linux but I'm learning fast and love it, but i still consider myself a bit of a noob in the linux world!
So i'm at a loss really as i have researched what I'm looking for but I'm getting the "out of my depth" feeling and this is why I'm here looking for a little guidance;)

Project: Media streaming and login page via any media device that has access to a web browser. :popcorn:
Example: iPhone, Xbox, PS3 and web browser

What I'm needing is some advice and guidance on the following:
1. Media streaming software which is the best but free? (or very cheap!)
2. Noob guide to creating a login page and how to setup access using login details

Notes:
Web Sever: Apache2 installed and configured

---

### Post by TheFu on 2014-03-18
Use plex. Don't need to sign in or pay for anything.
Any DLNA client can access it - works from android, WDTV Live, XBMC, most "smart TVs" and blueray players. It is really bonehead simple.

I am NOT using the Plex client, just their server.

I use BubbleUPnP on Android as a controller.  Don't have a clue about apple or console support - I don't "do" proprietary stuff like those, sorry.  The server machine will need to fast enough to handle any transcoding on-the-fly, if necessary. That depends on the source audio and video involved and what each playback system can handled.  For all my systems, 1080p video works perfectly with near ZERO CPU (all done in the GPU hardware) if h.264 video and AAC audio are used.

Oh - and no need for apache at all.

---

### Post by Gasric on 2014-03-19
Hey TheFu,

Cheers for the info will take a look at it this evening and will give you a PM if thats okay with any questions i might have :)

---

### Post by TheFu on 2014-03-19
PM is NOT ok ... unless you will pay my rate and min engagement. ;)

---

