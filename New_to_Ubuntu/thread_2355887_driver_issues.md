---
title: "driver issues"
date: 2017-03-17
forum: New to Ubuntu
---

### Post by levsau on 2017-03-17
[FONT=verdana]So I've just installed Ubuntu 16.04 LTS, and I decided to have it use the binary drivers for my 980 ti which were included as an option in the driver menu. And so I let it do its thing and then restarted it when it was finished, now it refuses to boot into ubuntu. Any ideas?

 Edit: wait a second, while I was sitting here writing this. I heard the little bingo sound that it makes when I boots up. Although it's not putting out a signal to the screen.
[/FONT]

---

### Post by Autodave on 2017-03-17
Where did you get the driver from? You should use the ones in the repositories. You may have to remove the one you just installed and then pull it from the repositories. The newest one is 378.?? I believe.

---

### Post by levsau on 2017-03-17
I got the driver from the drivers menu in the settings. If I were to uninstall it, how would I go about doing so? Whenever I select Ubuntu, It gives me a purple screen for about 10 seconds, and then it just stops putting out a signal. I've tried ctrl+alt+f1/f2 to get to the login screen and it hasn't worked

---

### Post by Perfect Storm on 2017-03-18
Try when before it boots up hit  <shift> and then <e>
Then find the line that says linux and add the following **nomodeset** (right after quiet splash).

Then <F10> to boot.

---

