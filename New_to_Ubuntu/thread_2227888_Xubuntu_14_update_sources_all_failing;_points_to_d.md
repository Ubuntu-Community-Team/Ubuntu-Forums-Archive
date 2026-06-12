---
title: "Xubuntu 14 update sources all failing; points to dead URL?"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by cole4 on 2014-06-04
Fresh install of Xubuntu 14. Allowed updates during install.

sudo apt-get update results in a long list of 404 errors.

For some reason all the sources are pointing to us.archive.ubuntu.com and then looking for the Trusty sources. There aren't any Trusty sources anywhere on that server, or the Main server. I can access the servers, pull them up and navigate their filetrees in my browser, I just can't find any Trusty sources.

Any suggestions? Extensive Googling hasn't yielded any results.

---

### Post by LastDino on 2014-06-04
You can change servers from ''software & update'' manager in settings. Just open it and click on the downward arrow next to server link provided in the box saying ''download from''. Then select ''other'', then click on ''select best server'' and let it run its course and when its done, click on ''choose server''. That will close that sub-window, then you will be asked to ''update cach/resources'' when you click on close, proceed with positive reply to that and again, let it run its course.

Then you can try running update to see if its working or not. If there are any errors, click on details and post it back here.

---

### Post by cole4 on 2014-06-04
Ah, I wasn't aware the GUI had that functionality. I'm used to working on command lines with server installs.

It looks like it's behaving properly. I'd consider this solved.

---

### Post by cole4 on 2014-06-04
Just curious, do you know the equivalent for that functionality via terminal command?

---

### Post by LastDino on 2014-06-04
Well, there are options like netselect and apt-gets mirror method, but I've never actually used them but since you've command line experience, maybe you can work on it. 

Mirror lists.
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
[http://mirrors.ubuntu.com/](http://mirrors.ubuntu.com/)
[http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror/125252#125252](http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror/125252#125252)

Methods. These are old descriptions so you might need to change wherever applicable.
[http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line)

OR
Wait for someone better to guide by posting new thread about that, lets say, in chat section?

---

