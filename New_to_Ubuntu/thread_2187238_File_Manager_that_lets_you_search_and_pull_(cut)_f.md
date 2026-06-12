---
title: "File Manager that lets you search and pull (cut) files from folders (Windows 7)"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by hardkhora on 2013-11-11
Every now and then, I look for a file manager that can do what I've been looking for and it is going on years. I know I haven't looked as detailed as I could but I went over this article recently: [http://www.tuxarena.com/2011/06/20-file-managers-for-ubuntu/](http://www.tuxarena.com/2011/06/20-file-managers-for-ubuntu/)
And it seems there still isn't something that can do what Windows XP and Windows 7 (the later easier than the former) have been doing for a long time now...don't care about Windows 8.
I simply want to be able to do a search on a folder, and then be able to move all the files from subfolders to another folder. I've tried with Cateye in the past and all I could do was a copy and not a cut.

An example in Xubuntu 13.10: Created several files made 3 folders put  a few files in each folder and then put one folder into another until I  had a stack. Right clicked and did a search, pulled up all of the  files, sorted them, selected them, and then tried Ctrl-X, tried right  clickin but I only get for an option (that is relavent) Copy Location.  Can't move the files from out of the folders.

Anyone have a better suggestion?

---

### Post by linuxguru43 on 2013-11-11
Have you tried PCMANFM?   sudo apt-get install pcmanfm  It is titled File Manager. The thing I love about PCMANFM is you can switch it to root access and cut and paste anything anywhere on the system. Faster than using CL for me.

---

### Post by Mark Phelps on 2013-11-11
You need to be aware that if you make changes to files and/or folders in a Win7 OS partition from inside Ubuntu, you risk filesystem corruption in Windows, which could then render Win7 unbootable.  To be safe, you should only ever mount a Win7 OS partition read-only.

---

### Post by amanchesterman on 2013-11-11
Umm ... not sure that I have understood exactly what you want to do ... but using Thunar (with Xubuntu) I can go into a folder, search-and-select all files that match a given pattern in the filename, and then simply drag-and-drop those files into a different folder or subfolder. Would that meet your needs?

---

### Post by hardkhora on 2013-11-11
> [COLOR=#000000]Have you tried PCMANFM? sudo apt-get install pcmanfm It is titled File Manager. The thing I love about PCMANFM is you can switch it to root access and cut and paste anything anywhere on the system. Faster than using CL for me.[/COLOR]
I use Lubuntu most of the time, PCMANFM doesn't allow you to do this, not on 13.10 at least.

> [COLOR=#000000]Umm ... not sure that I have understood exactly what you want to do ... but using Thunar (with Xubuntu) I can go into a folder, search-and-select all files that match a given pattern in the filename, and then simply drag-and-drop those files into a different folder or subfolder. Would that meet your needs?[/COLOR]
Last few times I've tried this it only copies the file, doesn't move the file.

Goal: I have a folder with a lot of subfolders. In those sub folders I have a lot of files. I want those files in a different folder without having to copy them first as this takes more time and wear on my harddrive.

---

### Post by linuxguru43 on 2013-11-11
To switch to root access in Thundar click Tools and then click Open Current Folder as Root. Now it will cut and paste anything anywhere you want. Hopefully you know what you are doing.This would be as close as you can get to the same feature in Windows Explorer. You can mess up a system very quickly if you cut and paste files around though so be careful.

---

### Post by hardkhora on 2013-11-11
> **linuxguru43 said:**
> To switch to root access in Thundar click Tools and then click Open Current Folder as Root. Now it will cut and paste anything anywhere you want. Hopefully you know what you are doing.This would be as close as you can get to the same feature in Windows Explorer. You can mess up a system very quickly if you cut and paste files around though so be careful.
[COLOR=#000000]The issue isn't that I don't have rights to move the files. It is I can't do a search so I can get a full list of files in folders and them pull them out of those folders so that I can move them to another location.[/COLOR]

---

### Post by linuxguru43 on 2013-11-11
Have you tried using the Find in Thundar?  Click Tools >> Find

---

### Post by amanchesterman on 2013-11-11
"Last few times I've tried this it only copies the file, doesn't move the file."
There's some discussion of this in other threads in this forum: some people seem to encounter this behaviour, others don't. The view seems to be that it isn't intrinsically a problem with Thunar and that it depends on which desktop environment (and which version thereof) you are using.
Personally, I'm not expert in these matters; I'm using Xubuntu 12.10 and drag-and-drop moves files for me, but that's not much help to you. However it looks as though Thunar may have the capability you need, if you can find a solution to the copy vs. move problem. Have you tried using the Xfce environment instead of Lubuntu?

---

### Post by hardkhora on 2013-11-11
> **linuxguru43 said:**
> Have you tried using the Find in Thundar?  Click Tools >> Find

Yes, it finds the file but it is the cut/paste that is the road block.

> **amanchesterman said:**
> "Last few times I've tried this it only copies the file, doesn't move the file."
There's some discussion of this in other threads in this forum: some people seem to encounter this behaviour, others don't. The view seems to be that it isn't intrinsically a problem with Thunar and that it depends on which desktop environment (and which version thereof) you are using.
Personally, I'm not expert in these matters; I'm using Xubuntu 12.10 and drag-and-drop moves files for me, but that's not much help to you. However it looks as though Thunar may have the capability you need, if you can find a solution to the copy vs. move problem. Have you tried using the Xfce environment instead of Lubuntu?

I haven't tried Xubuntu since 12.04. Just to be clear. For you, you're able to search the file, and then move it (not just copy it)? I'd be willing to use Xubuntu again if that is true.

Update, downloading Xubuntu 13.10 now to test when I get home.

---

### Post by Impavidus on 2013-11-11
I hardly ever use drag-and-drop (I love terminals), but I just tried in thunar. Drag-and-drop in the same partition defaults to move (inode stays the same), drag-and-drop to a different partition defaults to copy (original file remains).

---

### Post by hardkhora on 2013-11-11
> **Impavidus said:**
> I hardly ever use drag-and-drop (I love terminals), but I just tried in thunar. Drag-and-drop in the same partition defaults to move (inode stays the same), drag-and-drop to a different partition defaults to copy (original file remains).
Awesome. Just so I can try to replicate, were you using thunar to search a folder before you did a drag-and-drop? Or another search program?

---

### Post by The Cog on 2013-11-11
Ctrl-X and Ctrl-V (or Edit/Cut and Edit/Paste) can cut and paste files in most file managers, even to move files between different partitions, provided you have required permissions.

---

### Post by hardkhora on 2013-11-11
Just tried in Xubuntu 13.10 and it doesn't work. I have the same issue  I've had for years. My process, Created several files made 3 folders put  a few files in each folder and then put one folder into another until I  had a stack. Right clicked and did a search, pulled up all of the  files, sorted them, selected them, and then tried Ctrl-X, tried right  clickin but I only get for an option (that is relavent) Copy Location.  What are you all doin' that I'm not?

---

### Post by hardkhora on 2013-11-11
Update! I found Caja 1.4.0 works!!! I can pull out files. Thank you Linux Mint. I just tested this too. I have the answer I've been needing.
[COLOR=#000000]Is there any way to get Caja in Lubuntu? I did some searching and the only thing I came up with is that it is paired with Linux Mint MATE.[/COLOR]

---

### Post by hardkhora on 2013-11-11
**Un-needed, sorry**

---

### Post by jerome1232 on 2013-11-11
Nautilus does this by default in 13.04 for me. If I open a folder and start searching, all sub-folders get searched, I can then select all and cut or copy then paste the files to a new location.

---

### Post by alphacrucis2 on 2013-11-11
I just tried this with nautilus/files in gnome 3.10 and it appears to work? So there is a plus for the oft' maligned Nautilus

---

### Post by hardkhora on 2013-11-12
> **jerome1232 said:**
> Nautilus does this by default in 13.04 for me. If I open a folder and start searching, all sub-folders get searched, I can then select all and cut or copy then paste the files to a new location.
13.04 of Ubuntu? I'll have to try Nautilus in Lubuntu again.

Maybe off topic, but is there any way to get Caja in Lubuntu? I did some searching and the only thing I came up with is that it is paired with Linux Mint MATE.

---

### Post by jerome1232 on 2013-11-12
> **hardkhora said:**
> 13.04 of Ubuntu?

Yes plain old Unity.

---

### Post by hardkhora on 2013-11-12
> **jerome1232 said:**
> Yes plain old Unity.
I dislike unity, but i'll try out the file manager in Lubuntu.
[COLOR=#000000]Update: Nautilus works fine with searching moving in Lubuntu!
[/COLOR][COLOR=#000000]
Is there any way to get Caja in Lubuntu? I did some searching and the only thing I came up with is that it is paired with Linux Mint MATE.[/COLOR]

---

