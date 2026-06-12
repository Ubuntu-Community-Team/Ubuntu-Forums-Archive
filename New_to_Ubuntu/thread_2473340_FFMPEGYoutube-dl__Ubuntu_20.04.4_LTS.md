---
title: "FFMPEG/Youtube-dl  Ubuntu 20.04.4 LTS"
date: 2022-04-01
forum: New to Ubuntu
---

### Post by todolinuxvidz1 on 2022-04-01
Hello and greetings all,
I have been using FFMPEG and Youtube-dl on Windows for a long time.
Recently I have migrated over to linux and I installed FFMPEG and Youtube-dl using the method., sudo apt install ffmpeg and sudo apt install youtube-dl

FFMPEG Appears to work fine with the exception that the grammar of the commands appears a bit more finicky.

However youtube-dl commands all seem to return the same sort of problem.
> youtube-dl -F [https://www.youtube.com/watch?v=FmZXCqqx6q0](https://www.youtube.com/watch?v=FmZXCqqx6q0)
[youtube] FmZXCqqx6q0: Downloading webpage
ERROR: FmZXCqqx6q0: YouTube said: Unable to extract video data


I will also approach this from a troubleshooting avenue via youtube-dl but was hoping something would jump out to people if I did something wrong in the installation, or that maybe I have to configure something in Ubuntu.

Id appreciate any help or being pointed in a new direction.
Thanks!

---

### Post by ActionParsnip on 2022-04-01
[https://manpages.ubuntu.com/manpages/xenial/en/man1/youtube-dl.1.html](https://manpages.ubuntu.com/manpages/xenial/en/man1/youtube-dl.1.html)

       -F, --list-formats
              List all available formats of requested videos

---

### Post by todolinuxvidz1 on 2022-04-01
Thank you!
Lot of good information there.  Definitely bookmarked for my next inevitable issue.


I seem to have found a work around that Im not too bothered with using.

instead of using this command
youtube-dl -F "https://www.youtube.com/watch?v=Uj6HcobebE8"

I use this command, and then it appears to work fine.
python3 $(which youtube-dl) -F "https://www.youtube.com/watch?v=Uj6HcobebE8"

---

### Post by slickymaster on 2022-04-01
Closed.

See [https://ubuntuforums.org/showthread.php?t=2439118](https://ubuntuforums.org/showthread.php?t=2439118)

---

