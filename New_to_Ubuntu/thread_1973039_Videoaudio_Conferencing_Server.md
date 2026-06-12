---
title: "Video/audio Conferencing Server"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by ArslanW on 2012-05-04
I recently got my Ubuntu 12.04 and was wondering how can I turn my computer into a server which provides video/audio conferencing to people over a local network.... via Android phone or any computer

Friends suggested OpenIMSCore, some said Asterisk... I read about them a little and i think OpenIMSCore is my ticket but im still a little confused as to how I can achieve this goal....

Any suggestions? If so then can you provide a resource or something....

Thanks!

---

### Post by bhunji on 2012-05-16
Look into Big Blue Button and Open Meetings. Might be be more fully featured than you're looking for - they are designed for internet use, but both can be accessed by client machines using a web browser.

They are both under active development. BBB currently has some audio/video sync issues, and it's recommended to install the server on it's own machine. OM is now developed by the Apache Foundation and seems to be in Beta. The installation looks moderately hairy though!

When it's more complete, it should be fairly easy to install Ubuntu server, the OM packages and then install a desktop environment over that.

Long term I think OM will be the more popular, it's got all the features that will endear it to business and education users (scheduling, whiteboard, file transfers, encryption, unlimited sized rooms, screen sharing).

If you've never set up a server before (and don't want to now) there are plenty of web based, OS agnostic video-conf. services around (some are free for limited use).

---

