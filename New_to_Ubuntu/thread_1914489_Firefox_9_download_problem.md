---
title: "Firefox 9 download problem"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-01-24
I realize that there already is a thread about Firefox and I did read many of the posts but could not find anyone discussing my particular issue.

I am a total newb to Ubuntu and Linux and just installed Ubuntu two days ago.

I tried to download Firefox9. I got the Archive Manager window and I apparently downloaded incorrectly. 

After the download, I found Firefox9 in the archive manager and tried to extract the files. Nothing happened. Now I can't find that file so I can't try again. I thought I lost the file so I tried to download FF9 again, but my system won't let me. So I guess FF9 is somewhere on my computer but I can't find it.

How can I correct this? Thanks

---

### Post by FormatSeize on 2012-01-24
```
sudo apt-get uninstall --purge firefox
sudo apt-get install firefox
sudo apt-get update
```
 
The first command gets rid of any faulty versions of Firefox that you downloaded previously, while the second install Firefox from the repositories, which should work fine. Or, you can go to Mozilla.com and get Firefox from there. I generally prefer not to use the Software Center. There always seems to be a problem with that thing, in my experience.
 
 
Doesn't Ubuntu come with Firefox already installed?

---

### Post by Frogs Hair on 2012-01-24
Hello and Welcome 

Firefox should have updated to version 9 via the update manager if using 11.10 . For other versions of Ubuntu  the Firefox stable  PPA would be easiest to install  . If using 11.10 and you did not receive the update the method above should work .

---

### Post by Curtis6767 on 2012-01-24
Thanks, I now have FF9 up and running.
This one did not do anything. I typed it in and received an 'error' message.

"sudo apt-get uninstall --purge fireox"

This one downloaded and installed FF9 so I didn't have to go beyond.

"sudo apt-get install firefox"

And since I just installed Ubuntu I have 291 updates ready to be installed. FF9 might be one of them, but I can't find it in the list. I will install those updates later.

Thanks

---

