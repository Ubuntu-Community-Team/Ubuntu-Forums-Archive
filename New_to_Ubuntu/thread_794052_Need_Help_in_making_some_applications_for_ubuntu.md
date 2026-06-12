---
title: "Need Help in making some applications for ubuntu"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by vginov on 2008-05-14
Dear All
I have been using Red Hat for all the most 3 years.. Now I am changing to Ubuntu.

I would like to mention some need of the end user we should focus on if we want the world to go with free source.

1. Mac's Interface
2. Windows's Accessibility
3. Linux's Administration 

1. Mac4Lin project is doing the first one.

2 & 3 are being focused by ubuntu. 

Now ubuntu is giving good interface with some accessibility and some Administration.

I would like to also contribute to the Linux community as i can..

If we make all the shell commands as an executable applications (deb files)then it would be easy for people to get what they need.

For example we now have the extractor as they see in windows (Right Click > Extract Here). Like this all the commands can be made as an .deb file and allowed users to use..

Mostly i forces on  

1. Internet Connection Sharing (Firestarter is not yet good enough)
2. Right click on a .tar.gz file and make it as an .deb file (All the make commands can be put together)
3. Right Click on the .rpm file and make it as a .deb file (alien commands can be used)
and so on...

what i find being as an administrator is that people want it as easy as it can be because they are already spoon fed so there is no way for us to change them so let us change for them...

So if any of you can help me with how to make a shell script as .deb file that would help me to help the open source world 

Thanks a lot to all

---

### Post by Xiong Chiamiov on 2008-05-15
I'm not sure how to go about putting something into a right-click menu, but the shell script is rather simple.
```

#!/bin/bash
./configure
sudo make
sudo checkinstall

exit 0

```
or some such, I'm not too familiar with checkinstall, having only discovered it recently and not needing to compile very often.

---

