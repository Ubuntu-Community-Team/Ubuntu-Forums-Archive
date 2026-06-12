---
title: "GUI app to batch &quot;sanitize&quot; filenames so that Windows can handle them?"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by Haisiong on 2013-09-16
I&#8217;m a Windows user who wants to convert.  I&#8217;m not averse to
learning.  Back in the day, I used to enjoy DOS 6.22, and even 
played with batch files a little.  Now I want to go with Linux, 
I really do.  But some annoyances are pretty off-putting.

I&#8217;d like to download files using Linux on the web, then transfer them
across OS&#8217;s, i.e. handle the saved webpages in both Lubuntu and XP.  
 I&#8217;m flabbergasted at my inability to simply save a webpage in Linux 
then read and manipulate it in Windows.  

For instance: I see an Amazon review webpage, or a Frys advertisement
which I want to read later.  I click &#8220;save&#8221;.  If the .mht or .html filename 
saves with a &#8220;:&#8221; or a &#8220;|&#8221; (as many do), it seems I can&#8217;t copy it to a thumb drive 
and paste it to an XP machine.  

So after using a day of my life googling, I learn that there are some 
characters in filenames which Linux does permit while Windows doesn&#8217;t.  
And I see that I&#8217;m not the first to encounter this difficulty while trying to 
use both OS&#8217;s. 

I read plenty of forum postings by Linux users who, with the zeal of
religious fundamentalists, berate Microsoft for this, but don&#8217;t offer help.
I see tutorials detailing at tedious length the history of file systems, but 
again offering no solution.  Finally I find command line methods for 
dealing with the forbidden characters, but as a Linux newbie I&#8217;m baffled 
by command line syntax.  Evidently it&#8217;s fundamentally different from DOS.  

So maybe I need to spend another day of my life getting spun up on basic 
use of the linux command line.  Or maybe I need to wait another 10 years 
for Linux to become friendly to those who wish to migrate from Windows...
Frankly, I don&#8217;t have an unlimited amount of free time to learn these things 
today, right now.  I&#8217;d like Linux to just work, and permit me to climb the 
learning curve and learn the finer points at my leisure.

It appears the app &#8220;Glindra&#8221; includes a command &#8220;rena&#8221; which has a &#8220;-safe&#8221; 
switch which &#8220;maps problematic characters like *?:[]"<>|(){} to underscore&#8221;.
Sounds like just the ticket!  But after a few failed efforts at installing and using
the app, I realize I&#8217;m still too perplexed by the file structure of Linux to install 
this app correctly.  
 
Please.  Is there no GUI app in Linux that will let me quickly and easily
batch &#8220;sanitize&#8221; filenames so that Windows will handle them?  
Pyrenamer seems to offer promise, but it&#8217;s not clear how to make it
drill down and operate in subdirectories.

There have been other massive annoyances in getting up and running with Linux 
(can&#8217;t copy and paste to a terminal, can&#8217;t easily set up an extended desktop to a 
2nd monitor) but this one takes the cake.  Discourages one from migrating to Linux.

Come on guys, I&#8217;m really missing something here, right?

---

### Post by buzzingrobot on 2013-09-16
You are, I fear, setting Windows up as the standard for operating systems.  It isn't, becuse there is no standard operating system.

The characters ":" and "|"  have special meaning in Unix and Linux shells.  The first is the path separator and the second is the piping symbol.  You don't say how you were copying the files, but, research how to escape characters to avoid their interpretation as those special symbols.

In any case, why not just save the URL's?

If you expect Linux to work exactly like a Windows, you will be very frustrated.

(If you are, in fact, copying the files in the shell, try bracketing the filename with quotes, or, putting a '\' immediately before each obstreperous character.  Can't guarantee this; it's been years since I had to worry about moving files to Windows.)

---

### Post by QIII on 2013-09-16
> 
There have been other massive annoyances in getting up and running with Linux 
(can&#8217;t copy and paste to a terminal, can&#8217;t easily set up an extended desktop to a 
2nd monitor) but this one takes the cake.  Discourages one from migrating to Linux.

These are just matters of learning something new.  There is a bit learning curve, and it is sometimes a bit frustrating. But it is there.  Think of it like learning a new language.  It takes a little work.  But it starts to make sense after a while.  After that, it becomes fun.

Linux does (mostly) just work.  But not the same way as Windows.

You can paste to a terminal using CNTL + SHIFT + V (in most terminal emulators).

You can easily set up an extended desktop when you learn how.  It will depend on whether you are using the default video driver or a proprietary one.  Here, for example, is my desktop spanning three monitors.

[ATTACH=CONFIG]246290[/ATTACH]

As for the mass-renaming, unfortunately I don't know of a utility to do that, but someone will surely be by with a suggestion.

Have patience and don't expect to know how to do everything right off.  It takes a while to learn a foreign language.  Have some fun with it and enjoy the trip.

---

### Post by Haisiong on 2013-09-16
QIII, I&#8217;m much obliged.  I can appreciate the analogy about language.
I have known the frustration of language immersion overseas, having to 
revert to being a helpless child, and eventually over time becoming 
conversant in a foreign tongue.

Now.  As for this filename issue, I still do believe the Linux-Windows dysfunction is  
surprising.  Google tells me that I&#8217;m not the only one who has raised an eyebrow at this.  

On my laptop running Lubuntu, Frys webpages do save in Linux with a &#8220;|&#8221; in the filename, 
and Amazon&#8217;s with a &#8220;:&#8221;.  And that means those saved webpages can&#8217;t be opened later 
on a Windows box.  

Interoperability would be a good thing, would it not?  We who wish to migrate from Windows
can't do it instantaneously!

Anyway, after reading your words, I was encouraged to try again.
Found that pyRenamer, a GUI app, will fix my numerous folders that
contain problematic filenames, in a quick enough process that although 
not terribly elegant is not too troublesome either.  And in the process 
I learned that &#8220;Add files recursively" is evidently another way to say 
&#8220;include subfolders".

FWIW, in case it helps other newbies:

Open pyRenamer
Find the saved files and folders under 
   media\b\ (the thumb drive)
Highlight the files and folders in the right pane
On the right, click &#8220;Add files recursively"
On the tabs below, click &#8220;Substitutions&#8221;
Click &#8220;Replace"
type : and _
click &#8220;Preview&#8221; 
Click &#8220;Rename"
Repeat, replacing |, ?, and &#8220; with _.

That seems to rehabilitate most all webpage filenames
that include problem characters.

 Thanks to all and again to you QIII for the encouragement.

---

