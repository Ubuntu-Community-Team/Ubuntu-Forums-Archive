---
title: "Can Conky display the size of a folder?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by stormtrooprdave on 2008-10-12
Just started experimenting with Conky and I am trying to get it to display the size of individual folders.

I have a dual boot with XP and all my media is on the XP partition. To display the XP used/size i have this:

${offset 240}${color slate grey}XP: ${color }${fs_used /media/drv0}/${fs_size /media/drv0}
${offset 240}${fs_bar 3,100 /media/drv0}

This shows 116GB/200GB. I now want to show the size of my document folders so for My Music I have done this:

${offset 240}${color slate grey}Music: ${color }${fs_used /media/drv0/Documents and Settings/Dave/My Documents/My Music}/${fs_size /media/drv0/Documents and Settings/Dave/My Documents/My Music}
${offset 240}${fs_bar 3,100 /media/drv0/Documents and Settings/Dave/My Documents/My Music}

However this also shows 116GB/200GB but My Music folder only has 15GB in it. What do I need to do to get it to display the actual size of My Music, My Pictures and My Videos?

(I've looked in other conky threads but they move so fast that my problem keeps getting overlooked)

---

### Post by hwnddawg on 2008-10-12
Also have (several) dual-boots.  In Kubuntu, the KDirStat utility really does a great job, quick too!  The display is like an expandable tree format.  So you can see info for a drive, then click on directories to expand and see the info for those.  Great for seeing where to clean-out temp files (e.g. browser cache, old packages) and other cruft.

HTH!

Winthrop Yu

---

### Post by Tom--d on 2008-10-12
> **stormtrooprdave said:**
> Just started experimenting with Conky and I am trying to get it to display the size of individual folders.

I have a dual boot with XP and all my media is on the XP partition. To display the XP used/size i have this:

${offset 240}${color slate grey}XP: ${color }${fs_used /media/drv0}/${fs_size /media/drv0}
${offset 240}${fs_bar 3,100 /media/drv0}

This shows 116GB/200GB. I now want to show the size of my document folders so for My Music I have done this:

${offset 240}${color slate grey}Music: ${color }${fs_used /media/drv0/Documents and Settings/Dave/My Documents/My Music}/${fs_size /media/drv0/Documents and Settings/Dave/My Documents/My Music}
${offset 240}${fs_bar 3,100 /media/drv0/Documents and Settings/Dave/My Documents/My Music}

However this also shows 116GB/200GB but My Music folder only has 15GB in it. What do I need to do to get it to display the actual size of My Music, My Pictures and My Videos?

(I've looked in other conky threads but they move so fast that my problem keeps getting overlooked)


When you have this /home/tom/Desktop/Apple Orange it will not work, due to a space, you need this:

/home/tom/Desktop/Apple\ Orange 
That will now work.

---

### Post by hellion0 on 2008-10-12
Just a stab in the dark on my part, but I don't think the normal fs_bar and such on Conky will work for a single folder, seeing as the folder is not a partition in itself. In which case, it'll default to reading the size and capacity and such of the partition the folder is located on.

---

### Post by ProgramErgoSum on 2008-10-12
Don't know about Conky. Would [inotify]("http://inotify.aiken.cz/?section=inotify&page=about&lang=en") help ?

---

### Post by stormtrooprdave on 2008-10-12
> **Tom--d said:**
> When you have this /home/tom/Desktop/Apple Orange it will not work, due to a space, you need this:

/home/tom/Desktop/Apple\ Orange 
That will now work.

Still could not get it to work despite a hundred different permutations of backslashes and quotation marks.

In the terminal I did get the following command to display the directory size:

du -sh /media/drv0/Documents\ and\ Settings/Dave/My\ Documents/My\ Music

Can this be used in conky?

---

### Post by stormtrooprdave on 2008-10-12
I got it to display the size of the folder using the execi du -sh command but it displays as:

16G /media/drv0/Documents\ and\ Settings/Dave/My\ Documents/My\ Music

This messes up my layout and looks terrible, plus there would be no bar to go with it. 

I know the information is there because if i right click properties on the folder it says Contents 15.5GB and Free Space 83.5GB, I just need to know how to get this displayed in conky?

---

### Post by splat_ed on 2008-10-15
I've been mucking about with this to try and do the same and I think this might be the best way...

du -sh *your directory here* | awk '{print $1}'

as we only need the first column so awk can cut everything else out

Mike
(complete beginner, just learnt about pipes and stuff recently :))

EDIT: New thought for today... to get the bar use $execibar du -sh *your directory here* | awk '{print $1}' | tr -d A-Za-z to get rid of the letter at the end (then you'll have a number for a bar). Next problem though will be it won't care about Mb, Gb etc - not tried personally yet

---

### Post by stormtrooprdave on 2008-10-15
> **splat_ed said:**
> I've been mucking about with this to try and do the same and I think this might be the best way...

du -sh *your directory here* | awk '{print $1}'

as we only need the first column so awk can cut everything else out

Mike
(complete beginner, just learnt about pipes and stuff recently :))

EDIT: New thought for today... to get the bar use $execibar du -sh *your directory here* | awk '{print $1}' | tr -d A-Za-z to get rid of the letter at the end (then you'll have a number for a bar). Next problem though will be it won't care about Mb, Gb etc - not tried personally yet

Thanks for your help - the first command worked great and just displayed the numerical size of the folder.

I couldnt get the bar to work though - it came up with this error:

sh: Syntax error: Missing '}'

---

### Post by EdwardMorris on 2010-05-26
I'm having this problem even while staying within the linux side

root: ${fs_used_perc /}% ${fs_bar 6 /}
home: ${fs_used_perc /home/emorris}% ${fs_bar 6 /home/emorris}

Both show the same 14%, no idea why.

---

### Post by bone2006 on 2010-08-16
The execp does it

${offset 640}${color}Dropbox: ${execp du -sh /home/Tim/ | cut -c 1-5}

Here's what I'm using to display the space in a person's dropbox folder.

---

### Post by Off Topic on 2012-09-25
Execpi IS the answer.  Thank You.

---

