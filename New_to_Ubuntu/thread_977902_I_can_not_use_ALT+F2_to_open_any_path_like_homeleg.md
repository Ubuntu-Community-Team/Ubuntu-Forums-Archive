---
title: "I can not use ALT+F2 to open any path like /home/legolas/"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-10
Hi
Thank you for reading my post
I have problem with opening any path (directory) using ALT+F2, for example when I type ALT+F2 and then type /home/legolas/ into it, instead of opening nautilus it opens VLC media player.

What should I do now to fix this problem?
Thanks

---

### Post by MasterSander on 2008-11-10
type nautilus xD

---

### Post by -Zeus- on 2008-11-10
that might be a workaround, but it doesn't fix it.  Can you check your preferred applications?  preferences> preferred applications

---

### Post by MasterSander on 2008-11-10
does it open a file from your home folder when you type it or just VLC itself?

---

### Post by legolas_w on 2008-11-10
In the Prefered Application, I just can customize web browser, mail reader, multimedia and so on, but it has no tab for file browsing.

To open my home folder I open a nautilus and navigate to my home folder or type /home/legolas/ into the nautilus address bar.

When my home folder is open in the nautilus I can open any of the folders which are inside it easily with no problem, just double click and it opens.

When I want to open Places > Home Folder, it opens the VLC and VLC status bar shows file:///home/legolas

I should say that it is not working correctly after I upgrade to 8.10 from 8.04

Thanks for your help.

---

### Post by MasterSander on 2008-11-10
try reinstalling nautilus or try this first. in terminal type killall nautilus then type nautilus, any difference?

---

### Post by -Zeus- on 2008-11-10
try going to any folder, right clicking on it, selecting properties, then go to the open with tab.  That should be set to 'open folder'

---

### Post by -Zeus- on 2008-11-10
MasterSander, I realize that you're trying to help, but throwing out random things like 'reinstall' or 'kill it then try again' will not help him solve his problem

---

### Post by MasterSander on 2008-11-10
with all due respect, they're not random. I've had problems with nautlis before (wouldn't display my desktop) and killing an relaunching helped.

---

### Post by -Zeus- on 2008-11-10
if this error had anything to do with nautilus, that would be vaild advice, but I fail to see how vlc running could have anything to do with nautilus.  I bet you 100:1 that nautilus is never getting called in that instance

---

### Post by MasterSander on 2008-11-10
yeah but I don't think the problem isn't either the fact that /home gets opened because it's not the standard application, cause it either opens or gives permission denied. When I reread this thread it's more likely caused by a wrong shortcut.

---

### Post by legolas_w on 2008-11-10
> **-Zeus- said:**
> try going to any folder, right clicking on it, selecting properties, then go to the open with tab.  That should be set to 'open folder'

Thank you very much. it resolved the problem, I can not understand how does opening folders were assigned to VLC:confused:

---

