---
title: "Font Folder Location"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by CountyPyr on 2008-10-17
Hi

I'm brand new, & I just installed version 8.04 LTS. I need to add some of my Windows fonts, but I haven't been able to figure out where the Font folder is located.

Also, is there a specific procedure for adding a font, or do I just drag and drop the .tty file into the Font folder?

Thanks for the help.

---

### Post by kaibob on 2008-10-18
The easiest way to install new fonts is to place them in the /home/username/.fonts directory. You will have to create this folder if it's not present. 

The following Ubuntu Wiki provides detailed instructions on the installation of fonts:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by CountyPyr on 2008-10-18
Hi

Thank you for the help. BTW, I am surprised that there are so many locations in which to keep fonts. Any idea why? I would have thought that a single global repository would be both the simplest and easiest way to handle this function.

The other surprise is that this isn't accomplished by either a simple drag-and-drop of a file(s) or even a <Ctrl + C> & <Ctrl + V> of a file(s).

---

### Post by redseventyseven on 2008-10-18
There are a few places to install fonts for a few reasons. One is so that you can choose between installing them just for single users and installing them for everybody. Another reason is that linux simply gives you options! Different distributions handle fonts in slightly different ways by default, and you as a user are free to stick with that or try a different way of doing things. It's different from the windows way of doing things. I'm not saying it's better or worse, it's just different.

Fonts which are installed by packages (using Synaptic Package Manager or the apt-get commandline tool) which come from online repositories will install themselves in the "system-wide" part of your computer, which is a little fiddly (but possible) to install things on manually. The fact that there's also a place in the "user's home" part of your computer where you can install fonts takes a bit of getting used to, but it's just nice to have options.

It is possible to install fonts by dragging-and-dropping or cutting-and-pasting, by the way. Folders that begin with "." are hidden by default; you can display hidden folders in the nautilus file manager by pressing Ctrl-H. If you do this in your home folder, you should reveal a folder called ".fonts". Open this folder and you should be able to drag and drop to your heart's content.

---

### Post by kaibob on 2008-10-18
> **CountyPyr said:**
> ...The other surprise is that this isn't accomplished by either a simple drag-and-drop of a file(s) or even a <Ctrl + C> & <Ctrl + V> of a file(s).

All you need to do is copy the font (tty) file to the ~/.fonts directory. After a restart, the font is available for use without taking any further action.

Just to check this, I did the following:

1) Opened Nautilus and copied the kartika.ttf file from the Windows font directory to my Ubuntu ~/.fonts directory.

2) Opened gedit and checked the "editor font" under preferences. Kartika was shown as a font option. 

3) Loaded OpenOffice Writer and kartika was shown under the drop-down list of fonts.

---

### Post by Kellemora on 2008-10-18
Hi CP

Don't want to buck against those who have been around much longer than I have, BUT.

We place ALL of our ttf fonts in
/usr/share/fonts/truetype
where I feel they BELONG...........

I just moved some Bitstream fonts again the other day.
They had hard to find ID numbers as file names, such as TT0710M_.ttf
I HATE THAT..........

I made a new FOLDER in the /usr/share/fonts/truetype directory that reads simply ttf-bitstream-charter, as these are the Charter group of Bitstream fonts.  I ALSO renamed each of the files from the numbering scheme to what each font really was, such as TT0710M_.ttf was changed to CharterBlackItalicBT.ttf

Changing the names of the files, nameing the folder anything you want, has NO AFFECT on how the font is found or performs.  Font's get their data from the actual FONT itself, NOT from the filename.
So just name it anything that has meaning to you.....

EVERY program can FIND the fonts if they are where the programs and system expects to find them!  

If you are trying to copy fonts from another computer, you may get the access denied warning.
No problem!
Move the font into a shared folder on the other machine.
Move the file to a folder on your machine or the desktop.
Open Nautilus as ROOT and make your way to the folder or desktop where you put the fonts, highlight and copy them.
NOW you can paste them into your fonts folder with no permission warnings.

Just remember, Proprietary fonts ARE NOT Portable, so embedding them in documents will not work on another computer.
If you are a licensed user, some give codes that allow the use of part of the set as embedded.
Or what I do when I'm sending a document to a public printer, I will send them a copy of each of the fonts used in the document.  They install them, run my order, then uninstall them, OR they are supposed to uninstall them.

TTUL
Gary

---

### Post by reg4c on 2008-10-18
Kellemora has mentioned the easiest way to install fonts:

gksudo nautilus

Navigate to /usr/share/fonts/truetype

Paste the fonts there, and done!

Cheerio

---

### Post by CountyPyr on 2008-10-18
[QUOTE=redseventyseven;5988337] <There are a few places to install fonts for a few reasons. One is so that you can choose between installing them just for single users and installing them for everybody.<

I understand the logic of "Global" & "Specific User". I am lost on what /user/local/share/fonts means when /username/.fonts is for the specific user. Does this restrict the fonts to only the users of a specific computer? If so, does "Global" mean all users on both the specific computer as well as users on the local network?

According to /etc/fonts/fonts.conf, fonts are also stored in /user/share/x11/fonts. What's a x11?

>It is possible to install fonts by dragging-and-dropping or cutting-and-pasting, by the way.<

I was neither as thorough nor as accurate as I should have been when I mentioned the drag-and-drop and copy-paste methods in my first response post to kaibob. In the Ubuntu wiki to which he directed me, the user is told to create a new directory in Nautilus /usr/share/fonts/truetype. However to do this requires acquiring root permissions. So far, the only way that I have found to do so is by entering text at the prompt in a terminal window (gksu & sudo). I should have said that I would have thought that creating a directory and/or dropping files into a directory belonging to root would have initiated a pop-up box requesting the root password. Instead, the pop-up box simply stated that I didn't have permission to complete the task. In Nautilus, I also reviewed its menu system, however I did not locate any menu item in Nautilus that allows for temporarily becoming root, either. Have I just missed how to do it, or is this just a Gnome and/or Nautilus security "feature"?

---

### Post by CountyPyr on 2008-10-18
> **kaibob said:**
>  <All you need to do is copy the font (tty) file to the ~/.fonts directory.<


I apologize. I did not state my thoughts in a clear and accurate manner. Apparently, I thought that I was multi-tasking, and yet my mind wasn't fully engaged. Please see my response to redseventyseven for an explanation as to what I was trying to say to you. And BTW, you really need to improve your mind-reading skill set.

---

### Post by CountyPyr on 2008-10-18
Hi Kellemora

Like you, I just need to place my fonts in the "global" container. I am the only user on my computer, and if I create additional user names for me, then I expect that I shall still want/need access to the installed fonts. This thinking is probably a carryover from being a Windows person.

Thanks for the information about being able to change the font file's name. I hadn't thought about doing that, but it sure would make life easier.

Fortunately, embedding fonts in a document is not an issue for me.

---

### Post by Kellemora on 2008-10-18
Hi CP

The ONLY time I may place a font in the hidden folder in my /user directory is when it is a privately owned font belonging to a customer and can ONLY be used in their documents.  More often than not, these are not fonts as you think of them, but company logo's, special insignia's, proprietary letters.
By placing them in my home/client directory, it prevents them from appearing anywhere else.
Examples would be like the word Splenda would appear as an oval about 15 characters long, or the deep 6 logo would take up 4 vertical lines, but work similar to a drop cap, without my having to do anything except hit the proper key.
I'm sure you've read lot's of various texts over the years where you find this in documentation or on labels in the text areas.

But also I have their entire font's in there too for a few companies too.

I think you asked about the X11 fonts folder.  I'm not sure but I believe those are the SCREEN fonts used by X.

I have about 10,000 more fonts than Windows could handle without Choking on them, hi hi.....  Crashed the Doze many times by not removing fonts before installing new ones.  So, even on the DOZE machines we had separate font files, which were a royal pain.

Linux has some GREAT features not found in the DOZE, and one of these is your ability to put fonts into their own folders, and place them in different areas as well.

I'm a noob too, so haven't quite figured out how to cause only certain fonts to appear for certain purposes yet, OTHER THAN storeing them in client folders in my /home directory.  Means I have to log off and back on when working on that clients stuff to have access to those font's, unless they are in my personal /user directory.

It's just too darn tempting to want to use something you know is in another clients font folder because it saves a lot of work sometimes.
But if I forget to highlight it and change the font, my head could roll, hi hi...........

But personally, I feel having all your fonts in one convenient place is the way to go.  That way you know WHERE they are, and all users can use them.  And the ability to group them into their own folders makes keeping up with what you own or have so simple compared to the DOZE.  One of the reasons I put the manufacturers name in the Folder name, BEFORE the font name.  That way all ttf-Bitstream-anything folders are listed with all the Bitstream fonts together.  For "me" it's important to know which ones are proprietary and which ones are public domain and/or portable.

Now that I've switched the office over to Linux completely, finding my maze of font types for one group style is a daunting enough task.  But the ability to put them into their own folders is truly a Godsend over the Doze method.

And thanks for the thank you as well!

If this post is now solved, you can go to the TOP and under THREAD TOOLS, at the bottom is a line that says SOLVED, click on it to mark the thread solved.

TTUL
Gary

---

### Post by Kellemora on 2008-10-18
Duplicate Post

---

### Post by CountyPyr on 2008-10-19
Hi Kellemora

You Wrote:
<And the ability to group them into their own folders makes keeping up with what you own or have so simple compared to the DOZE.>

Yes, I can see the possibilities. I agree with you that having the capability to assign fonts to separate folders is much better.

You Wrote:
<X11 fonts folder. I'm not sure but I believe those are the SCREEN fonts used by X.>

This is confusing for a noob. First their is Gnome, & then it appears that their is an x inside the Gnome. Also, it seems that there might be a Compiz in there, too. Presumably, this is all part of the flexible and interchangeable bigger picture.

You Wrote:
<If this post is now solved, you can go to the TOP and under THREAD TOOLS, at the bottom is a line that says SOLVED, click on it to mark the thread solved.>

Thanks. I do know about this procedure. The reason that I haven't marked it solved, yet, is that I still have questions outstanding from my response to "redseventyseven". I realize that the original question has been resolved, but the anciliary questions that it generated seemed to still fit inside the thread, at least to me. Let me know if you think that I should mark this thread solved, and then start another one about the anciliary questions.

---

### Post by Kellemora on 2008-10-19
Hi CP

It IS better to keep separate questions in different threads, AND put the topic in the subject line too, as then some of the guru's here might see it and respond faster.

I'm a noob to, so my response could be all wrong.
X-Window is the feature that allows you to use the Graphical Interface of your choice, such as Gnome or KXE or whatever that other one is called.
Or as I see it, instead of JUST WINDOWS, you have a choice of many different GUI's (window versions), but regardless of which windows version you choose, it has to run on (for lack of a better term) a windows generator.  I've read about it enough times I should remember, but I IS Olde Now and would forget my own name if it wasn't pinned to my shirt pocket.  At least I found out my name wasn't really 'Kick Me' which I found pinned to the back of my shirt quite often, hi hi..........

On the Font's - It's easy to amass thousands upon thousands of fonts, but we most often only have a few we really like.  I started using proprietary fonts as that way I knew I had FULL FONTS (usually).  A lot of these free ones truly are lacking substance, and some flat out cause problems too!

Since windows didn't allow font folders, I maintained separate font files, and for a long time used to even print out books of my fonts until even they became to wieldy to handle.
When I found a font in PRINT somewhere that I really liked, I would find out what it was and get a full copy of that font set, often only to discover I already owned it, under some obscure name or number.
That's when I discovered you could rename your fonts to any name you wanted to use for them.  In my case, I used a simple fontographer program that would READ the name of the font from the file, then rename the file to that name.  All I had to do was hit a button and wait 37 hours for it to run all of my fonts and rename them.
But there is a bad side to that too!
You end up downloading or buying fonts based on the original file name and still end up with duplicates.  But today they have font comparison programs that can line up all your similar fonts quickly.

So far, the only thing I have NOT figured out yet, is if I can store fonts in a directory in Linux and NOT have Linux programs find them.  I'm hoping so because the last Windows machine I have here is soon to be converted to Ubuntu also.  Right now I'm using some unmounted drives for Archival Storage of Data I like to keep handy.  I'm thinking of taking a couple of older drives and loading all of my fonts onto them and sticking it on a shelf.

Don't laugh at this!  I still have half a zillion 5-1/4 floppies, one original font set on each one.  Started moving them over to CDs last year, before I can't get any 5-1/4 inch drives anymore.  I lost quite a bit of old archived data from 8 inch floppies when we got rid of the Wang VS or maybe it was Lisa, don't remember that far back, hi hi.......

Good Luck

TTUL
Gary

---

### Post by CountyPyr on 2008-10-20
Hi Kellemora

You Wrote:
>It IS better to keep separate questions in different threads, AND put the topic in the subject line too, as then some of the guru's here might see it and respond faster.<

I shall initiate a new thread for each question. Thanks for the advice.

I think that the other window program to which you refer is KDE.

You wrote:
>So far, the only thing I have NOT figured out yet, is if I can store fonts in a directory in Linux and NOT have Linux programs find them.<

Perhaps changing a file's extension would work like it would in Windows? eg font.tty changed to font.tt_

You Wrote:
>half a zillion 5-1/4 floppies<

Boy, I haven't seen a 5-1/4" disc in a long, long time. I began working with PCs after 5-1/4" discs replaced 8" discs so I never have used one.

With all of those fonts, I presume that you use both desktop publishing and image editing programs. I am curious as to which Linux versions of these programs that you use. I do some desktop publishing for my micro-sized company - technical manuals primarily. In the Windows world, I use Corel Photo-Paint for image editing and Corel WordPerfect for both word processing and desktop publishing.

---

### Post by Kellemora on 2008-10-20
Hi CP

Our primary business was publishing, things like pamphlets, newsletters, yearbooks for smaller schools, etc.

If you didn't notice, I'm a noob too!  Just stared using Ubunu in the first week of September and have already converted my whole office over to Ubuntu.  Right now I'm using Open Office, have converted almost all of our doc over to odt.

As far as graphics, I can't even recommend a good one for windows.
I use like 9 different programs because each one has a specific feature that does exactly what we want it to the way we want to do it.

Look at it this way, with all the mega powerful word processing programs out there, not a single one of them has a very simple feature that was introduced with Windows 3.0 WRITE......  We still use the 3.11 version of Write every single day, it's the BASE that we build nearly every document from.  You might call it our Draft Horse.  As simple as Windows WRITE is (the original, not word pad they called write also), it can literally shave HOURS sometimes days on larger projects.  Once we have the text laid out the way we want it, then we move it over to OOwriter to finish the job.

Despite the fact I have a few very expensive graphics programs here, I do most of my editing and restoration on MGI PhotoSuite and an even older program called Foto Touch Color or FTColor for short.  Like Windows Write, it has a feature I've never found in ANY OTHER program, no matter how expensive.  However FTColor is only used for one purpose!  I have PhotoGraphics, expensive, not worth a hoot, Oh, I use a 9 buck program for balancing a crop to the rule of thirds, because it's fast and you can make adjustments without starting over.

Because we still have ONE Doze machine left here, and due to the changeover I've been totally swamped.  I have not yet had time to try out different graphics programs other than Gimp, with Xsine.  I have some nice scanners here that were designed by HP for an HP computer, the software sucks canal water and it won't run on the HP computers.  Runs fairly well on an older 1.6gig Compaq, but on Ubuntu, it shines like it never shone before.  Fast and nearly perfect every single time.  But, I haven't done much more than set it up and scan some test images to see how it worked.  I'm very happy with it now.  And what I've used of Gimp so far, it seems to do the trick for scanning and preliminary adjustments.

Now, the graphics and images we use in newsletters and the like, that's a whole different ball game that photo restoration and/or removing backgrounds, taking out people or places, etc. which is a side business I sorta cut back on after moving south.  Too many hours for not enough money if you know what I mean.  
I restored some old photo's for a local VFW Hall as my last job, so as you realize that was near gratis work, hi hi.......

I'm sorry, I get carried away, keep forgetting this is an instructional forum, not a chit chat.

TTUL
Gary

---

### Post by CountyPyr on 2008-10-20
Hi Kellemora

You Wrote:
>We still use the 3.11 version of Write every single day<

I am curious, what is the "simple feature" that only WRITE has?

---

