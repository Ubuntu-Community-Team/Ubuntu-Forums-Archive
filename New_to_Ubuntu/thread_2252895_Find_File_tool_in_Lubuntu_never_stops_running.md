---
title: "Find File tool in Lubuntu never stops running"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-11-15
I installed Lubuntu 14.04.1 LTS a few months ago. For some reason the "Find Files" tool in the PCManFM 1.2.0 file manager never stops running. You just have to close it to get it to stop, which is very inconvenient. It did not do this before. I have added a screenshot that shows the same single file, "FindFileTester", being "found" repeatedly. I've added a screenshot below to illustrate this. The mouse arrow in the screenshot should, however, be a running circle, not an arrow, because it never stops running unless it is closed. 

QUESTION: Any idea what I can do about this? 

Thanks,

Able

[ATTACH=CONFIG]257980[/ATTACH]

---

### Post by AbleTassie on 2014-11-15
To be more accurate, the Find Files tool never stops when searching in the Home folder. It does stop in smaller folders, however. I would like to be able to search in the home folder without this problem. Searching smaller individual folders would be very inconvenient.

Thanks,

Able

---

### Post by sudodus on 2014-11-15
Maybe there is an infinite loop because of some symbolic link.

Do you see the same problem with the command line tool find?

```
find ~ -iname "*filefiletester*"
```

or

```
find -L ~ -iname "*filefiletester*"
```

The latter command looks for symbolic links, and in my computer it finds a 'file system loop'.

---

### Post by bapoumba on 2014-11-15
Just to point out that I do not see this behaviour if I search in my home for a file that has no symbolic link as sudodus pointed out. Searching on my / for a file that does have one shows the same as you do, ie the circle keeps spinning even after finding the string pattern. To note, I have let it run while I'm googling on that, and it found 2 additional files. I suppose PCManFM becomes very slow if you have a large number of files to search. Letting it run to see if it's going to stop by itself.
[http://sourceforge.net/p/pcmanfm/bugs/621/](http://sourceforge.net/p/pcmanfm/bugs/621/)

---

### Post by AbleTassie on 2014-11-15
> **sudodus said:**
> Maybe there is an infinite loop because of some symbolic link.

Do you see the same problem with the command line tool find?

```
find ~ -iname "*filefiletester*"
```



Hi Sudodus, I don't get anything with this first command.

> **sudodus said:**
> 

or

```
find -L ~ -iname "*filefiletester*"
```

The latter command looks for symbolic links, and in my computer it finds a 'file system loop'.

With this second command, it apparently finds files and just keeps searching and apparently never stops. See screenshot below.

Thanks,

Able

[ATTACH=CONFIG]257991[/ATTACH]

---

### Post by AbleTassie on 2014-11-15
> **bapoumba said:**
> Just to point out that I do not see this behaviour if I search in my home for a file that has no symbolic link as sudodus pointed out. Searching on my / for a file that does have one shows the same as you do, ie the circle keeps spinning even after finding the string pattern. To note, I have let it run while I'm googling on that, and it found 2 additional files. I suppose PCManFM becomes very slow if you have a large number of files to search. Letting it run to see if it's going to stop by itself.
[http://sourceforge.net/p/pcmanfm/bugs/621/](http://sourceforge.net/p/pcmanfm/bugs/621/)

Bapoumba,

Thanks for your reply. I do not really understand your reply, however. I am not sure what a symbolic link is. Do you think I should report this as a bug at the link you gave? I searched for the bug at that link and it apparently is not there.

Thanks,

R.

---

### Post by vasa1 on 2014-11-15
One way to look at symbolic links is to consider them to be "shortcuts" to the real file which could be anywhere else. Having symbolic (aka logical) links saves space by not having to reproduce the actual files in several locations. I may have oversimplified but you can search the 'net for more info.

---

### Post by sudodus on 2014-11-16
I'm rather sure now, that your problem is related to a 'file system loop' cause by some symbolic link. Maybe you can identify where you have that link, and make a search script, that searches everywhere except where you have that link (that causes a file system loop).

---

### Post by bapoumba on 2014-11-16
> **RMcGinnis said:**
> Bapoumba,

Thanks for your reply. I do not really understand your reply, however. I am not sure what a symbolic link is. Do you think I should report this as a bug at the link you gave? I searched for the bug at that link and it apparently is not there.

Thanks,

R.

In a way, I think PCManFM is slow searching places where there is a large number of different files and substructures.
Here is a search on my root file system that is taking ages to complete :
```
search:///?recursive=1&show_hidden=0&name=km_mile*&name_ci=1
```
Searching for files that start with "km_mile", I know I have one in my /home, there are no symbolic link. The search has currently been going on for 15 mins, is hogging my cpu and memory (this is a poor old laptop..).
If I run the exact same search in my /home (the file is one level below in another file), the hit is immediate.

---

### Post by matt_symes on 2014-11-16
Hi

you can use the type parameter with the lower case L and the find command from the command line to find symbolic links


```
find ~ -type l
```

Kind regards

---

### Post by AbleTassie on 2014-11-17
> **bapoumba said:**
> In a way, I think PCManFM is slow searching places where there is a large number of different files and substructures.
Here is a search on my root file system that is taking ages to complete :
```
search:///?recursive=1&show_hidden=0&name=km_mile*&name_ci=1
```
Searching for files that start with "km_mile", I know I have one in my /home, there are no symbolic link. The search has currently been going on for 15 mins, is hogging my cpu and memory (this is a poor old laptop..).
If I run the exact same search in my /home (the file is one level below in another file), the hit is immediate.

Thanks Bapoumba, Matt and Sudodus,

I think maybe you are all correct in some way about this problem. My laptop is old too and I think PCManFM is slow and I think it may eventually stop searching after a long time, even when searching in a high level folder. In fact I think I observed this recently. On the hand, since there was only one copy of the sought document (or file), FindFileTester, why would the file keep showing up repeatedly as it does?

I searched for symbolic links with the command that Matt gave and I got the results below, which may explain the behaviour:

name@name:~$ find ~ -type l
/home/name/.mozilla/firefox/z37wz69t.default-1410575131272/lock
/home/name/.wine/dosdevices/d::
/home/name/.wine/dosdevices/e:
/home/name/.wine/dosdevices/f::
/home/name/.wine/dosdevices/e::
/home/name/.wine/dosdevices/z:
/home/name/.wine/dosdevices/c:
/home/name/.wine/drive_c/users/name/My Documents
/home/name/.wine/drive_c/users/name/My Videos
/home/name/.wine/drive_c/users/name/My Pictures
/home/name/.wine/drive_c/users/name/My Music
/home/name/.wine/drive_c/users/name/Desktop
name@name:~$ 

Thanks,

R.

---

### Post by matt_symes on 2014-11-17
Hi

> **RMcGinnis said:**
> Thanks Bapoumba, Matt and Sudodus,

I think maybe you are all correct in some way about this problem. My laptop is old too and I think PCManFM is slow and I think it may eventually stop searching after a long time, even when searching in a high level folder. In fact I think I observed this recently. On the hand, since there was only one copy of the sought document (or file), FindFileTester, why would the file keep showing up repeatedly as it does?

I searched for symbolic links with the command that Matt gave and I got the results below, which may explain the behaviour:

name@name:~$ find ~ -type l
/home/name/.mozilla/firefox/z37wz69t.default-1410575131272/lock
/home/name/.wine/dosdevices/d::
/home/name/.wine/dosdevices/e:
/home/name/.wine/dosdevices/f::
/home/name/.wine/dosdevices/e::
/home/name/.wine/dosdevices/z:
/home/name/.wine/dosdevices/c:
/home/name/.wine/drive_c/users/name/My Documents
/home/name/.wine/drive_c/users/name/My Videos
/home/name/.wine/drive_c/users/name/My Pictures
/home/name/.wine/drive_c/users/name/My Music
/home/name/.wine/drive_c/users/name/Desktop
name@name:~$ 

Thanks,

R.

That's a number of wine symbolic links you have there. 

I can almost guarantee that they are the problem especially, I expect, the symlinks in the "dosdevices" directory.

If I remember correctly, they point to your root folder and other hard drives and such like. That can be a huge number of files to search and you only need one symbolic link loop.....

So you can either remove the links in wine (the may be a good idea from a security and malware point of view anyway) or you can make sure you don't follow symbolic links when you are searching.

What would you like to do ?

EDIT: to double check can you post the output of this command into your next post

```
ls -l ~/.wine/dosdevices/*
```

Kind regards

---

### Post by AbleTassie on 2014-11-17
> **matt_symes said:**
> Hi



That's a number of wine symbolic links you have there. 

I can almost guarantee that they are the problem especially, I expect, the symlinks in the "dosdevices" directory.

If I remember correctly, they point to your root folder and other hard drives and such like. That can be a huge number of files to search and you only need one symbolic link loop.....

So you can either remove the links in wine (the may be a good idea from a security and malware point of view anyway) or you can make sure you don't follow symbolic links when you are searching.

What would you like to do ?

EDIT: to double check can you post the output of this command into your next post

```
ls -l ~/.wine/dosdevices/*
```

Kind regards

I need WINE to use a program that I cannot get to run in Linux/Lubuntu. So I am not sure what to do in that regard, although since I am dual booting Lubuntu and Windows XP, I could uninstall WINE and just use the program on the Windows side, when needed. I suppose I could also just have the unistalled version of WINE on hand and just install it on the Lubuntu side when needed and then unistall it as well. 

The output from the command above is:

name@name:~$ ls -l ~/.wine/dosdevices/*
lrwxrwxrwx 1 name name 10 Aug 14 16:32 /home/name/.wine/dosdevices/c: -> ../drive_c
lrwxrwxrwx 1 name name  8 Aug 14 16:43 /home/name/.wine/dosdevices/d:: -> /dev/sr0
lrwxrwxrwx 1 name name 27 Nov 15 19:03 /home/name/.wine/dosdevices/e: -> /media/name/FreeAgent Drive
lrwxrwxrwx 1 name name  9 Aug 15 19:46 /home/name/.wine/dosdevices/e:: -> /dev/sdb1
lrwxrwxrwx 1 name name  8 Aug 15 19:46 /home/name/.wine/dosdevices/f:: -> /dev/sdb
lrwxrwxrwx 1 name name  1 Aug 14 16:32 /home/name/.wine/dosdevices/z: -> /


Thanks,

R.

---

### Post by matt_symes on 2014-11-17
Hi

You can still use wine without the symlinks.

You remove the symlinks using winecfg if I remember correctly.

You would only need to remove the dosdevices symlinks.

You should be alright keeping the symlinks to documents, pictures, videos etc as long as there is not a huge number of files in them.

You will still be able to use the windows program you use in wine in Lubuntu :)

EDIT: or you can delete the symlinks from the command line of course.

Kind regards

---

### Post by AbleTassie on 2014-11-18
> **matt_symes said:**
> Hi

You can still use wine without the symlinks.

You remove the symlinks using winecfg if I remember correctly.

You would only need to remove the dosdevices symlinks.

You should be alright keeping the symlinks to documents, pictures, videos etc as long as there is not a huge number of files in them.

You will still be able to use the windows program you use in wine in Lubuntu :)

EDIT: or you can delete the symlinks from the command line of course.

Kind regards

Thanks Matt, 

QUESTION: if I remove the symlinks as you are saying, what effect would that have on using the program that requires WINE? The page at [https://www.winehq.org/site/docs/wineusr-guide/config-wine-main](https://www.winehq.org/site/docs/wineusr-guide/config-wine-main) seems relevant to what you are saying. An excerpt from that page is below. 

Thanks, R.

**4.1.4. Drive Settings**

            Windows requires a fairly rigid drive configuration that Wine             imitates.  Most people are familiar with the standard notation             of the A: drive representing the floppy disk,             the C:             drive representing the primary system disk, etc.   Wine uses             the same concept and maps those drives to the underlying native             filesystem.           
            Wine drive configuration is relatively simple.             In **winecfg under the Drives tab you'll             see buttons to add and remove available drives.             When you choose to add a drive, a new entry will be made             and a default drive mapping will appear.  You can change where             this drive points to by changing what's in the             Path: box.  If you're unsure of the             exact path you can choose Browse to search for it.             Removing a drive is as easy as selecting the drive and             clicking Remove.            **
**            [B]winecfg has the ability to automatically detect the drives             available on your system.  It's recommended you try this             before attempting to configure drives manually.  Simply             click on the Autodetect button to             have Wine search for drives on your system.            **[/B]
**[B]            You may be interested in configuring your drive settings             outside of [B]winecfg, in which case you're in luck because it's             quite easy.  All of the drive settings reside in a special             directory: ~/.wine/dosdevices.  Each             "drive" is simply a link to where it actually resides.  Wine automatically             sets up two drives the first time you run Wine:            **[/B][/B]
[B][B][B]$ ls -la ~/.wine/dosdevices/
lrwxrwxrwx  1 *wineuser* *wineuser*   10 Jul 23 15:12 c: -> ../drive_c
lrwxrwxrwx  1 *wineuser* *wineuser*    1 Jul 23 15:12 z: -> /[/B][/B][/B]**[B][B]             To add another drive, for example your CD-ROM, just create a new              link pointing to it:            **[/B][/B]
**[B][B]$ ln -s /mnt/cdrom ~/.wine/dosdevices/d:**[/B][/B]**[B][B]             Take note of the DOS-style naming convention used for links -              the format is a letter followed by a colon, such as a:.  So,              if the link to your c: drive points to              ~/.wine/drive_c, you              can interpret references to c:\windows\system32              to mean ~/.wine/drive_c/windows/system32.       **[/B][/B]

---

### Post by matt_symes on 2014-11-18
Hi

> QUESTION: if I remove the symlinks as you are saying, what effect would that have on using the program that requires WINE?

Basically it will restrict where the program running under wine can access.

Most programs running under wine don't need access to the root partition of your hard drive. 
Many also don't need access to any external drives you may have.
Many can get away without access to the pseudo c drive as well.

You can also add the symlinks back easily enough using winecfg if you get into issues especially as it's only one windows application you use under wine.

I don't know what the program you are running under wine is, so it's hard to be more precise.

Kind regards

---

### Post by AbleTassie on 2014-11-18
> **matt_symes said:**
> Hi



Basically it will restrict where the program running under wine can access.

Most programs running under wine don't need access to the root partition of your hard drive. 
Many also don't need access to any external drives you may have.
Many can get away without access to the pseudo c drive as well.

You can also add the symlinks back easily enough using winecfg if you get into issues especially as it's only one windows application you use under wine.

I don't know what the program you are running under wine is, so it's hard to be more precise.

Kind regards

Thanks Matt, 

I occasionally use the Windows version of Foxit pdf reader with WINE to edit pdf documents. So it appears that if I delete the symlinks to various drives, Foxit Reader/WINE might be unable to find the drives. So perhaps the use of Foxit Reader might be restricted. For example, maybe I could not open a document by right clicking the document and asking that the document be opened using the Reader. Perhaps I'd have to use the open function in the Reader to open the document, or vice versa.

QUESTION: Any comments?

Thanks,

R.

---

### Post by vasa1 on 2014-11-18
> **RMcGinnis said:**
> ...
QUESTION: Any comments?
...
I'd just add that your options to "find" are relatively limited when you use the file manager. If you don't mind using the terminal you can set up all sorts of conditions to give your find command focus. And you can have several different find commands, assign aliases to them and then just have to type in a couple of keys to get your work done. For example, I have an alias called 5m which tells me what's changed in the last five minutes (and excludes certain folders such as caches):```
alias 5m='find ~/ ! -path "*mozilla*" ! -path "*google-chrome*" ! -path "*cache*" ! -path "*dropbox*" -mmin -5 -type f -ls'
```

---

### Post by matt_symes on 2014-11-19
Hi

> **RMcGinnis said:**
> Thanks Matt, 

I occasionally use the Windows version of Foxit pdf reader with WINE to edit pdf documents. So it appears that if I delete the symlinks to various drives, Foxit Reader/WINE might be unable to find the drives. So perhaps the use of Foxit Reader might be restricted. For example, maybe I could not open a document by right clicking the document and asking that the document be opened using the Reader. Perhaps I'd have to use the open function in the Reader to open the document, or vice versa.

QUESTION: Any comments?

Thanks,

R.

It's been a very long time since I have used wine so I will place a ceavet that I am remembering correctly.

If you start Foxit pro as a stand alone app you'll be able to "open/save dialog" to the places that are symlinked. The documents/my documents folder would be the most useful for you here.

If you right click on a pdf and open it in wine, it should open and you should be able to save it by selecting the save option. Selecting the save as option will limit you to locations that are symlinked in wine.

If anybody else knows different then please speak up. If the above is wrong then I apologise.

Anyway, what you can do is remove the symlinks one by one and test the behaviour in between. That won't take too long. They are easy to reenter.

kind regards

---

### Post by AbleTassie on 2014-11-19
OK Matt, I will attempt tp give this a try and let you know the results. But it may take a few days to a week given my time constraints.

Thanks again Matt and others: Sudodus, Vasa, Bapoumba.

R.[**[COLOR=#990303][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805")

---

### Post by vasa1 on 2014-11-19
Somewhat off the main point, but what sort of editing of pdf files do you do? Is that the only reason you need Wine?

---

### Post by AbleTassie on 2014-11-21
> **vasa1 said:**
> Somewhat off the main point, but what sort of editing of pdf files do you do? Is that the only reason you need Wine?

Vasa,

I think it is the only reason I use WINE. I highlight text, add page numbers, add textboxes and commentary. I do not think the Linux version of Foxit Reader works very well, but the Windows version does. I looked into all of this several months ago and came to the conclusion this was really my only option for editing pdf documents. I don't have enough RAM to Virtualbox Windows.

Thanks,

R.

---

### Post by sudodus on 2014-11-21
Did you try ***xournal***? (You find it in the repositories)

```
sudo apt-get install xournal
```

---

### Post by AbleTassie on 2014-11-21
> **matt_symes said:**
> Hi

You can still use wine without the symlinks.

You remove the symlinks using winecfg if I remember correctly.

You would only need to remove the dosdevices symlinks.

You should be alright keeping the symlinks to documents, pictures, videos etc as long as there is not a huge number of files in them.

You will still be able to use the windows program you use in wine in Lubuntu :)

EDIT: or you can delete the symlinks from the command line of course.

Kind regards

Matt and others,

I am not sure how to remove symlinks. Under WINE in Lubuntu there is a vertical menu that includes "Confiure Wine" and in Configure Wine there is a Drives tab. It is easy to remove drives, but the C drive cannot be removed and the path to the C drive does not appear to be changeable either. I removed all drives except for C and the Find Files tool still runs a very long time in the home folder. 

There is a quote beneath my name below from under "4.1.4. Drive Settings" on the page at this link [https://www.winehq.org/site/docs/wineusr-guide/config-wine-main](https://www.winehq.org/site/docs/wineusr-guide/config-wine-main)  that MAY be relevant. 

QUESTION: Any comments on how to remove symlinks?

Thanks,

R.[U]

Quote:[/U][I][B][I] 

"You may be interested in configuring your drive settings             outside of **winecfg,  in which case you're in luck because it's             quite easy.  All  of the drive settings reside in a special             directory:  ~/.wine/dosdevices.  Each             "drive" is simply a link to where  it actually resides.  Wine automatically             sets up two drives  the first time you run Wine:            **
[/I]
[I][B]$ ls -la ~/.wine/dosdevices/
lrwxrwxrwx  1 wineuser wineuser   10 Jul 23 15:12 c: -> ../drive_c
lrwxrwxrwx  1 wineuser wineuser    1 Jul 23 15:12 z: -> /"
 [/B][/I] [/B][/I]

---

### Post by vasa1 on 2014-11-21
> **RMcGinnis said:**
> Vasa,

I think it is the only reason I use WINE. I highlight text, add page numbers, add textboxes and commentary. ...
I forgot to ask ... do you then have to pass these pdf files to anyone else? I'm asking because at least highlighting or annotation seem to be dependent on the pdf reader/editor. Doing something successfully with one Linux pdf reader/editor may not mean that all what you've done can be passed around to people who may use other readers.

---

### Post by AbleTassie on 2014-11-21
> **sudodus said:**
> Did you try ***xournal***? (You find it in the repositories)

```
sudo apt-get install xournal
```

Thanks Sudodus, 

I'll try it.

R.

---

### Post by AbleTassie on 2014-11-21
> **vasa1 said:**
> I forgot to ask ... do you then have to pass these pdf files to anyone else? I'm asking because at least highlighting or annotation seem to be dependent on the pdf reader/editor. Doing something successfully with one Linux pdf reader/editor may not mean that all what you've done can be passed around to people who may use other readers.

Vasa,

There is some difference in highlighting when reading with my own pdf Evince Document Viewer: the side edges of the highlighting bulges out. But this does not appear to happen when the documents are submitted and appear online. I don't think there are any other differences I know of.

Thanks,

R.

---

### Post by AbleTassie on 2014-11-22
> **sudodus said:**
> Did you try ***xournal***? (You find it in the repositories)

```
sudo apt-get install xournal
```

Thanks Sudodus. I tried xournal. it is OK, but based on trying it briefly, I am pretty confident that it really is not as good or versatile or powerful as Foxit Reader. I wish it was, it would have been a pleasent surprise if it was. On the other hand it can do some highlighting and has a typewriter type function.

Thanks,

R.

---

### Post by AbleTassie on 2014-11-24
> **matt_symes said:**
> Hi



It's been a very long time since I have used wine so I will place a ceavet that I am remembering correctly.

If you start Foxit pro as a stand alone app you'll be able to "open/save dialog" to the places that are symlinked. The documents/my documents folder would be the most useful for you here.

If you right click on a pdf and open it in wine, it should open and you should be able to save it by selecting the save option. Selecting the save as option will limit you to locations that are symlinked in wine.

If anybody else knows different then please speak up. If the above is wrong then I apologise.

[B]Anyway, what you can do is remove the symlinks one by one and test the behaviour in between. That won't take too long. They are easy to reenter.
[/B]
kind regards

Matt or others,

How do I remove a symlink in WINE? I am not sure how to do this.

Thanks,

R.

---

### Post by matt_symes on 2014-11-27
Hi

You should be able to use winecfg to delete the symlinks. You may have to install it.

Kind regards

---

### Post by AbleTassie on 2014-12-01
> **matt_symes said:**
> Hi

You should be able to use winecfg to delete the symlinks. You may have to install it.

Kind regards

Thanks Matt. I already have Winecfg, but I have no idea how to remove symlinks using Winecfg or not using Winecfg. This WINE link [https://www.winehq.org/site/docs/wineusr-guide/config-wine-main](https://www.winehq.org/site/docs/wineusr-guide/config-wine-main)   has instructions for configuring WINE. But it is not clear to me from looking at this page how to remove a symlink.

Any more comments from you or anybody else about how to remove a symlink are welcome.

Thanks,

R.

---

