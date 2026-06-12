---
title: "Minimize-on-click stopped working"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by peterson43 on 2012-08-21
A few months ago I added the minimize-to-click patch to my Ubuntu 12.04 following the instructions at [http://www.omgubuntu.co.uk/2012/03/how-to-minimize-apps-to-the-unity-launcher-in-ubuntu-12-04]("http://www.omgubuntu.co.uk/2012/03/how-to-minimize-apps-to-the-unity-launcher-in-ubuntu-12-04"). 

It worked great and I loved this feature, but a few weeks ago it just stopped working. Does anyone know why or how to get it working again?

---

### Post by Bashing-om on 2012-08-21
Hi ! peterson43....

 If I might suggest; uninstall the click-on package in accordance with the uninstall directive at the bottom of the source link. Here is addition help in this how-to:[ http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html ]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")
 Then: reinstall once more.
 It might be possible to reconfigure the package, but as it is not supported, I have my doubts about a fix ..you may however research the re-configure option and see what you think.
 Please advise of your solution.
 As you find this successful, please mark this thread as solved.
[]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

---

### Post by newb85 on 2012-08-21
Peterson43,
  I also use the same patched version of Unity.  It is still working fine for me.  I second Bashing-om's advice.

---

### Post by newb85 on 2012-08-21
Oh, I just checked, and I'm actually using a different patched version of Unity from a different ppa, with installation instructions at [http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html](http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html).  You might try using that one instead.

The one I'm using can also bring back the dodge windows behavior the launcher had in previous releases, but only if the setting is changed in compiz.

---

### Post by peterson43 on 2012-08-23
Okay, I seem to have really screwed something up. I decided to use ppa-purge to remove the minimize-on-click patch per the instructions at [http://www.webupd8.org/2012/03/unity-with-minimize-on-click-patch.html](http://www.webupd8.org/2012/03/unity-with-minimize-on-click-patch.html)
(I don't remember if I got error messages at this point or not). 

Then, I followed the instructions on that same page on installing the patch. However, I could not run the command
```
sudo apt-get update
```
Something seems screwed up with the software sources and I cannot run Update Manager, Ubuntu Software Sources, or Synaptic Package Manager. They all give an error message or immediately shut down when I try to open them. 

I was able to get into the GUI software sources list and uncheck the minimize-on-click ppa from the list, but that didn't seem to help either. I've restarted the computer a couple of times, but that doesn't seem to do anything. 

I've attached a screenshot of the error message that I get when trying to start Update Manager. It seems to say there is something wrong with the file /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list

I checked the contents of this file, and they are the following
```

# deb http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu precise main
# deb-src http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu precise main
ain

```

Anyone have ideas as to what I should do?

---

### Post by peterson43 on 2012-08-23
I might have solved my own problem (though I still don't have the minimize-on-click working). 

I commented out the third line in the file that had the error in it so it now reads
```

# deb http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu precise main
# deb-src http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu precise main
# ain
```

I'm guessing that the "ain" was somehow the remenant of "main" that somehow got left behind. 

I noticed that there is a similar file called /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list.save that had a similar line. That file reads
```

# deb http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu precise main
deb-src http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu precise main
ain

```

I haven't changed this file since it apparently isn't causing problems. I'm guessing from the name of it that it's just a backup for the other file I modified in case the other file got changed/corrupted. If that's the case then it doesn't matter if I fix this one or not. 

At this point I'm a little nervous about trying to add the minimize-on-click patch again. Any suggestions on how I could do this properly? Could I just delete these files from the sources.list.d folder, then restart the computer and add the ppa again according to the original instructions? Is there a better way?

---

