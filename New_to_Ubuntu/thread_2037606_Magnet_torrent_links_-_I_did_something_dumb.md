---
title: "Magnet torrent links - I did something dumb"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by toomanymatts on 2012-08-05
ok I just did something stupid.

New install of Lubuntu on to a home theatre PC, went to a torrent site which uses magnet links, I clicked on the torrent I wanted to download, it gave me the big page of text that it always does on the first time you try to DL a magnet link, and I hit OK, and set it as default handler without looking.

I am dumb, I had never started Transmission on this machine, and now I have accidentally set Chromium browser as my default handler for magnet torrent links.  This is dumb.

How can I change this so that Transmission handles them?

---

### Post by Dylan1473 on 2012-08-05
I'm not 100% sure in the case of LXDE but I think you can probably right click a torrent icon, select Properties, and look for a drop down box or other menu of some kind that will probably be labelled "Open With" or something of the sort. You'll be able to select Transmission or any other torrent client of your choice from there. This is the case with most file managers.

EDIT: I just checked and it seems LXDE uses the pcmanfm file manager which - by a happy coincidence - is the one I have on my computer, so this method should definitely work. It'll be listed under your Internet applications from "Customize" if it's not one of the defaults, which it probably will be.

---

### Post by toomanymatts on 2012-08-05
> **Dylan1473 said:**
> I'm not 100% sure in the case of LXDE but I think you can probably right click a torrent icon, select Properties, and look for a drop down box or other menu of some kind that will probably be labelled "Open With" or something of the sort. You'll be able to select Transmission or any other torrent client of your choice from there. This is the case with most file managers.

EDIT: I just checked and it seems LXDE uses the pcmanfm file manager which - by a happy coincidence - is the one I have on my computer, so this method should definitely work. It'll be listed under your Internet applications from "Customize" if it's not one of the defaults, which it probably will be.
hi - thanks for this - and yes, it works with .torrent files, however magnet torrents (such as those on Pirate Bay) work differently - kinda sorta opening directly from the browser and without downloading the torrent file first, and these are the ones I am having the issue with.

---

### Post by mcduck on 2012-08-05
You should be able to change the default applications your browser uses to handle file types in the browser itself.

---

### Post by jtarin on 2012-08-05
With Transmission I normally just right-click the magnetic link then open Transmission and choose "File-Open URL". It will then  be automatically copied and started.

---

### Post by toomanymatts on 2012-08-05
> **mcduck said:**
> You should be able to change the default applications your browser uses to handle file types in the browser itself.
i totally agree with you there.  I really *should* be able to...but if it's a setting in Chromium, I really can't find it.

> **jtarin said:**
> With Transmission I normally just right-click the  magnetic link then open Transmission and choose "File-Open URL". It  will then  be automatically copied and started.

ya, that works as a workaround I guess, although I would prefer to just be able to click on it and have it jump-start like it does on my other machines.  

Any other ideas?  Ive been reading around with all the fighting people have done to try and change away from Transmission to another torrent client, and I suspect I need to do basically the same thing, but doesn't seem to be a definitive answer on the way to get that done.

---

### Post by toomanymatts on 2012-08-05
solved with a switch to Firefox (it's worth that much to me!) 

I'd prefer to be using Chromium though, so if anyone knows how I change the application handling there, I'd be very interested to hear it.

---

### Post by colin.p on 2012-08-05
Ha, I did the exact same thing as you. I have an old lucid athlon that I use specifically for downloading. I tried Chromium, instead of my usual FF, and now magnets won't open anything but Chromium and it doesn't do anything. I tried most of the usual hints but still nothing. I just said screw it and use the old "copy url".
It works for now until I truly get around to sorting it out, or until you find an answer, then I'll just copy you.:P

---

### Post by Paqman on 2012-08-05
> **toomanymatts said:**
> 
I'd prefer to be using Chromium though, so if anyone knows how I change the application handling there, I'd be very interested to hear it.

Wrench icon > Privacy > Content Settings > Handlers > Manage Handlers

---

### Post by jtarin on 2012-08-05
> **Paqman said:**
> Wrench icon > Privacy > Content Settings > Handlers > Manage Handlers
+1 for this

---

### Post by marinara on 2012-08-06
this is mis-info.  on ubuntu, (with unpatched xdg-open) chromium doesn't work with magnet links, you have to use firefox.

---

### Post by markbl on 2012-08-06
> **toomanymatts said:**
> and yes, it works with .torrent files, however magnet torrents (such as those on Pirate Bay) work differently - kinda sorta opening directly from the browser and without downloading the torrent file first, and these are the ones I am having the issue with.
I had the same problem with google chrome but when I reset my preferred app to transmission for torrent files via the file properties/open with dialog then I found that chrome then started transmission for magnet torrents as well. So clicking on the .torrent file changed my default for both types of torrents.

---

### Post by jtarin on 2012-08-06
> **marinara said:**
> this is mis-info.  on ubuntu, (with unpatched xdg-open) chromium doesn't work with magnet links, you have to use firefox.
If your on updates why would it be unpatched? For your info FF, Chrome and Chromium all open magnetic links on my system. 12.04

---

### Post by toomanymatts on 2012-08-08
> **Paqman said:**
> Wrench icon > Privacy > Content Settings  > Handlers > Manage Handlersthanks for this, but  everything in both fields there is blank (other than mailto links being  handled by Gmail).

> **marinara said:**
> this is mis-info.  on ubuntu, (with unpatched xdg-open) chromium doesn't work with magnet links, you have to use firefox.
I use Chromium on my other computer (running Ubuntu 12.04) and it handles magnets with no problem at all.

---

### Post by jtarin on 2012-08-08
Look in your home folder for a "hidden" file. /.config/chromium/Local State

If you find it make sure your browser is closed then open the file in a text editor and look for "protocols" and "magnet" and change "true" to "false" (this means ignore Magnet links = false) 

5. save file in same format it's already in (should not have file extension on end of filename)(not Local State.txt or anything else)........Relaunch browser. 
   

note:  if it still doesn't work, open this file again and simply delete the entire line with "magnet" (and nothing else)this will reset it.

---

### Post by toomanymatts on 2012-08-09
> **jtarin said:**
> Look in your home folder for a "hidden" file. /.config/chromium/Local State

If you find it make sure your browser is closed then open the file in a text editor and look for "protocols" and "magnet" and change "true" to "false" (this means ignore Magnet links = false) 

5. save file in same format it's already in (should not have file extension on end of filename)(not Local State.txt or anything else)........Relaunch browser. 
   

note:  if it still doesn't work, open this file again and simply delete the entire line with "magnet" (and nothing else)this will reset it.

thanks, it was already set to false, but just deleting the line half worked.

It worked insofar as it no longer automatically associates Chromium with the magnet links and killed the 'remember my choice' part of it.

So I went back in and again tried to open a magnet link, clicked on it, hit Launch Application (and this time wasn't dumb enough to put 'remember' and once again, it opened a Chromium blank window - just didn't make the association with Transmission at all.

This is interesting in that Firefox immediately opens them with Transmission, and I've done 'Open URL' from Transmission with no issues using a pasted magnet link, but Chromium just isn't making the association, and doesn't give me any options anywhere (that I can find) to do so.

For what it's worth, here is a screengrab of all it offers:

[IMG]http://s11.postimage.org/soe8eduoz/External_Protocol_Request_001.png[/IMG]

---

### Post by jtarin on 2012-08-09
Nevermind:P

---

### Post by dodo3773 on 2012-08-09
Does this work?:
```

xdg-mime default transmission-gtk.desktop application/x-bittorrent x-scheme-handler/magnet

```

Where "transmission-gtk.desktop" is the name of the .desktop file you want to open magnet links. Usually .desktop files are located in "/usr/share/applications" or similar. May just be called "transmission.desktop". After that you can look at this file to verify:
```

~/.local/share/applications/mimeapps.list

```

or just run this:
```

xdg-mime query default "x-scheme-handler/magnet"

```

If that still doesn't work you may need to edit xdg-open directly.

---

### Post by BerryPezenar on 2013-01-22
I did the exact same thing. Also, I find it very annoying having to manually paste the url's into Transmission.

---

