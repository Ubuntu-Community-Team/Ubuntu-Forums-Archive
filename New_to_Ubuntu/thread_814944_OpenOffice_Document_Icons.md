---
title: "OpenOffice Document Icons"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by X40nick on 2008-06-01
Hi,

I did install IBM Lotus Symphony, but I removed it as I didn't like it. I followed the instructions and it has gone, but there are probably traces of it leftover.

I was going to open a ODT document and I get the IBM Lotus Symphony Document icon, not the default OpenOffice icon, this is driving me crazy!!! 

How can I change it so that when I go to open something I get the OpenOffice icon? It happens when I am trying to open something with OpenOffice open? 

Please help!

Thank you so much!

Nick

---

### Post by sayakb on 2008-06-01
Are you talking about the splash screen?
Then perhaps this might help: [http://ubuntuforums.org/showthread.php?t=6978](http://ubuntuforums.org/showthread.php?t=6978)

---

### Post by X40nick on 2008-06-01
No, I am talking about the icons when I open a document.

---

### Post by sayakb on 2008-06-01
The toolbar icons? Sorry, it's not clear. Can you post a screenshot?

---

### Post by durand on 2008-06-01
Maybe the icons in the filemanager?

---

### Post by X40nick on 2008-06-01
Right, when I open OpenOffice Word Processor and then click open. I get the file window, I navigate to the folder I want, and then the document. I see the IBM Lotus Symphony icon for all the ODT formatted documents?

Do you see what I'm saying?

Thank you.

Nick

---

### Post by durand on 2008-06-01
Right, that is to do with the gtk icon theme. Go to System - Preferences - Appearance and try changing the theme, then back again. It might be that lotus added its own icons for odt files. I guess you could use a different icon theme but you would have to investigate exactly what icons lotus added which would probably be somewhere in /usr/share/icons/.

---

### Post by X40nick on 2008-06-01
Thanks, I did try that but got no where. Here is a screenshot, this is such a pain in the backside!!!

Thank you.

Nick

---

### Post by X40nick on 2008-06-01
I get that damn logo with ALL the ODT documents when opening them via OpenOffice.

Nick

---

### Post by durand on 2008-06-01
So, what's the default application to open odt. Right click on the document, then click on Properties, Open With.

---

### Post by X40nick on 2008-06-01
The default application to open ODT documents is, Openoffice.

Thanks,

Nick

---

### Post by durand on 2008-06-01
Hmmm...Do other icon themes have the same problem? This is getting kinda annoying now.

---

### Post by X40nick on 2008-06-01
Yes, I just don't see what is causing it. 

Please don't give up!

Thanks,

Nick

---

### Post by sayakb on 2008-06-01
Goto /usr/share/icons 
Do you see the icon there? If not, then search in /usr/share/icons/Human/*look for all sizes*/apps
Tell me if you find the icon. And if you do, delete it by launching nautilus as root:
```
gksudo nautilus
```

---

### Post by durand on 2008-06-01
Ok, look in /usr/share/icons/ If there is an icon like the one that's displayed on odf files, rename it and restart nautilus, etc. 

EDIT: Do the files have this icon in nautilus (the file manager) as well?
EDIT2: D'oh! Replied too late :P

---

### Post by X40nick on 2008-06-01
No, I have just looked and the icon isn't there?

Thanks,

Nick

---

### Post by durand on 2008-06-01
Did you install Symphony using a deb package? If you did, try completely removing it using synaptic. Maybe you should redownload the package and rerun any uninstaller script there may be? Also, try the symphony forums if there is one.

I need to do some exam revision now, I'll try to reply when I can.

---

### Post by sayakb on 2008-06-01
Look inside the /usr/share/icons/Human/*size*/mimetypes folder also..

---

### Post by durand on 2008-06-01
Do the files have this icon in nautilus (the file manager) as well?

---

### Post by sayakb on 2008-06-01
Ok.. now this may finally work. Download [this]("http://gnome-look.org/content/download.php?content=56625&id=1&tan=91538841") icon package. Now goto System->Preferences->Appearance and drag n drop this downloaded file upon the window, which should install the icon. Now click **Customize** and then **Icons** tab, and select *NuovoXT.2.2 *from there.
Now check again.

---

### Post by X40nick on 2008-06-01
OK, thank you.

No, there is no icon there either. :(

Thanks,

Nick

---

### Post by durand on 2008-06-01
```
find /usr/share/icons/ | grep symphony
```
Replace symphony with ibm and lotus as well and try it again. The icon must be somewhere. Also, does it show up in nautilus as another user? If it doesn't, the icon is in your home folder somewhere.

---

### Post by durand on 2008-06-01
Oh and what does the A in the icon mean....

---

### Post by sayakb on 2008-06-01
Check ~/.icons folder also. Though Nuovo should fix the problem.

---

### Post by X40nick on 2008-06-01
Nuovo did not fix the problem.

I did the find thing, deleted everything it found and I will restart it now. 

But I think I am getting close to the end!

Thank you!

Nick

---

### Post by X40nick on 2008-06-01
Ctrl+Alt+Bksp (restarted)

Tried new user account, still same problem.

Tried mine, same problem.

I really don't know what to do? Please don't give up!

Thank you.

Nick

---

### Post by sayakb on 2008-06-01
Where did you find the icon?

---

### Post by The Cog on 2008-06-01
That's the OpenOffice file finder isn't it? Try looking in OpenOffice's menu - Tools->Options and then look in either View or Appearance and see if there's a setting there. View has  a setting for icon style.

---

### Post by X40nick on 2008-06-01
I found the icons, in various folders. There was just one, in some different sizes?

Still no luck with changing the view?

Thanks,

Nick

---

### Post by sayakb on 2008-06-01
Install catfish (search tool, you need a GUI alternative for the command line search tools at this point)
And put the search criteria as the icon names that you deleted (For eg, it can be odt or office or whatever the icon names were). If you see a similar icon, delete it. Search /usr/share/icons and ~/.icons

---

### Post by X40nick on 2008-06-01
PROBLEM SOLVED!!! I installed IBM Lotus Symphony 1, and it seems to have sorted itself out!!! I may keep it, or try and remove it. 

Thank you though for all your work, I am really grateful for it.

Kind Regards,

Nick

---

### Post by durand on 2008-06-01
This is really silly. Try opening the package used to install Sympon....

Nevermind! Looks like you solved it! That was a heck of a weird bug.

---

### Post by durand on 2008-06-01
Remember to mark the thread as solved. Also, edit your OP so that others with this problem will be able to find an answer quickly.

---

