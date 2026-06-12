---
title: "I don't understand how network drives are seen &amp; remembered"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by DerekP on 2013-01-20
Hiya,

I'm having trouble understanding how Ubuntu, and programs that run in it see, remember and use network folders. I'm pretty experienced with Windows, and this seems foreign.

When i boot, my NAS is rarely visible in Nautilus/Nemo (i have Cinnamon theme installed, but not using it), and i have to manually connect to my shares the first time and then save bookmarks, some programs don't see these bookmarks. (also - after reboot, the bookmarks also don't retain their name - they all say "smb" only).

For example, i tried to upload a file to Skydrive (using Firefox and Opera), and i couldn't because the file was on the NAS and there was no way i could see to browse to it. I had to copy the file, or 'touch' it so that it was in my recent file list.

How can i easily navigate to networked locations?

Thanks.

---

### Post by mapes12 on 2013-01-20
To avoid any definition complications of NAS, could describe your set up please?

---

### Post by 3rdalbum on 2013-01-20
> **DerekP said:**
> Hiya,

I'm having trouble understanding how Ubuntu, and programs that run in it see, remember and use network folders. I'm pretty experienced with Windows, and this seems foreign.

When i boot, my NAS is rarely visible in Nautilus/Nemo (i have Cinnamon theme installed, but not using it), and i have to manually connect to my shares the first time and then save bookmarks, some programs don't see these bookmarks. (also - after reboot, the bookmarks also don't retain their name - they all say "smb" only).

For example, i tried to upload a file to Skydrive (using Firefox and Opera), and i couldn't because the file was on the NAS and there was no way i could see to browse to it. I had to copy the file, or 'touch' it so that it was in my recent file list.

How can i easily navigate to networked locations?

Thanks.

Networked locations are mounted inside the .gvfs folder, which is an invisible folder inside your home directory. You may wish to bookmark this folder. In some circumstances, certain types of local drives may appear here too.

It didn't always work like this, and it might not always work like this in the future, but that's how it is now as long as you're using a Gnome-based desktop (such as Gnome Classic, Gnome Shell, Unity, Mate, Cinnamon etc).

Other desktops like KDE or XFCE work in different ways, so they will mount network directories in a different location.

---

### Post by mapes12 on 2013-01-20
> Networked locations are mounted inside the .gvfs folderIt's a hidden folder but you can create a shortcut to it by right clicking and selecting **Link to**. However, this file is in different locations on 12.04 compared to 12.10, hence my suggestion you let us know your set up.

---

### Post by DerekP on 2013-01-20
Thanks, i'm using Ubuntu (Unity) 12.04, the NAS is a Synology DS411j.

I think i found it here:

/home/me/.gvfs

But it's empty.

---

### Post by DerekP on 2013-01-21
How do i right-click a folder i can't see? Can i temporarily unhide it? I'm guessing in 'terminal', but i don't know how.

And if it's empty, what does that mean?

---

### Post by Elfy on 2013-01-21
> **DerekP said:**
> How do i right-click a folder i can't see? Can i temporarily unhide it? ...

In the file manager - Ctrl+H will unhide and hide folders/files

---

### Post by coldcritter64 on 2013-01-21
> **Elfy said:**
> In the file manager - Ctrl+H will unhide and hide folders/files
This OP, or the View menu in nautilus can be used with the "Show Hidden Files" option. The keyboard combination CTRL + H is also listed in there beside it for your reference. Cheers.

Edit: Is the .gvfs folder empty when you have some network share mounted and accessible ? IIRC it will only have contents when a remote, or possibly in some cases a local, share/s are mounted.

---

### Post by DerekP on 2013-01-23
Codcritter64, i thought they were not there before (a couple of days ago), but now i see they are.

OK, so that works for the original purpose, being able to upload networked files via a bowser. But why is it that the browser can see THAT bookmark, but not the other two bookmarks i created (that reside inside that dir)?

Why doesn't Nautilus just 'see' my NAS at any rate, with no bookmarking?

---

