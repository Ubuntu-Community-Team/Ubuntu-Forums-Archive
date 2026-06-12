---
title: "Firefox Download Error"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by elysianfields44 on 2011-09-23
When I try to "open with ubuntu software centre (default)" a .deb file from firefox 3.6 (instead of saving the file, and then opening it), I get the following error message:

```

**Download Error**

/tmp/myfile.deb could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.
```

I checked the /tmp folder, and it has 777 permissions, and is owned by root. Moreover, the file, myfile.deb, is actually downloaded successfully in /tmp even though I get the download error. So I'm guessing it failed at the opening part.

Any ideas as to what's going wrong? Thanks.

---

### Post by elysianfields44 on 2011-09-25
Anyone?

---

### Post by LinuxFan999 on 2011-09-25
What is the name of the file you are trying to open?

---

### Post by elysianfields44 on 2011-09-25
[http://desktop.google.com/en/linux/download.html](http://desktop.google.com/en/linux/download.html)

The .deb for Debian/Ubuntu x86

Thanks.

---

### Post by elysianfields44 on 2011-09-25
But, the error is not limited to the .deb file above. I get the same error every time I click on a .deb file download in firefox and select "Open with Ubuntu Software Centre". 

For example, if I try to download Chrome from here: [http://www.google.com/chrome/index.html?platform=linux&hl=en](http://www.google.com/chrome/index.html?platform=linux&hl=en), I get the same error if I select "Open with Ubuntu Software Centre" instead of saving the .deb file and then opening it.

---

### Post by elysianfields44 on 2011-09-25
Furthermore, I noticed the following:

1) I click the "Open with Ubuntu Software Centre" option for a .deb file within Firefox
2) The file gets downloaded successfully in /tmp
3) When I view /tmp, the permissions on the newly downloaded file are 400, and it's owned by me.

I have a feeling the read-only permissions on the file may be causing the error - why does firefox save the file with 400 permissions? The permissions on the directory /tmp are 777.

---

### Post by Captain Smiley Pants on 2011-09-25
You are using gnome, right? Try going to your file manager (just open up Places -> Downloads, navigate if you need to, etc) and right clicking the file and selecting Properties, then the Open With tab, then make sure it's on GDebi Package Installer.

If that's not working for you, open up a terminal and navigate to the folder and pull a *sudo dpkg -i package.deb* (package.deb being your file) and see if that displays any error messages. Post them messages if you find one :)

EDIT: Oh I just noticed you are trying to install Chrome, if you don't want to deal with that specific package then check the Ubuntu Software Center or Synaptic Package Manager for the chrome package in there. But you probably want the *latest* which is cool too, whatever floats your boat just wanted to point that out :)

---

### Post by flanagan on 2011-09-25
I think what your seeing is a result of this bug, which claims to have been fixed in Firefox 4.0 and better:

see [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/254169]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/254169")

Have you tried upgrading your version of Firefox. 3.6 seems kind of old.

---

### Post by elysianfields44 on 2011-09-26
> **flanagan said:**
> I think what your seeing is a result of this bug, which claims to have been fixed in Firefox 4.0 and better:

see [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/254169]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/254169")

Have you tried upgrading your version of Firefox. 3.6 seems kind of old.

Thanks for the link, I found that through my own googling as well - I'll try upgrading firefox and will post here if it solves the problem.

Also, Firefox 3.6 is the default version shipped with maverick 10.10 which is what I'm running. (See sticky: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247))

---

### Post by jtarin on 2011-09-26
You might also try changing the default download location for Firefox derived downloads. I have a folder in my home folder I download to. This way there is no problem with permissions. Then you will be able to install using right-click Debi-installer.

---

