---
title: "trash"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-03-21
Hi
I have put some files in t.he trash 2 off which I want to recover, and I want to see what else is in the trash bin

Could some one tell me where I could find the trash bucket please

Sorry that should have read as rubbish bin

Hang on now, I have found the rubbish bin, but the files I am looking for are in "Trash" they are two files that I was using in (windows, microdoze) it is it, that is reporting as trash? and the 2 you-tube files that I deleted where not in rubbish bin here on Ubuntu

Confusing ain't it

Dave

---

### Post by airplanesimen on 2012-03-21
If you cant find the files in the trash-can, i bet you have deleted the files for good, and not just put them in the trash :(  What version of linux are you using?

---

### Post by DaveMcC on 2012-03-21
Hidden file, 
There was a dot in front of trash, which I missed seeing
But I now have my 2 u-tubes back 

So we shall called this one solved

Dave

---

### Post by HiImTye on 2012-03-21
you put them in the trash while using Windows?

---

### Post by 3rdalbum on 2012-03-21
"Trash" and "Rubbish Bin" are the same.

I'm not exactly sure what you're saying - did you say that you put some files in the Recycle Bin on Windows and you can't find them on Ubuntu? They don't use the same trash folder; they are different trashes (it's like saying "I put the envelope in the bin in the kitchen, why can't I find it in my laundry bin?").

If you have emptied the Rubbish Bin/Trash, then the files are gone. If you right-clicked a file and chose "Delete" from the menu, or pressed Shift-Backspace with it highlighted, then the file is gone immediately without ever entering the Rubbish Bin/Trash. If however you right-clicked the file and chose "Move to Rubbish Bin" instead, and have NOT emptied the rubbish bin, then the files should still be in there.

To make things a little more confusing, if you have been using a file browser as root (you know, with 'sudo') and used the "Move to Rubbish Bin" function in the root file browser, then these files will be in root's trash, not in your normal user account's trash. You'd need to open a root file browser again and look under Rubbish Bin on the left side of that window, to access the files in the root Rubbish Bin.

---

### Post by DaveMcC on 2012-03-21
No, I deleted them in Ubuntu, It's only when I moved down, low down to micro-doze that I went, oh, oh I needed them 2, video tutorial's for Serif
It was only when I was trying to find them again, I discovered (".Trash" hidden file, )

I take it was made by Ubuntu

---

### Post by ajgreeny on 2012-03-21
I am also not at all sure what you did, but if you put files that were on your windows partition into the trash while using ubuntu, it is a warning not to do so again.

They will not be put into the windows recycle bin, nor will they be in your usual ubuntu user's trash, but in a trash made on the windows partition while it's mounted, that may be wiped out when the windows partition is unmounted.

Just a warning!  Delete files from windows while running windows, not when running ubuntu.

---

### Post by d4m1r on 2012-03-21
.trash is different from the regular Trash.

.trash = its a hidden folder I only see gets created when delete stuff from removable media (ex: USB stick)

Trash = local trash bin (no hidden folder created for local files) but you are still able to restore stuff if its in there.

---

