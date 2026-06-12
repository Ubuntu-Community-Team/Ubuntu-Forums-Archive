---
title: "[SOLVED] Problem with firefox, immediately hangs-up on start?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by germanix on 2008-10-05
I have been on the Ubuntu-Forum all day without any problems, when all of a sudden firefox hanged-up. When it does this it covers the whole of the screen, so the top and bottom panels on the Ubunto desktop are no more visible. You cannot close firefox,(the top panel here also nor visible) nor can you restart the computer. I have re-booted a few times (by using the reset button on the computer) but everytime I start Firefox it immediatly hangs up. The problem realy started as follows:
I had closed firefox and used the option for firefox to save the settings of the current sitting for the next start-up, Firefox closed. I then had a website that I had downloaded previously still stuck on the desktop. For a minute I was not sure what it was, so I clicked it to open. It opened firefox again, then the screen blinked a couple of times and firefox hanged-up.
I am now on my lap-top. Any ideas how I could fix this problem?

---

### Post by AndyCooll on 2008-10-05
You could delete the .mozilla folder in your home directory (making a backup copy of it first, just in case you want to retrieve things like your bookmarks).

:cool:

---

### Post by germanix on 2008-10-05
Mozilla folder? I dont seem to have one. Where do I find it?

---

### Post by bobnutfield on 2008-10-05
To see your mozilla folder, you have to enable "View Hidden Files" from the view menu in your home directory.  But. before you delete your .mozilla folder, try to delete the cache first.  Go to /home/<you>/.mozilla/firefox/<something).default and delete the cache folder.  It will be recreated for you when you reopen firefox.  It may be that you have a locked file.

---

### Post by germanix on 2008-10-05
What does the <something) mean? I get a syntax error ?

---

### Post by bobnutfield on 2008-10-05
You folder will have a differ name to mine. It will look something like this:

> /home/bob/.mozilla/firefox/ao1mlqw6.default/cache

It is the cache folder you want to delete.  Some settings will not work correctly, such the forum layout here, but it wil correct itself quickly.

---

### Post by germanix on 2008-10-05
I understand what you are telling me, but I do not know the name of the folder or where to get it. So I cannot complete the command!

I found it, dumb old me. forgot that you already told me where it was.

---

### Post by germanix on 2008-10-05
OK I am now in the default directory and can see the cache. can I delete it from this position or must I cd to cache to delete? how do I delete?

---

### Post by bobnutfield on 2008-10-05
I have had to do this a couple of times, and I simply do it from the GUI.  Navigate to that folder and right click on it, and select delete.  It does not require sudo priveledge.

---

### Post by germanix on 2008-10-05
Deleting the cache did not solve the problem, so I have now deleted the mozilla file and it seems to have worked. I thank you bobnutfield and andycooll for all of your help. Wish you a nice day.

---

