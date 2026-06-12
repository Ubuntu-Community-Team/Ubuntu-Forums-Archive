---
title: "[SOLVED] hidden files &amp;amp; how to create, delete and control them"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-20
I have to copy the contents of .dmrc to some file not named .dmrc. Then I have to delete the file named:.dmrc. Then I have to recreate the file named .dmrc and put the contents back in it.

Then the .dmrc must be:

sudo chmod 700 /home/mark
sudo chmod 644 /home/.dmrc

How do I create and save a hidden or -dot- or '.' file?

---

### Post by Elfy on 2008-10-20
To move file 
```
mv .dmrc nameoffile
```

To read old file from a terminal
```
nano nameoffile
```

Shift+Ctrl+T will open a new tab in the terminal to open file for editing

To edit file
```
nano .dmrc
```

Make sure you are in your home before you start

---

### Post by H.Callahan on 2008-10-20
Assuming that you want just a ASCII file, you could:

```
nano .dmrc
```

Then enter whatever you want to put in it; hit Control-O to save (retaining the .dmrc file name) and the Control-X to exit.

If you want it to be another type of file, just open whatever application that you want and then save the file with the name .dmrc.

[edit: Ok, it looks like forestpixie beat me to it with a better explanation than mine.  I defer to him.]

---

### Post by Mark_in_Hollywood on 2008-10-20
> **forestpixie said:**
> In home from a terminal to make the 

```
 mkdir .nameoffile
```

why do I need to make a directory for this? I want to put this on /home/mark/Desktop

mark is my username.

I don't want to copy or move the file. I want to copy the contents of the file, save the contents to a file (I'm using the filename: dmrc-contents) and create a file with the same name: .dmrc, with the contents "pasted" into it.

By the bye: when I try to copy the contents of .dmrc and make a file named: dmrc-contents and save it to my Desktop, it turns up as a "hidden" file, even though it has no hidden or dot in the filename. What gives here?

---

### Post by Elfy on 2008-10-20
You don't and it's gone now :)

The easiest way to copy the contents to a new file is to move it - the old one is then gone and then make the new file with nano and copy the contents to the new file

mv original
cat original
nano new

---

### Post by mister_pink on 2008-10-20
I don't quite understand why you would want to copy the contents then paste them again - its exactly the same as just copying the file. Perhaps you could get more useful advice if you let us know what the more direct issue is.

Also, hidden files act exactly like normal files except they start with a ".". To see them in nautilus, press ctrl+H and then you can open them normally in your text editor by just clicking them.

---

### Post by Mark_in_Hollywood on 2008-10-20
> **mister_pink said:**
> I don't quite understand why you would want to copy the contents then paste them again - its exactly the same as just copying the file. Perhaps you could get more useful advice if you let us know what the more direct issue is.

Also, hidden files act exactly like normal files except they start with a ".". To see them in nautilus, press ctrl+H and then you can open them normally in your text editor by just clicking them.

When I power up the 'puter I get an error message about a file named: home/mark/.dmrc

This happened because I plugged a used drive (with XP) into the 'puter via a usb port (external drive usb 2.0). Once I did this, the drive could not be mounted. I d/l'd GParted and formatted the drive Pri. Part. ext3 for the whole disk.

When I rebooted I got the .dmrc file permssions fiasco and 2 thumb drive and the 80 gig usb drive now say "permissions cannot be determined" AND I cannot write to, copy to or (more or less use) the 'new' 80 gig drive. Some years ago, I had the same .dmrc problem (same use of external usb drive), so, going back to my post, I saw a post where the .dmrc had been solved by

copying the contents of the file
deleting the file
re-creating the file
and the chmod and chown stuff

I hope that in fills the confusion I've caused. I thought I was keeping it simple.

Do I need to be "root" to use nano and copy hidden files?

---

### Post by jerome1232 on 2008-10-20
Well here goes, really the cat isn't any diffrent then just copying the file... but it's technically copying the contents of the file rather than copying the file.

```
cat .dmrc > .dmrc.bck
rm .dmrc
cp .dmrc.bck .dmrc
#since there's no point to chmoding a file twice
chmod 644 .dmrc
```

---

### Post by Elfy on 2008-10-20
I had to 

```
sudo chmod 644 /home/username/.dmrc
sudo chown ricardisimo /home/username/.dmrc
sudo chmod -R 700 /home/username
sudo chown -R ricardisimo /username/ricardisimo
```

Incidentally I believe my problem came about before I realised I needed to use gksudo for gui apps and not to use sudo with them

---

### Post by Mark_in_Hollywood on 2008-10-20
> **forestpixie said:**
> I had to 

```
sudo chmod 644 /home/username/.dmrc
sudo chown ricardisimo /home/username/.dmrc
sudo chmod -R 700 /home/username
sudo chown -R ricardisimo /username/ricardisimo
```

Incidentally I believe my problem came about before I realised I needed to use gksudo for gui apps and not to use sudo with them


For me, it worked as far as:

mark@Lexington-19:/$ sudo chmod -R 700 /home/mark
chmod: cannot access `/home/mark/.gvfs': Permission denied

---

### Post by Mark_in_Hollywood on 2008-10-20
> **jerome1232 said:**
> Well here goes, really the cat isn't any diffrent then just copying the file... but it's technically copying the contents of the file rather than copying the file.

```
cat .dmrc > .dmrc.bck
rm .dmrc
cp .dmrc.bck .dmrc
#since there's no point to chmoding a file twice
chmod 644 .dmrc
```

**This worked!!!**

Thanks, community

---

