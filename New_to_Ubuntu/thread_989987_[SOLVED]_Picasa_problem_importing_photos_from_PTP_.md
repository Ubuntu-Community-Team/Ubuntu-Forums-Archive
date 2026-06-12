---
title: "[SOLVED] Picasa problem importing photos from PTP camera"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by bigspottycat on 2008-11-22
I had a recent problem importing photos into Picasa on Ubuntu 8.10 Intrepid Ibex (clean install). I have now found a workaround which I am posting here for anyone else who is having the same problem.

When I attach either of my cameras (Canon IXUS 500 and Kodak Easyshare M853, both PTP) a dialog box pops up asking to say that a camera has been detected, and asks what do I want to do. Importing via F-spot was flawless but I really wanted to use Picasa so I could sync my photo albums with PicasaWeb. Picasa could recognise that I had attached a PTP camera but didn't find any photos to transfer.

Then I noticed that if I choose to unmount the camera when the dialog box pops up, suddenly Picasa will recognise the photos and is able to transfer/import them!

From googling around I think the problem lies with the way PTP cameras are mounted in 8.10 (gnome now uses gvfs to mount PTP cameras as a filesystem which nautilus can browse). This is generally a good thing but seemed to stop Picasa from importing properly. 

Stopping ubuntu from mounting the camera when I attached it via USB was more difficult than I thought. The old 'removable drives and media' menu seems to have disappeared in Ubuntu 8.10 to be replaced by preferred applications (under System-Preferences), which doesn't include how cameras are handled. I assume this is because Nautilus now handles this under Edit-Preferences-Media. However, there is no option to tell nautilus to stop mounting usb attached cameras (even the 'do nothing' option didn't stop the cameras being mounted).

In the end I wrote a small bash script which tells gvfs to unmount the camera as soon as it is attached then load picasa. Now when I attach my camera via usb, it automatically unmounts the camera and loads Picasa, which is then able to import the photos. Phew!

I have attached the bash script if anyone else wants to use it. It is a quick and dirty workaround. I can't see how it would cause any damage but I'm new to bash scripting so don't blame me if it does anything it shouldn't- it works fine for me anyway! Save the file somewhere then make it executable (right click on the file, then under Properties-Permissions, tick 'Allow executing file as program'). Save the file as 'unmountcamera' in /usr/local/bin (you might need to become root to save the file here, I use Alt-F2, then type 'gksudo nautilus' to become root).

Now when the camera is attached you can either type 'unmountcamera' in the terminal to allow Picasa to import photos, or set nautilus to automatically run the script when you attach the camera (nautilus Edit-Preferences-Media-Photos-Open with other application-custom command, then type 'unmountcamera').

I suspect there is a much simpler way to do this; please feel free to reply here if you know of a better way. In any case, I learnt a bit more about how usb devices are mounted from sorting this one out!

---

### Post by celem on 2008-12-30
Thanks - this issue was bugging me. I've downloaded your script and will give it a try.

---

### Post by celem on 2009-01-02
FYI - I solved the problem in a different way that requires no shell script, and it works with the media open. See my post at:
[http://tinyurl.com/a2b7e4](http://tinyurl.com/a2b7e4)

---

