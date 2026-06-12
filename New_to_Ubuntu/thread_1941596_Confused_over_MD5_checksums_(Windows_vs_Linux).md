---
title: "Confused over MD5 checksums (Windows vs Linux)"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by FulciLives on 2012-03-15
I'm confused about the whole MD5 checksum thing.

Allow me to explain what it is I am confused about.

I have MD5 text files that I've created in Windows and now that I'm using Linux (in this case Ubuntu 12.04 Beta 1) I am finding that I cannot check them without being told that there is a formatting error.

So I use md5sum (in terminal) to create a new MD5 file. When I compare it to the other MD5 file (that was made in Windows) I see that the numbers (the MD5 checksums) match up and that the formatting is ALMOST the same but not exact. I'll give you an example.

Say I have a folder with two files in it. We'll call them filename01.mkv and filename02.jpg for this example. The MD5 file made in Windows looks like Example A below and the MD5 file made in Linux looks like Example B below:

```
Example A - Windows MD5
253343b4d39e9e8b337a7db300d5e7dd *filename01.mkv
cd103030ad0dd35ecf0af1d6cc327417 *filename02.jpg

Example B - Linux MD5
253343b4d39e9e8b337a7db300d5e7dd  filename01.mkv
cd103030ad0dd35ecf0af1d6cc327417  filename02.jpg
```

As you can see the two are almost exactly the same other than the ASTERISK in front of the file names (in the Windows created MD5 file). The Linux created MD5 file doesn't have the ASTERISKS. Instead there is a space where the ASTERISK would be.

So as I said when I try to use md5sum in Linux to check a MD5 made in Windows I'm given an error (wrong formatting). When I try to check a MD5 made in Linux using Windows I also get an error (again due to the difference in formatting).

Is there a way around this formatting difference? Right now the only solution I see is to manually edit the MD5 file to remove all the of the ASTERISKS (since most of my MD5 files are Windows created and yet I'm now trying to convert myself full time to Linux via Ubuntu which means I need to check these Windows created MD5 files in Linux).

All help appreciated! :)

---

### Post by jerome1232 on 2012-03-16
Based on this [http://thestarman.narod.ru/DOS/MD5progs.html](http://thestarman.narod.ru/DOS/MD5progs.html)

it shouldn't really matter, using the asterisk is supposdly an archaic way to format md5sum files, on my system md5sum doesn't complain abou asterisks being there. Perhaps you simply need a more up-to-date program for your md5suming in windows?

---

### Post by FulciLives on 2012-03-16
Been playing with this more since I posted the above and now I'm even more confused LOL

As I said in the post above I can't seem to use the Linux 'md5sum' terminal command to check the MD5 files made in MS Windows without getting an error. I pointed out the difference in formatting between my MS Windows made MD5 files and the MD5 files that I create under Linux (again using Ubuntu 12.04 Beta 1 right now).

Well here is how I've been making my Linux MD5 files:
md5sum *.* > md5.txt

However I was reading about the -b binary option so I tried this:
md5sum *.* -b > md5.txt

The MD5 without the -b option looks like my "Example B" in the above post. However the MD5 using the -b option looks like my "Example A" in the above post.

In other words if I create a MD5 in Linux with the md5sum -b option then it looks EXACTLY like the MD5 made in Windows.

Now as you can imagine I can use md5sum to verify the Linux made MD5 and it works regardless of how the MD5 was made (be it with the -b option or without). That makes sense but what doesn't make sense is that the Windows made MD5 (which looks EXACTLY like the Linux made MD5 with the -b option) gives me an error when trying to verify with md5sum. What the hell?

And if that isn't confusing enough ... check this out:
I went back into MS Windows and from there I can successfully use the Linux made MD5 (the one made with the -b option) and it works.

I hope this isn't confusing. Again to be clear: The Windows made MD5 has the ASTERISKS but md5sum in Linux gives me errors when I try to check it (I get no such errors checking the same Windows made MD5 in Windows). However when I make a MD5 in Linux using the -b command I get the ASTERISKS and as far as I can tell it looks EXACTLY like the Windows made MD5 and md5sum will successfully check it (and the same file even works in Windows).

So why can't md5sum check the Windows made MD5 files?

I don't understand what the problem is here <<< rips out hair >>>

*** EDIT ***
I just wanted to add that on MS Windows I use a program called "Trader's Little Helper" in order to make and verify MD5 checksum files. I use this program because it was the only simple MD5 GUI type program I could find that seemed to work (again the MD5 files never gave me trouble in MS Windows and I even tried using another different MD5 GUI program on Windows to double check the MD5's made with Trader's Little Helper and it had no problems either with the files. I stopped using that other program though because it was old and would crash a lot ... it was made back when WinXP was current and never updated ... whereas Trader's Little Helper was updated as recently as 2011)

---

### Post by jerome1232 on 2012-03-16
I wonder if it's the line endings, Windows uses diferent line endings than Unix like OS's.

If you install the program dos2unix, and run it with the -b option, it will convert your file to unix line endings and make a backup of the original. Check it's man page for more info. ie

```
dos2unix -b /pita/md5file
```

Again, just taking stabs in the dark.

---

### Post by FulciLives on 2012-03-16
> **jerome1232 said:**
> I wonder if it's the line endings, Windows uses diferent line endings than Unix like OS's.

If you install the program dos2unix, and run it with the -b option, it will convert your file to unix line endings and make a backup of the original. Check it's man page for more info. ie

```
dos2unix -b /pita/md5file
```

Again, just taking stabs in the dark.
Interesting.

I didn't actually try this (what you suggested) but it gave me an idea ...

I opened the Windows made MD5 with a text editor (while in Ubuntu) and copied it and pasted it into a new txt file. Just a simple COPY & PASTE is all. Guess what? The new file works now with md5sum. Son of a bitch, huh?

Apparently it is some sort of Windows vs Linux file/text formatting issue.

Please note that after I tried this (and saw that it worked) I decided if maybe I couldn't make it even simpler. So I tried to open the Windows made MD5 in Ubuntu with a text editor and then simply use the "SAVE AS" feature to save it again (under the same name). Unfortunately that didn't work. It seems I need to COPY AND PASTE it into a new Linux made txt document for it to work.

---

### Post by jerome1232 on 2012-03-16
What text editor are you using for Linux, Gedit has an option to specify your line endings, (hit save as and change the line endings lower right corner) and for Windows I believe Notepad+ (or is it notepad++? can't remember but it's a great text editor) has the option to specify your line endings as well.

---

### Post by FulciLives on 2012-03-16
> **jerome1232 said:**
> What text editor are you using for Linux, Gedit has an option to specify your line endings, (hit save as and change the line endings lower right corner) and for Windows I believe Notepad+ (or is it notepad++? can't remember but it's a great text editor) has the option to specify your line endings as well.
I could kiss you LOL

When I right click on my MD5 files I get an option to open into a text editor and I guess by default Ubuntu uses gedit. So yes I tried what you said and it works.

So basically I just have to open the file into gedit (very easy to do via the GUI) and hit SAVE AS and change the "Line Ending" to "Unix/Linux" and that does the trick!

Jeez what a pain in the *** that was but THANK YOU for helping me to figure it all out.

I greatly appreciate it! :)

HOWEVER there is still one more issue I need to tackle in regards to all this (ha ha and you thought this was finally solved).

Some of my Windows made MD5 checksum files have sub folders in them.

For instance I have a lot of music files. Every album is in its own folder (or dir). All the files for that album are in that folder but then I have a folder in that folder called "Artwork" that has the CD scans.

The MD5 file is located in the ALBUM folder but also references the files in the ARTWORK sub folder.

Here is an actual MD5 file to show you exactly what I mean:

```
210af50eaf926e6b7b20bbff14435437 *00. Manfred Hubler & Sigfried Schwab - 3 Films by Jess Franco.m3u
17e2157b86c1414e897189eb10150c19 *01. The Lions and the Cucumber.flac
3bf44f702be425b0b211a56c8fb6a08a *02. Psycho Contact - Part One.flac
e4cb3cce799aea2f3c8ac303497de378 *03. There is No Satisfaction.flac
b05c05a5c0f6eecc521097b714b2bb1b *04. Psycho Contract - Part Two.flac
c0380de9cdc70a00e7b14b5aa9ffe551 *05. The Message.flac
4a41ca7499e6c5933d6b25c2c32c5361 *06. Psycho Contract - Part Three.flac
a655eb87af3fed10493c411f261c7710 *07. Ghost or Good and Bad Onions.flac
a1ba312bb9c3adb7778bb8ad700ee261 *08. Psycho Contract - Part Four.flac
311ba7cb146f829a9ad0ab2d0a372878 *09. Countdown to Nowhere.flac
a41726f960c83228bfde81cf6e230c97 *10. Psycho Contract - Part 5.flac
2be7f5d2490b4cfdbb4209d21fa52fc8 *11. Droge CX 9.flac
7117d5f6729f7b870ffec4598ebe8f18 *12. Dedicated to Love.flac
786735d660c44af213a15ad76112a5b3 *13. People's Playground Version A.flac
e64e4729e34e0d321b3c6ddcb0779233 *14. We Dong Care.flac
749ef42462c0dc7943742c6ac6e9ec08 *15. People's Playground Version B.flac
f6fb69cfd4ce1b51c6544630a9e51dd2 *16. The Ballad of a Fair Singer.flac
73a21858a2b7ccb1a02dd66129935c0c *17. Peoples Plaground Version C.flac
b8d740fc9e17424a4c32d7755704a952 *18. Necronomania.flac
e1c5acce5377f3d4fd397335bde5fb50 *19. Kama Sutra.flac
e031b7e1a5fd1913717fec91031a120c *20. People's Playground Version D.flac
28a188dbd6d9de413a2d4ae6a510d4c3 *21. Shindai Lovers.flac
b4ecd964390ac0c7864f17fcbd532346 *22. Konkubination.flac
90efc07a5905e50dc848f046c6f2e21a *23. People's Playground Version E.flac
e4cbdbd14b76d6ece5b79305df700494 *24. The Six Wisdoms of Aspasia.flac
75293a26165c2351474fc0e13e523747 *CUE Sheet File - 3 Films by Jess Franco (flac).cue
66ed65564b21fdaf805816572c8cefd4 *CUE Sheet File - 3 Films by Jess Franco (wav).cue
55db3167f43399418a1e9c189cfea9cd *CUETools LOG File - 3 Films by Jess Franco.accurip
f21a19ff4ce11e78b6a8aac66dc212dd *EAC LOG File - 3 Films by Jess Franco.log
c77962db9d5df2286fe83b3de39c6b9d *folder.jpg
c77962db9d5df2286fe83b3de39c6b9d *Artwork\3 Films by Jess Franco - folder image.jpg
b18cc3be93c94d4f1880e440e8381d65 *Artwork\3 Films by Jess Franco back booklet Large.jpg
f4cf0a0ff8fb82a54066ca647e3f6d45 *Artwork\3 Films by Jess Franco back cvr.jpg
4c3c4070e261e77d57cbf0e6ee3a2c4f *Artwork\3 Films by Jess Franco book 1.jpg
e796f318f2672487463f5bb56eed82d2 *Artwork\3 Films by Jess Franco book 2.jpg
5ffdc9d961345d3acd88697e03c7bd60 *Artwork\3 Films by Jess Franco book 3.jpg
a28b5e74bc382e5a730ab2f0d6e4580e *Artwork\3 Films by Jess Franco book 4.jpg
f24972555be578d4dca5a211822ae360 *Artwork\3 Films by Jess Franco front cvr Large.jpg
c072c5de4ab54b811048a4ac34cdf0e5 *Artwork\CD Info.jpg
```
Now when I use md5sum to check this it checks all of the files except for those in the ARTWORK sub directory. It simply says that it cannot find them or that they are missing or some such thing.

Currently I'm using the following Terminal command: md5sum -c checksum.md5
Note "checksum.md5" is the name of the txt file with the MD5 checksum totals (as seen in the example above for the Jess Franco CD)

So is there some way to check those files in the sub directory using md5sum?

I did try to google this and I came up with something called "md5deep" which is like md5sum except it can also check sub directories. Here is a link to it: [CLICK HERE](http://md5deep.sourceforge.net/)

Now I was able to install this "md5deep" but despite the examples given on that website I can't figure out how to use it. The examples seem to be geared more towards creation of MD5 files rather than checking existing MD5 files. I find all this command line syntax confusing without examples for my exact situation. Help please?

---

### Post by jerome1232 on 2012-03-16
> **FulciLives said:**
> 
So basically I just have to open the file into gedit (very easy to do via the GUI) and hit SAVE AS and change the "Line Ending" to "Unix/Linux" and that does the trick!

Kind of why I mentioned dos2unix, you could batch convert every .txt file in a folder as easily as

```
dos2unix *.txt
```


> **FulciLives said:**
> 
```
210af50eaf926e6b7b20bbff14435437 *00. Manfred Hubler & Sigfried Schwab - 3 Films by Jess Franco.m3u
17e2157b86c1414e897189eb10150c19 *01. The Lions and the Cucumber.flac
3bf44f702be425b0b211a56c8fb6a08a *02. Psycho Contact - Part One.flac
e4cb3cce799aea2f3c8ac303497de378 *03. There is No Satisfaction.flac
b05c05a5c0f6eecc521097b714b2bb1b *04. Psycho Contract - Part Two.flac
c0380de9cdc70a00e7b14b5aa9ffe551 *05. The Message.flac
4a41ca7499e6c5933d6b25c2c32c5361 *06. Psycho Contract - Part Three.flac
a655eb87af3fed10493c411f261c7710 *07. Ghost or Good and Bad Onions.flac
a1ba312bb9c3adb7778bb8ad700ee261 *08. Psycho Contract - Part Four.flac
311ba7cb146f829a9ad0ab2d0a372878 *09. Countdown to Nowhere.flac
a41726f960c83228bfde81cf6e230c97 *10. Psycho Contract - Part 5.flac
2be7f5d2490b4cfdbb4209d21fa52fc8 *11. Droge CX 9.flac
7117d5f6729f7b870ffec4598ebe8f18 *12. Dedicated to Love.flac
786735d660c44af213a15ad76112a5b3 *13. People's Playground Version A.flac
e64e4729e34e0d321b3c6ddcb0779233 *14. We Dong Care.flac
749ef42462c0dc7943742c6ac6e9ec08 *15. People's Playground Version B.flac
f6fb69cfd4ce1b51c6544630a9e51dd2 *16. The Ballad of a Fair Singer.flac
73a21858a2b7ccb1a02dd66129935c0c *17. Peoples Plaground Version C.flac
b8d740fc9e17424a4c32d7755704a952 *18. Necronomania.flac
e1c5acce5377f3d4fd397335bde5fb50 *19. Kama Sutra.flac
e031b7e1a5fd1913717fec91031a120c *20. People's Playground Version D.flac
28a188dbd6d9de413a2d4ae6a510d4c3 *21. Shindai Lovers.flac
b4ecd964390ac0c7864f17fcbd532346 *22. Konkubination.flac
90efc07a5905e50dc848f046c6f2e21a *23. People's Playground Version E.flac
e4cbdbd14b76d6ece5b79305df700494 *24. The Six Wisdoms of Aspasia.flac
75293a26165c2351474fc0e13e523747 *CUE Sheet File - 3 Films by Jess Franco (flac).cue
66ed65564b21fdaf805816572c8cefd4 *CUE Sheet File - 3 Films by Jess Franco (wav).cue
55db3167f43399418a1e9c189cfea9cd *CUETools LOG File - 3 Films by Jess Franco.accurip
f21a19ff4ce11e78b6a8aac66dc212dd *EAC LOG File - 3 Films by Jess Franco.log
c77962db9d5df2286fe83b3de39c6b9d *folder.jpg
c77962db9d5df2286fe83b3de39c6b9d *Artwork\3 Films by Jess Franco - folder image.jpg
b18cc3be93c94d4f1880e440e8381d65 *Artwork\3 Films by Jess Franco back booklet Large.jpg
f4cf0a0ff8fb82a54066ca647e3f6d45 *Artwork\3 Films by Jess Franco back cvr.jpg
4c3c4070e261e77d57cbf0e6ee3a2c4f *Artwork\3 Films by Jess Franco book 1.jpg
e796f318f2672487463f5bb56eed82d2 *Artwork\3 Films by Jess Franco book 2.jpg
5ffdc9d961345d3acd88697e03c7bd60 *Artwork\3 Films by Jess Franco book 3.jpg
a28b5e74bc382e5a730ab2f0d6e4580e *Artwork\3 Films by Jess Franco book 4.jpg
f24972555be578d4dca5a211822ae360 *Artwork\3 Films by Jess Franco front cvr Large.jpg
c072c5de4ab54b811048a4ac34cdf0e5 *Artwork\CD Info.jpg
```
Now when I use md5sum to check this it checks all of the files except for those in the ARTWORK sub directory. It simply says that it cannot find them or that they are missing or some such thing.

Currently I'm using the following Terminal command: md5sum -c checksum.md5
Note "checksum.md5" is the name of the txt file with the MD5 checksum totals (as seen in the example above for the Jess Franco CD)

So is there some way to check those files in the sub directory using md5sum?

I did try to google this and I came up with something called "md5deep" which is like md5sum except it can also check sub directories. Here is a link to it: [CLICK HERE](http://md5deep.sourceforge.net/)

Now I was able to install this "md5deep" but despite the examples given on that website I can't figure out how to use it. The examples seem to be geared more towards creation of MD5 files rather than checking existing MD5 files. I find all this command line syntax confusing without examples for my exact situation. Help please?

I'd have to look into it, I'll get back to you on it.

---

### Post by jerome1232 on 2012-03-16
Okay, take a look at md5deep man page.

```
man md5deep
```

Based on what it says (give it a read, it's got a lot of good info in there)

I would think on of these options is what you want

```
md5sum -k -m /path/to/md5file
###
### or
###
md5sum -k -M /path/to/md5file
###
### maybe it will need the -r option?
###
md5sum -rk -m /path/to/md5file
#### maybe this one?
md5sum -nk -m /path/to/md5file
```

Anyways just look at the man page and try various options out, read what they do, you have an understanding of what you want to see.

---

### Post by FulciLives on 2012-03-16
I assume jerome1232 that whenever you said "md5sum" in your last post that you actually meant "md5deep"

Anyway I tried your suggestions and some others and despite 'playing around' with it some I just can't figure it out.

Nothing seems to be working as it should with this "md5deep"

---

### Post by jerome1232 on 2012-03-16
hmmm I messed with it a bit, everything seems to work fine for me (I ended up using md5deep to make the list, md5sum to check)

Maybe I'll try it with some of your filenames that aren't working?

```
jeremy@jeremy-farewell:~$ md5deep -rk Desktop/ > md5file
jeremy@jeremy-farewell:~$ cat md5file 
ec5c5e3c033de26d9a41a86ba2282b4a */home/jeremy/Desktop/Scanned Document.jpg
d41d8cd98f00b204e9800998ecf8427e */home/jeremy/Desktop/test/file
d41d8cd98f00b204e9800998ecf8427e */home/jeremy/Desktop/test/file with a space
dd61551944e731fddb718aba1ab802e0 */home/jeremy/Desktop/loandocs.jpg
fe317ab7e61fc52aef81ac3e44416a55 */home/jeremy/Desktop/513846_Docs.PDF
jeremy@jeremy-farewell:~$ md5sum -c md5file 
/home/jeremy/Desktop/Scanned Document.jpg: OK
/home/jeremy/Desktop/test/file: OK
/home/jeremy/Desktop/test/file with a space: OK
/home/jeremy/Desktop/loandocs.jpg: OK
/home/jeremy/Desktop/513846_Docs.PDF: OK
jeremy@jeremy-farewell:~$ 
```

---

### Post by jerome1232 on 2012-03-16
I think I know what it is, your files are listed with a relative path, make sure your md5 file is inside the folder you want to run the check on, for example you want to check everything under ~/Music, copy the md5 file to your ~/Music folder then from the command line.

```
cd ~/Music
md5sum -c md5file
```

edit: I recreated that situation like this (me trying to demonstrate on the commandline what i'm talking about.

```
jeremy@jeremy-farewell:~/Desktop$ md5deep -rkl * > md5file
jeremy@jeremy-farewell:~/Desktop$ cat md5file
fe317ab7e61fc52aef81ac3e44416a55 *513846_Docs.PDF
dd61551944e731fddb718aba1ab802e0 *loandocs.jpg
ec5c5e3c033de26d9a41a86ba2282b4a *Scanned Document.jpg
d41d8cd98f00b204e9800998ecf8427e *test/file
d41d8cd98f00b204e9800998ecf8427e *test/file with a space
jeremy@jeremy-farewell:~/Desktop$ md5sum -c md5file 
513846_Docs.PDF: OK
loandocs.jpg: OK
Scanned Document.jpg: OK
test/file: OK
test/file with a space: OK
jeremy@jeremy-farewell:~/Desktop$ cp md5file ../
jeremy@jeremy-farewell:~/Desktop$ cd ../
jeremy@jeremy-farewell:~$ pwd
/home/jeremy
jeremy@jeremy-farewell:~$ md5sum -c md5file 
md5sum: 513846_Docs.PDF: No such file or directory
513846_Docs.PDF: FAILED open or read
md5sum: loandocs.jpg: No such file or directory
loandocs.jpg: FAILED open or read
md5sum: Scanned Document.jpg: No such file or directory
Scanned Document.jpg: FAILED open or read
md5sum: test/file: Not a directory
test/file: FAILED open or read
md5sum: test/file with a space: Not a directory
test/file with a space: FAILED open or read
md5sum: WARNING: 5 of 5 listed files could not be read
jeremy@jeremy-farewell:~$ cp md5file Desktop/
jeremy@jeremy-farewell:~$ cd Desktop/
jeremy@jeremy-farewell:~/Desktop$ md5sum -c md5file 
513846_Docs.PDF: OK
loandocs.jpg: OK
Scanned Document.jpg: OK
test/file: OK
test/file with a space: OK
jeremy@jeremy-farewell:~/Desktop$ 

```

---

### Post by FulciLives on 2012-03-16
Well I don't know how to do this other than to COPY AND PASTE what I did in Terminal.

Here goes:

```
fulcilives@fulcilives-CG5270:~/Music/Soundtracks - Film & TV/3 Films By Jess Franco - Manfred Hubler & Sigfried Schwab [FLAC]$ ls
00. Manfred Hubler & Sigfried Schwab - 3 Films by Jess Franco.m3u
01. The Lions and the Cucumber.flac
02. Psycho Contact - Part One.flac
03. There is No Satisfaction.flac
04. Psycho Contract - Part Two.flac
05. The Message.flac
06. Psycho Contract - Part Three.flac
07. Ghost or Good and Bad Onions.flac
08. Psycho Contract - Part Four.flac
09. Countdown to Nowhere.flac
10. Psycho Contract - Part 5.flac
11. Droge CX 9.flac
12. Dedicated to Love.flac
13. People's Playground Version A.flac
14. We Dong Care.flac
15. People's Playground Version B.flac
16. The Ballad of a Fair Singer.flac
17. Peoples Plaground Version C.flac
18. Necronomania.flac
19. Kama Sutra.flac
20. People's Playground Version D.flac
21. Shindai Lovers.flac
22. Konkubination.flac
23. People's Playground Version E.flac
24. The Six Wisdoms of Aspasia.flac
Artwork
checksum.md5
CUE Sheet File - 3 Films by Jess Franco (flac).cue
CUE Sheet File - 3 Films by Jess Franco (wav).cue
CUETools LOG File - 3 Films by Jess Franco.accurip
EAC LOG File - 3 Films by Jess Franco.log
folder.jpg
fulcilives@fulcilives-CG5270:~/Music/Soundtracks - Film & TV/3 Films By Jess Franco - Manfred Hubler & Sigfried Schwab [FLAC]$ md5sum -c checksum.md5
00. Manfred Hubler & Sigfried Schwab - 3 Films by Jess Franco.m3u: OK
01. The Lions and the Cucumber.flac: OK
02. Psycho Contact - Part One.flac: OK
03. There is No Satisfaction.flac: OK
04. Psycho Contract - Part Two.flac: OK
05. The Message.flac: OK
06. Psycho Contract - Part Three.flac: OK
07. Ghost or Good and Bad Onions.flac: OK
08. Psycho Contract - Part Four.flac: OK
09. Countdown to Nowhere.flac: OK
10. Psycho Contract - Part 5.flac: OK
11. Droge CX 9.flac: OK
12. Dedicated to Love.flac: OK
13. People's Playground Version A.flac: OK
14. We Dong Care.flac: OK
15. People's Playground Version B.flac: OK
16. The Ballad of a Fair Singer.flac: OK
17. Peoples Plaground Version C.flac: OK
18. Necronomania.flac: OK
19. Kama Sutra.flac: OK
20. People's Playground Version D.flac: OK
21. Shindai Lovers.flac: OK
22. Konkubination.flac: OK
23. People's Playground Version E.flac: OK
24. The Six Wisdoms of Aspasia.flac: OK
CUE Sheet File - 3 Films by Jess Franco (flac).cue: OK
CUE Sheet File - 3 Films by Jess Franco (wav).cue: OK
CUETools LOG File - 3 Films by Jess Franco.accurip: OK
EAC LOG File - 3 Films by Jess Franco.log: OK
folder.jpg: OK
md5sum: Artwork\3 Films by Jess Franco - folder image.jpg: No such file or directory
Artwork\3 Films by Jess Franco - folder image.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco back booklet Large.jpg: No such file or directory
Artwork\3 Films by Jess Franco back booklet Large.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco back cvr.jpg: No such file or directory
Artwork\3 Films by Jess Franco back cvr.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco book 1.jpg: No such file or directory
Artwork\3 Films by Jess Franco book 1.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco book 2.jpg: No such file or directory
Artwork\3 Films by Jess Franco book 2.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco book 3.jpg: No such file or directory
Artwork\3 Films by Jess Franco book 3.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco book 4.jpg: No such file or directory
Artwork\3 Films by Jess Franco book 4.jpg: FAILED open or read
md5sum: Artwork\3 Films by Jess Franco front cvr Large.jpg: No such file or directory
Artwork\3 Films by Jess Franco front cvr Large.jpg: FAILED open or read
md5sum: Artwork\CD Info.jpg: No such file or directory
Artwork\CD Info.jpg: FAILED open or read
md5sum: WARNING: 9 listed files could not be read
fulcilives@fulcilives-CG5270:~/Music/Soundtracks - Film & TV/3 Films By Jess Franco - Manfred Hubler & Sigfried Schwab [FLAC]$ 

```
It doesn't seem to be able to "see" the files in the **Artwork** sub directory.

BTW the MD5 file is the same one I posted in an earlier post in this thread.

---

### Post by jerome1232 on 2012-03-16
oh, haha, doh! I should've realized this a long time ago.

The problem is Windows uses back slashes while Linux uses forward slashes.

```
C:[COLOR="Red"]\[/COLOR]blah[COLOR="Red"]\[/COLOR]blah[COLOR="Red"]\[/COLOR]blah
###
###Linux does this
###
[COLOR="Red"]/[/COLOR]blah[COLOR="Red"]/[/COLOR]blah[COLOR="Red"]/[/COLOR]blah
```

---

### Post by FulciLives on 2012-03-16
LOL

oh jeez

That worked.

I opened up the MD5 and did a SEARCH & REPLACE for "Artwork\" to "Artwork/" and then saved the file under a new name, "checksum_for_linux.md5"

Then I simply did this in Terminal: **md5sum -c checksum_for_linux.md5**

And it works !!!

I'm used to using the SEARCH & REPLACE function in Windows Notepad so having to do this in Linux (in the way I described) isn't the end of the world (especially since I normally only ever have one sub directory so it's just one SEARCH & REPLACE per file).

Still I wish I didn't have to do all that *sigh* but at least it is all sorted out now.

Thank you VERY MUCH for your help :)

I owe you big time my friend!

---

### Post by jerome1232 on 2012-03-16
I was playing and maybe there is a more elegant way to do this but this seemed to convert the slashes, it finds all instances of "\" and replaces it with "/". AFAIK files aren't allowed to have those characters in their names so it shouldn't ever mess with a file name to simply find all backslashes and convert them to forward slashes.

```
sed 's:\\:\/:' md5file
```

that will show you what the changes would do, to actually do it

```
sed -i 's:\\:\/:' md5file
```

Want to go backwards (convert it back to windows path)

```
sed -i 's:\/:\\:' md5file
```

---

### Post by FulciLives on 2012-03-16
I was hoping you might come back with a more, as you say it, elegant solution hehehe

I haven't tried it yet but it makes sense. I'll post back as to how it worked when I do get to try it.

Thanks again :)

---

### Post by jerome1232 on 2012-03-16
The best I can think of is creating an ugly little bash script so you don't have to remember the commands.

ie in gedit make this


```
#!/bin/bash
if [ -z "$1" ]; then
        echo usage: $0 file
        exit
fi
SRCF=$1
dos2unix "$SRCF"
sed -i 's:\\:\/:' "$SRCF"
exit 0


```

save it as convert2linux.sh (or whatever), right click it make it executable. Make a folder in your ~/ called "bin", put the script in there, logout then log back in. Now from a terminal you could do this (from any directory since the ugly script will be in your $PATH now) 

```
nameofyourscript.sh /full/path/to/md5sum
```

---

### Post by FulciLives on 2012-03-16
The script works great but is there a way to add to the script so that it makes a new file instead of over-writing the existing file? I'm fine with the same filename time and time again, say something like, "linuxchecksum.md5" or "linuxmd5.txt"

---

### Post by jerome1232 on 2012-03-16
Yeah, I actually initially had one up but it broke if you used quotes in your file path so I changed it. (I'm not very good at bash scripting :D)


This breaks if you put quotes in your file path and I don't know how to fix that :/

If you wanted to get crazy you can add a lot more error checking (like if the file exists etc...) But that's more for someone who actually knows how to bash script, you could always ask over in the programming section how you could improve it.


```
#!/bin/sh
if [ -z "$1" ] || [ -z "$2" ]; then
        echo usage: $0 infile outfile
        exit
fi

SRCF=$1
TGTF=$2
dos2unix "$SRCF" "$TGTf"
sed -i 's:\\:\/:' "$TGTF"

exit 0

```

---

### Post by The Cog on 2012-03-17
This command should convert your windows mdsum files to *nix format:```
sed -i -e 's,\r,,g' -e 's,\\,/,g' md5file
```
It removes the carriage returns and changes backslash to slash. Replace **md5file** with the name of the file to convert.

---

### Post by qyot27 on 2012-03-17
> **FulciLives said:**
> The script works great but is there a way to add to the script so that it makes a new file instead of over-writing the existing file? I'm fine with the same filename time and time again, say something like, "linuxchecksum.md5" or "linuxmd5.txt"
The -i command that you're giving to sed means 'inplace'.  Remove it and sed won't modify the original file.  But by default, it will output the result to the Terminal window.  To make it output to a new file, you need to use the > character and specify a new file name to dump the output to.

For instance, yet another way to do all of this:
```
sed -e 's/\\/\//g' md5file | fromdos > md5file_new
```
sed leaves the original file alone, the | character tells it to pipe a modified version with all backslashes converted to forward slashes to fromdos (tofrodos package), which converts CRLF to LF and finally the > tells it to dump the result to a new file.  In a script, it could be made to look like this:

```
#!/bin/bash -x
set -e
sed -e 's/\\/\//g' "$1" | fromdos > "$1"_new
```
Let's call this script convert.sh
The -x in the hashbang line tells bash to display the commands as it runs them, and *set -e* tells the script to stop if it encounters an error.  It probably isn't too useful in this case since you're only running one command, but it's a good safety check.

You can then use it like this:
```
./convert.sh inputfilename
```
and it'll output a new file with _new appended to it.

---

### Post by FulciLives on 2012-05-02
> **The Cog said:**
> This command should convert your windows mdsum files to *nix format:```
sed -i -e 's,\r,,g' -e 's,\\,/,g' md5file
```
It removes the carriage returns and changes backslash to slash. Replace **md5file** with the name of the file to convert.
It turns out that this line of text is most valuable to me. It easily converts a MD5 file that was made in Windows to something that works in Linux. As a bonus I've found that it still manages to work in Windows after the change!

It seems that Windows doesn't care about the formatting as much as Linux does LOL

I've even installed "md5deep" in Linux and Windows and use that now to make my md5 checksum files (which I call: checksum.md5)

Anyway here's a question:

Is there a way to do this magical line-of-code from the Windows CMD prompt? I tried it but Windows said there is no "sed" command.

My thinking is this ... when working in Windows and making a MD5 it would be nice if I can change it to a Linux friendly format. Doing so immediately after making the md5 checksum is helpful since 1.) Windows will work with both formatting options (Windows & Linux) and 2.) I'd rather do the change as I make it so I don't later forget and have to do it later while I'm in Linux.

Any ideas?

---

### Post by qyot27 on 2012-05-02
You can get sed (and most of the rest of the standard Unix utilities) on Windows by installing MSys or Cygwin, which will make them available through MSys' or Cygwin's version of bash.

To make it visible to the normal Windows Command Prompt, you would add MSys' or Cygwin's /bin directory to Windows' PATH variable.  This can be edited through the Control Panel's System dialog.

---

### Post by FulciLives on 2012-05-03
Thanks for the tip. I went ahead and installed Cygwin on my Windows 7 (64-Bit) install. It created a directory called Cygwin on the C: drive with a bunch of stuff under it (including a /bin directory) so I added that path "C:/Cygwin/bin" to Windows and rebooted.

However I can't seem to get any of the info here to work.

For instance if I try this:
```
sed -i -e 's,\r,,g' -e 's,\\,/,g' md5file
```
I get the following:
```
sed: -e expression #2, char 7: unterminated 's' command
```
I should point out that I have no idea what it is trying to tell me and that this does work in Terminal while using Ubuntu.

So after that didn't work I decided to try this:
```
sed -e 's/\\/\//g' md5file | fromdos > md5file_new
```

When I do that I get the following:
```
'fromdos' is not recognized as an internal or external command, operable program or batch file.
```
Again this works in Ubuntu BUT it did prompt me to install "fromdos" so maybe I need to do that in my Windows 7 install of Cygwin but I'm not sure how to do that.

-----------------------------------------------------------------

OK well this is interesting ... 

After typing all the above (but before posting this) I did some Google searches and I found out that Cygwin includes a command called "dos2unix" and if I simply do that:
```
dos2unix checksum.md5
```
checksum.md5 is what I call my checksum file and using the code above converts it to a format that Linux can now use. So actually this makes it very simple! The only odd thing is that it does NOT change the slash from "\" to "/" but it still works in Linux (Ubuntu) when using "md5sum -c checksum.md5" so I'm happy but that seems against what the other stuff was doing?

So in short I've found that I can make a MD5 in Windows using either the GUI that I use OR using MD5DEEP (which I installed) and that I can now just run DOS2UNIX (thanks to Cygwin) and get a checksum file that works in Windows AND Linux.

So I'm happy!

Thank you again to all who have helped me ... I would have been utterly lost without all the help!

I'm marking this thread "solved" but if anyone has any further input please do so :)

---

### Post by qyot27 on 2012-05-03
You can get the Windows version of tofrodos (since it has both todos and fromdos in the package) from here:
[http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)

Just unpack it and stick them in C:\Windows


The untermination errors indicate that the syntax is written incorrectly somehow, and the expression and char #s indicate precisely where in the command it went wrong.  According to that error, it has a problem with the ,g in the second part of the command (possibly because of the / that comes immediately before it being interpreted differently).

Windows and Linux have different sets of escape and/or forbidden characters and therefore what works on one platform may not work on the other (although it's also sometimes Terminal-specific; you might be able to use the unaltered commands on Windows if you use the normal Cygwin terminal).

---

### Post by FulciLives on 2012-05-04
Thanks again for the info!

I got **tofrodos** installed but I'm probably just going to do what I mentioned before, i.e., use the "dos2unix" command but it's good to know about and play with all this stuff so thank you again.

---

