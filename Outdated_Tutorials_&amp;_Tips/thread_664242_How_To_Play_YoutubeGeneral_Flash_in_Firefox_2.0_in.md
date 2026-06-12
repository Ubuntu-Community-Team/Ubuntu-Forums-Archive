---
title: "How To: Play Youtube/General Flash in Firefox 2.0 in Ubuntu 7.10"
date: 2008-01-10
forum: Outdated Tutorials &amp; Tips
---

### Post by papuccino1 on 2008-01-10
Hello, this is my first guide and everything works 100% guaranteed!
Do you want to watch videos on YouTube, Dailymotion, Metacafe or just play some flash games, this is the guide for you.

**************************************************************
Note: If you've installed Gnash or any other flash add on through synaptic or through the Add/Remove appliance, uninstall them now.

Note 2: You must have Firefox and any other internet explorer closed for this to work and install correctly. I HIGHLY suggest you copy this guide in a simple text editor and read the steps from there. 

IF YOU LEAVE FIREFOX OPEN WHILE DOING THIS, IT WON'T WORK.
**************************************************************


1. Visit: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")



2. Click on "Option 1"; find the download link just beside the red flash icon.
[IMG]http://i1.tinypic.com/8eigd1d.png[/IMG]




3. Choose save to disk, and if your Firefox is set to default settings it will save the tar file on your desktop.



4. After it's done downloading right click on the tar file and select extract here. You'll create a folder on you desktop like this.
[IMG]http://i16.tinypic.com/8aap46e.png[/IMG]



5. Double click on the file selected by the red arrow in step Nº4.

6. Select "Run In Terminal".



7. Follow the dead easy instructions in the terminal that should pop up like this:
[IMG]http://i17.tinypic.com/7ynvgy1.png[/IMG]


That's it, now open Firefox and visit YouTube. Everything should be working 100%.

---

### Post by Redrazor39 on 2008-01-18
When I go to that site the link to download the tar.gz file is broken; it won't do anything when I click on it, no matter what I do. Can you post instructions to do this with Options 2 or 3?

---

### Post by gorilly on 2008-01-24
i searched for ages to get youtube working

that worked perfectly,

thanks man

---

### Post by TwiceOver on 2008-01-25
Never mind... Did something dumb.

---

### Post by POV_Dave on 2008-01-27
Thanks, that worked like a charm!

---

### Post by cdcweb on 2008-02-07
I simply can't download the flash plugin. It's been the same way for the last 3 days.

I don't dare use the *.deb package recommended on other sites/topics, because all it does is open a download window to the Adobe with the same slow/hanging results.

Until I can get this plug-in to the desktop, installing it is moot.

Does anyone know why the download site is so slow?

---

### Post by jwalling on 2008-02-14
I tried all the other ways to update Flash. No luck.
This method worked like a charm!  Thanks.:KS

---

### Post by nitricacid on 2008-02-14
I didn't have a problem with flash/ watching youtube when I installed 7.10.
It wasn't installed when the OS was installed but rather after I visited a site that required flash plug-in. I clicked the 'Install Program' button that appeared at the top of the page (on firefox) and everything manually installed, then once I rebooted the computer it ran all the flash sites (including youtube) great.

Kind of weird why I didn't have to download a package from adobe to install it, let alone go through the hassle of making symbolic links to get it to run in firefox...
I'm not complaining though... It worked on it's own and that is even better.

---

### Post by PiggiePaul on 2008-02-14
Going to try this tomorrow night.

Now I don't wish to appear thick, but rather than cock something up, I just have 1 query.

Could you/someone tell me exactly where to go and what to look for to make sure I've not got installed (or where to look to uninstall) anything I already may have in Firefox as you say at the start of your posting.

Thanks :)

===== EDIT =======

Just wanted to say, followed you excellent simple instructions and worked perfect.
Thanks.

---

### Post by Quotidian Minutia on 2008-02-17
I can't seem to get this working.  I've downloaded the file without any problems, and extracted it to the desktop.  But when I double click on the flashplayer-installer file, then choose "run in terminal", nothing happens.  I've tried several times, and have even tried restarting the computer, just in case, but still no luck.  Is there some way I can get around this?

---

### Post by teslarage on 2008-02-17
Hey there,

I am assuming you are running 32-bit Ubuntu.

Open up a terminal, browse to where you extracted the files, and try this (this is what I did when I installed mine):

```
sudo ./flashplayer-installer
```

---

### Post by dj_killer_lamb on 2008-02-18
Thank you thank you thank you!!! Have been trying to get flash working and haven't succeeded. Funny how the simple away of approaching something is usually the most effective!

---

