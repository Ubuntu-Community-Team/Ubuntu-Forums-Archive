---
title: "Ubuntu went crazy"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Dbugger on 2008-06-13
Help! My computer went crazy! HEre are the problems that happen now...

- My gnome bars disappear when i hit the shutdown button
- My network icon doesnt appear until 1 minute after the gnome desktop appears
- The bookmarks of firefox RC3 disappeared

Please help!!!!

---

### Post by pedro_orange on 2008-06-13
> My gnome bars disappear when i hit the shutdown button

Is this when u click the Shutdown button in the gnome-panel? Or when you hit shutdown on the big button on the pop up? Cause thats normal. 
Do they come back when you click Cancel?

> My network icon doesnt appear until 1 minute after the gnome desktop appears

Sounds like your computer is slow. If it's any consolation my network manager loads last as well.

> The bookmarks of firefox RC3 disappeared

Did this happen after an update by any chance?

---

### Post by wPwLUi3N on 2008-06-13
Did you do some tweaking?

Does this happen after installation of a particular package?

What was your last activity before this happen?

---

### Post by Dbugger on 2008-06-13
> **pedro_orange said:**
> Is this when u click the Shutdown button in the gnome-panel? Or when you hit shutdown on the big button on the pop up? Cause thats normal. 
Do they come back when you click Cancel?

Sounds like your computer is slow. If it's any consolation my network manager loads last as well.

Did this happen after an update by any chance?

When I hit the big red button, instead of the pop up, the bars disappear.

My computer was never SO slow.

I dont recall having done any recent update...

---

### Post by Dbugger on 2008-06-13
> **anuj.pathania said:**
> Did you do some tweaking?

Does this happen after installation of a particular package?

What was your last activity before this happen?

I wasnt doing any special activity that I recall...

---

### Post by Dbugger on 2008-06-13
I also get this message when i start firefox:

> [Exception... "Component returned failure code: 0x80520010 (NS_ERROR_FILE_NO_DEVICE_SPACE) [nsIFileOutputStream.write]"  nsresult: "0x80520010 (NS_ERROR_FILE_NO_DEVICE_SPACE)"  location: "JS frame :: file:///home/dbugger/.mozilla/firefox/rug0hbsm.default/extensions/%7B9AA46F4F-4DC7-4c06-97AF-5035170633FE%7D/components/4chanCom.js :: anonymous :: line 1094"  data: no]

and the history buttons in firefox are always disabled...

and when i start msn, I get this error:

> 
Fatal error
This is a bug. Please report it at: [http://www.emesene.org](http://www.emesene.org)

Traceback (most recent call last):

  File "/usr/share/emesene/emesenelib/SoapManager.py", line 92, in process
    return process()

  File "/usr/share/emesene/emesenelib/SoapManager.py", line 57, in process
    response.callback( response, *response.args )

  File "/usr/share/emesene/emesenelib/ProfileManager.py", line 112, in onGetMembershipList
    self.newCacheFile(self.user + '_ml.xml', response.body)

  File "/usr/share/emesene/emesenelib/core.py", line 905, in newCacheFile
    f.write(data)

IOError: [Errno 28] No space left on device

---

### Post by cariboo on 2008-06-13
Look at the last line in the msn error. It says no space left on device. You have to make some room on your hard drive. in a terminal run the following commands:

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

These are three seperate commands so hit enter after each one.

sudo apt-get clean will remove archived packages from /var/cache/apt/archives

sudo apt-get autoremove will remove any obsolete packages

df -h will show how much space is used on each mounted hard drive.

Jim

---

### Post by adamorjames on 2008-06-13
You most likely ran Firefox as root. To fix this do this.

```

 sudo chown -R user ~/.mozilla

```

Also Firefox 3 RC3 has nothing new in it for Linux.

---

### Post by Dbugger on 2008-06-14
it was the freespace issue. Thank you!

---

