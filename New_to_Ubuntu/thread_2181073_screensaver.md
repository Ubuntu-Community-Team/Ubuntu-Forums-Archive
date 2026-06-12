---
title: "screensaver"
date: 2013-10-16
forum: New to Ubuntu
---

### Post by frog3764 on 2013-10-16
Greetings to the Group

This NEWBIE / DUMMY is looking for a screensave that lets me use my own photo folder.  My os is 12.04 LTS.  I've only had this os for a week now, so please don't get technical on me as I don't know my way around yet.  All input is appreciated.

Thanks,
Jim

---

### Post by MrMichaelHill on 2013-10-16
I can't be of much help yet as I am typing this off a phone but there is a way, called XScreensaver I believe, in 90% sure it has a photo one it, have a read of this

[http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/)

Hope this might be a little help. =)

---

### Post by slickymaster on 2013-10-16
> **frog3764 said:**
> Greetings to the Group

This NEWBIE / DUMMY is looking for a screensave that lets me use my own photo folder.  My os is 12.04 LTS.  I've only had this os for a week now, so please don't get technical on me as I don't know my way around yet.  All input is appreciated.

Thanks,
Jim

_You can do it with XScreensaver:_
[LIST=1]
[*]open XScreensaver,
[*]click the Advanced tab,
[*]under the "Image Manipulation" section check the "Choose Random Image" to enable the 'Browser' button,
[*]press it and it will open the 'Select the image directory' dialog,
[*]navigate to your photo folder location and click the 'OK' button.
[/LIST]

---

### Post by frog3764 on 2013-10-17
Hey Mike and Slicky - thanks for your input.  I think you've  solved my problem.  I already downloaded Xscreensaver so now I need to figure out how to install it.   I saw a video on
Youtube on how to do this, so I'll study that.

Jim

---

### Post by slickymaster on 2013-10-17
You must be aware that in order to install Xscreensaver it is recommended to uninstall the gnome-screensaver first. All you have to do is:```
sudo apt-get remove gnome-screensaver
```After that install XScreensaver:```
sudo apt-get install xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
```And you're done.

---

### Post by newb85 on 2013-10-17
> **frog3764 said:**
>  I already downloaded Xscreensaver so now I need to figure out how to install it.   I saw a video on
Youtube on how to do this, so I'll study that.

Don't know what video you're watching, but you should be aware that downloading packages with your browser and then installing them (the Windows way) is in most cases not the best way in Ubuntu.  Installing them from the repositories using Ubuntu's package management system usually is.  Slicky has given one way to do that.  Another way is using Software Center.

---

### Post by frog3764 on 2013-10-17
Hey Newb85 - I did download the xscreensaver from the package installer here in Ubuntu.  I did install it ??? in the terminal, but the video I saw said I need to add a text file for this to work, and I'm afraid to continue with that.  Here is the video I saw -   [http://www.youtube.com/watch?v=CRwAJoxWOKE](http://www.youtube.com/watch?v=CRwAJoxWOKE)  Anyway, I thought I better hold off for now till I figure this out better.  I did uninstall the Gnome Screensaver first per this video.

Jim

---

### Post by slickymaster on 2013-10-17
See my previous post, [post #5]("http://ubuntuforums.org/showthread.php?t=2181073&p=12818508&viewfull=1#post12818508").

Or if you don't feel comfortable using a terminal, follow newb85's advise and install it through the Software Center.

---

### Post by frog3764 on 2013-10-17
I've already added it in the terminal, so is that OK?  Should I also use the software Center now?  What about the "text" file that should be added, or is that right, and from the video, it looks like a pretty complicated procedure to do that.

---

### Post by slickymaster on 2013-10-17
> **frog3764 said:**
> I've already added it in the terminal, so is that OK?  Should I also use the software Center now?
No. If you have done it via terminal, it's already installed.
> **frog3764 said:**
> What about the "text" file that should be added, or is that right, and from the video, it looks like a pretty complicated procedure to do that.
I don't have the slightest idea of what this text file is as I have not seen that video. But, AFAIK, there's no text files involved with the Xscreensaver installation.

Once you have installed it, all you have to do now is to perform a search in the Dash for Screensaver. Launch the Screensaver utility and use it to configure XScreenSaver and select your screensaver settings. The Screensaver utility will prompt you to stop the gnome-screensaver process and launch the xscreensaver background process when you start it.

---

### Post by frog3764 on 2013-10-17
I found the xscreensaver and set it up with my photo folder and it works fine, so thanks to all of you for your help.  Problem solved!

Jim

---

