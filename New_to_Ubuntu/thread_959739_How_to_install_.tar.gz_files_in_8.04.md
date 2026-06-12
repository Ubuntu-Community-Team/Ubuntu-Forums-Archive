---
title: "How to install .tar.gz files in 8.04"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by fslezak on 2008-10-26
I have this .tar.gz application that i need help installing.
Can someone help me?

---

### Post by redseventyseven on 2008-10-26
I think we'll need some more info! What package is it? What are the contents of the tar.gz file?

---

### Post by igknighted on 2008-10-26
> **fslezak said:**
> I have this .tar.gz application that i need help installing.
Can someone help me?

.tar.gz is (essentially) a .zip in windows.  You need to extract it (right click the file, extract here).  There should then be a readme file inside somewhere with directions on how to install.  Every one is different, so refer to the readme, or if you have specific questions with the readme (or there is none) post back with specifics on the application in question.

---

### Post by lazylew on 2008-12-08
> **igknighted said:**
> ...extract it (right click the file, extract here).  There should then be a readme file inside somewhere with directions on how to install.  Every one is different, so refer to the readme, or if you have specific questions with the readme (or there is none) post back with specifics on the application in question.
I have the same problem - not knowing how to work with the tar.gz
I downloaded a music player from [http://getsongbird.com/](http://getsongbird.com/) and extracted the files into a folder in my home 
The read me file talks about new features and developer links, but there's no explanation on how to proceed after installing. 
The Songbird-player doesn't appear in the Applications menu and right click on an mp3-file doesn't show the option of opening with songbird.

---

### Post by goferrr on 2008-12-08
If ~/Sogbird is a direcory where you extracted the archive songbirg.tar.gz
```
sh ~/Songbird/songbird
```
should work just fine.

Afterwards you may consider adding a Application launcher to your Gnome Panel. Path:
 ```
~/Songbird/songbird
```
Proper icon is in Songbird direcory.

---

### Post by theozzlives on 2008-12-08
I have songbird on my system and it came in a *.deb file

---

### Post by cdmike2k8 on 2008-12-08
In response to lazylew, songbird doesn't need to be installed AFAIK.  You just need to run the file songbird in the extracted folder.  I moved the entire directory to my home folder and renamed it to .songbird so that it would be hidden.  Then added a link to the file in applications menu.  If you need more help, start a new thread.

---

### Post by Farmer of Bricks on 2008-12-08
Look at [this wiki]("https://help.ubuntu.com/community/CompilingEasyHowTo"). It covers most of the basics. 
Check if your program is in the repos. If not, then:
 
1: Install build-essential and checkinstall:
```
user@prompt: sudo apt-get install build-essential checkinstall
```
2: Unzip the tarball:
```
user@prompt: tar xzvf tarballname.tar.gz
```
3: Make the program:
```
user@prompt: make
```
4: Run checkinstall to make the program show up in your ackage manager:
```
user@prompt: checkinstall
```

---

### Post by lazylew on 2008-12-08
> **cdmike2k8 said:**
> In response to lazylew, songbird doesn't need to be installed AFAIK.  You just need to run the file songbird in the extracted folder.  I moved the entire directory to my home folder and renamed it to .songbird so that it would be hidden.  Then added a link to the file in applications menu.  If you need more help, start a new thread.
I haven't found out how to reply and still have all other posts open to copy/paste for quotes from those multiple posts, so here goes improvisation ;-)

> goferr: If ~/Songbird is a direcory where you extracted the archive songbird.tar.gz
     Code:
     sh ~/Songbird/songbird  yes! that works to get the player started :-)
Still I don't see it appear in Applications and it goes away as soon as I close terminal.

> theozzlives: *.deb file  I just know about the "download" at [http://getsongbird.com/](http://getsongbird.com/)

To cdmike2k8: ok I'll post a new thread and link to here.

Edit: *seeing farmer of bricks post I'll postpone the new thread till I sort our the wiki and see if I understand 					 				*

---

### Post by goferrr on 2008-12-08
> **lazylew said:**
> 
Still I don't see it appear in Applications and it goes away as soon as I close terminal.

.

> Afterwards you may consider adding a Application launcher to your Gnome Panel. Path:
Code:

~/Songbird/songbird

Proper icon is in Songbird direcory. 
It won't appear in Applications unless you add it. Simply edit your Menu(right click - Edit Menus) and add a launcher just like I described above.
EDIT: 
I just need to add that Farmer of Bricks' post is irrevelant in this case, because Songbird does not need compiling or installing. You just launch it in a windows fashion;)

---

### Post by lazylew on 2008-12-08
> **goferrr said:**
> It won't appear in Applications unless you add it. Simply edit your Menu(right click - Edit Menus) and add a launcher just like I described above....

ok I'm almost there; even got to add the proper icon but it just won't appear in the menu despite dragging it to Sound and marking it with "v" (don't know what the term in english is)

---

### Post by Patrick793 on 2008-12-08
For the guys wanting Songbird as a .deb, go [here](http://www.getdeb.net/app/Songbird).

---

### Post by lazylew on 2008-12-12
I deleted everything I had put in the home folder after reading Songbird doesn't have to be there.
I went via this site [http://unter-hund.com](http://unter-hund.com) and got Songbird working in no time.

I know it's off-topic, but my first impressions of Songbird are beyond expectation.
This is indeed a media player that will be very popular :-)

Thanks again all for your help here!

---

