---
title: "Oh No!!!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by jwkungfu on 2008-05-16
I downloaded the Alternate CD for upgrading Gutsy to Heron...

It took ages, my net connection isn't very quick at all...

It should be on my desktop (that is where I like to save things to and that is where the download window said that it was downloading it to...?)

There was a message saying that it was unable to burn the CD (I think it mentioned something about not having a CD to burn to...)
As it was early in the morning and I was about to go to work, I thought I would burn the CD from the file on my desktop when I got home....

There is nothing on my desktop?????!!!!

Surely it has saved the file to my desktop?!!
How can I check my whole computer to find this file (can't be too hard to find? It is 699MB after all???!!!)

---

### Post by wormser on 2008-05-16
Check in /tmp.

---

### Post by hyper_ch on 2008-05-16
Use torrent for downloading the cd... it will also make sure that the download is not corrupted...

Here you can find all .torrent files:  [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by jwkungfu on 2008-05-16
> **wormser said:**
> Check in /tmp.

Thanks for the reply!

I tried a terminal...

john@john-laptop:~$ ls /tmp
gconfd-john     mapping-john  ssh-LLOleS5648     virtual-john.BddTmZ
keyring-FSpVtx  orbit-john    Tracker-john.5822

Not sure what that is telling me.....?

---

### Post by shifty_powers on 2008-05-16
it's giving you a list of files in the /tmp directory.

you're download obviously isn't in there.

how quickly do you need it? canonical will ship ubuntu on cd for free you know...

otherwise do a search for the file name i suppose...

---

### Post by PmDematagoda on 2008-05-16
How did you download the file in the first place?

---

### Post by jwkungfu on 2008-05-16
Thanks!
I have just requested another CD now...
I had troubles with the Install CD when I first swopped over to Ubuntu, a friend helped me out with CD's that he already had...
I'll just have to wait until my new CD arrives and give it a whirl then... hopefully no problems....

I am rather annoyed that the download is not on my desktop!!!!
How can it be that it was saved to another place?
It said destination desktop under the download bar!!!!!!!!!
It's no wonder newbies like myself have such problems when applications do such silly things!!!!!!!?

---

### Post by Malac on 2008-05-16
I suspect you accidentally tried opening/running the iso instead of saving it. I've done this myself from the download window. When this is chosen the file is downloaded to a temporary location for opening.
 
When it said "Unable to Burn CD", that was burning software trying to open it from the /tmp location. When this was cancelled the file in /tmp is deleted as it is considered finished with.
 
Hope this helps.

---

### Post by shifty_powers on 2008-05-16
yep sounds about right. think we've all done that at some point ;)

---

### Post by jwkungfu on 2008-05-17
I think you have hit the nail on the head...

Perhaps it's an over-sight by the people who made the application and I suppose it's impossible to create an application that will cover absolutely every possible situation that a newbie may stumble in to? 
Even if it results in losing a 699MB file that took over 7 hours to download.....

This is exactly the kind of thing the Ubuntu community needs to address!

It's OK to say Linux/Ubuntu isn't M$ but at the end of the day, if you are going to have a GUI then that GUI 'must' be as user friendly as possible ie. safe-guarding people from losing their data, error messages that have web links to possible fixes etc etc etc...

More attention to covering such 'problems' and people who try Ubuntu are alot less likely to go back to the dark side...

Cheers!
Ubuntu/Linux still rules!!!!!

:o)

---

### Post by SlappyPappy on 2008-05-17
Sure........  :)

---

### Post by ugm6hr on 2008-05-17
> **jwkungfu said:**
> Perhaps it's an over-sight by the people who made the application and I suppose it's impossible to create an application that will cover absolutely every possible situation that a newbie may stumble in to? 
Even if it results in losing a 699MB file that took over 7 hours to download.....

This is exactly the kind of thing the Ubuntu community needs to address!

It's OK to say Linux/Ubuntu isn't M$ but at the end of the day, if you are going to have a GUI then that GUI 'must' be as user friendly as possible ie. safe-guarding people from losing their data, error messages that have web links to possible fixes etc etc etc...

More attention to covering such 'problems' and people who try Ubuntu are alot less likely to go back to the dark side...

Is the application you talk of Firefox?

If so - then this is not an Ubuntu-specific issue, but a browser-wide problem.

All browsers (IE included) offer to download or open all files you select (unless you set them up otherwise).

It's unfortunate that not everyone realises that "open" means that it is downloaded to a temporary location, and is deleted at restart.

---

### Post by shadow-of-sin on 2008-05-17
The same thing happens for Windows AFAIK if you "Open" a file instead of saving it to hard disk(on any browser, not just Firefox)
EDIT: oops, didn't notice ugm6hr's post which says the exact same thing as mine...

---

### Post by jwkungfu on 2008-05-17
If I remember correctly...
I went to the Ubuntu site, clicked on the Alternate version of the Hardy upgrade CD and then a download window opened with the download bar and underneath it clearly said "Desktop"....?

I just think that it makes far more sense that by default all files should be saved onto something unless it is specificly requested to save it to a place where it could be very easy to accidently delete... as I found out...

After all that is why it's called a "Desktop".... 

But I'm not a programmer/developer.....   ;o)

---

### Post by jwkungfu on 2008-05-17
> **shadow-of-sin said:**
> The same thing happens for Windows AFAIK if you "Open" a file instead of saving it to hard disk(on any browser, not just Firefox)
EDIT: oops, didn't notice ugm6hr's post which says the exact same thing as mine...

OK
I guess my whinge goes beyond Ubuntu/Linux/M$ etc...
As a novice to computers I feel that too much effort is wasted in "developing" computers and not enough attention paid to making sure they do as they should... From a newbies perspective.... which is not knowing one end of the stick from the other........

---

### Post by HotShotDJ on 2008-05-17
> **jwkungfu said:**
> I just think that it makes far more sense that by default all files should be saved onto something unless it is specificly requested to save it to a place where it could be very easy to accidently delete... as I found out...There are often very good reasons NOT to do that.  Defaulting to "Save" rather than "Open" would aggravate me to no end!  Firefox (and most other browsers) default to asking you what you would like to do with files that you click on.  This makes perfect sense.  The problem is that MS Windows has trained people to just click "OK" whenever a dialog box comes up without even reading what the dialog says.  A huge number of Windows users would click "OK" in a box that said "Trash your harddrive?  Ok  Cancel"

---

### Post by jwkungfu on 2008-05-17
> **HotShotDJ said:**
> There are often very good reasons NOT to do that.  Defaulting to "Save" rather than "Open" would aggravate me to no end!  Firefox (and most other browsers) default to asking you what you would like to do with files that you click on.  This makes perfect sense.  The problem is that MS Windows has trained people to just click "OK" whenever a dialog box comes up without even reading what the dialog says.  A huge number of Windows users would click "OK" in a box that said "Trash your harddrive?  Ok  Cancel"

OK, but if your computer was to do as you told it to, after you changed the default it would always save the file to OPEN.
Perfect for experienced users who know exactly what they are doing.
Applications are not made to PLAY SAFE for newbies...
Newbies need the care, experienced people will always know how to adjust things to suit themselves.
:guitar::lolflag::popcorn::)

---

### Post by HotShotDJ on 2008-05-17
> **jwkungfu said:**
> OK, but if your computer was to do as you told it to, after you changed the default it would always save the file to OPEN."Save the file to OPEN" makes no sense.  The dialog asks if you want to OPEN a file (and what application you would like to use) OR would you like to save the file.  There is no option to "Save to Open."  I don't see how it could be clearer.  Save OR Open.  If you choose OPEN, then it will not be saved.  If you choose SAVE, it will not be opened.  I'm REALLY not trying to be difficult.  I just honestly don't understand the confusion here.

Hmmmm... what was the original question again?  :)

---

### Post by pbpersson on 2008-05-17
The bottom line here is that ALL computers need to be smarter.

I spend all day at work on Windows XP and it just annoys me to **NO** end when the computer does what I tell it to do instead of what I want it to do and all my work goes right down the drain and I have to start over.

:mad::mad::mad:

---

### Post by pbpersson on 2008-05-17
> **SlappyPappy said:**
> Sure........  :)

Hey.....totally off topic.....I LOVE your avatar!  :lolflag:

When I was a teenager I spent tons of time fooling with vacuum tubes.  This brings back such fond memories of my childhood.  :)

---

### Post by jwkungfu on 2008-05-17
> **HotShotDJ said:**
> "Save the file to OPEN" makes no sense.  The dialog asks if you want to OPEN a file (and what application you would like to use) OR would you like to save the file.  There is no option to "Save to Open."  I don't see how it could be clearer.  Save OR Open.  If you choose OPEN, then it will not be saved.  If you choose SAVE, it will not be opened.  I'm REALLY not trying to be difficult.  I just honestly don't understand the confusion here.

Hmmmm... what was the original question again?  :)

Oops, I think we are going in circles here...?
I tried downloading the Alternate Ubuntu upgrade to Hardy CD
The download window which had the download bar said downloading to desktop
I assumed (always dangerous) that the data was saved on my desktop... 
I had to go to work (was morning) so I guess I would be able to burn the CD later that day because the data was "saved to desktop"
I did see the message which said unable to Burn the CD (no CD in drive) but didn't worry because "the data was on my desktop"....
By default the system saved the data to a temp file which of cause is temporary and was deleted when I turned my computer off to go to work....
Great...... 699MB of data & 7hrs down the toilet....

As a newbie, I would appreciate less "new" features and more attention to making systems run in ways that assist me and not get bogged down with error messages due to applications trying to think ahead of what I am actually trying to do....

:confused::(:lolflag:

---

### Post by jwkungfu on 2008-05-17
> **pbpersson said:**
> The bottom line here is that ALL computers need to be smarter.

I spend all day at work on Windows XP and it just annoys me to **NO** end when the computer does what I tell it to do instead of what I want it to do and all my work goes right down the drain and I have to start over.

:mad::mad::mad:

HEAR HEAR !!!!!!!!!!!!!!!!!

:):popcorn::KS:lolflag:

---

### Post by bmac on 2008-05-17
Bad when the machine thinks ahead of you. :lolflag:
Prior to downloading and installing Feisty (first Ubuntu experience) I actually read the Installation Instructions... Amazing how simple it was with the documentation in hand.. Probably, not a bad idea for many other activities... You **mean** actually read the instructions. Be still....:smile:

---

### Post by ugm6hr on 2008-05-17
> **jwkungfu said:**
> Oops, I think we are going in circles here...?
I tried downloading the Alternate Ubuntu upgrade to Hardy CD
The download window which had the download bar said downloading to desktop
I assumed (always dangerous) that the data was saved on my desktop... 
I had to go to work (was morning) so I guess I would be able to burn the CD later that day because the data was "saved to desktop"
I did see the message which said unable to Burn the CD (no CD in drive) but didn't worry because "the data was on my desktop"....
By default the system saved the data to a temp file which of cause is temporary and was deleted when I turned my computer off to go to work....
Great...... 699MB of data & 7hrs down the toilet....

As a newbie, I would appreciate less "new" features and more attention to making systems run in ways that assist me and not get bogged down with error messages due to applications trying to think ahead of what I am actually trying to do....

As you say - going in cirlces...

The problem here is that you have misunderstood what Firefox has told you.  This is a bit difficult to explain in text, but I'll give it a try.

When you click (left-click) on a file that is not a regular web page, Firefox will always ask what to do with it (the first time it encounters that type of file), since it has no idea what it might be (including a virus etc), or how to open it.  You can specify what to do with file types, but you have to tell it what to do with every different type of file (e.g. .pdf, .doc, .iso etc).  Firefox can try and guess what you *might* want to do with the file, but will always check in case it is not clever enough.

This is because left-click means browse to / open rather than save (which is why when you click on web-links, the web page changes as you would expect).

If you right-click on a link, Firefox gives you *choices* as to what to do with the linked file (including Save etc).

Going back to left-clicking on an .iso file again... Firefox doesn't know what it is for certain, but thinks it is a CD image (which is what it is).  Ubuntu defaults to trying to burn a CD of an .iso image if you try to "run" an .iso image (e.g. double-click in Nautilus).  Hence, when you try to open an iso file from Firefox it offers options of: Open with CD burning application; Save to location (default desktop); sometimes it will offer option of Save with (variety of download managers).

At this point, you have obviously clicked open with CD burner - hence the temporary download, and Ubuntu's attempt to burn a CD.  When you click cancel, and reboot, the temporary files are all deleted.

I hope that explains things.

---

### Post by HotShotDJ on 2008-05-17
> **jwkungfu said:**
> The download window which had the download bar said downloading to desktop
I assumed (always dangerous) that the data was saved on my desktop...Ok. :)  That's a legitimate complaint.  Before you said that, it seemed that you were upset because Firefox failed to properly read your mind. If, at any point, it gives you the message that it is downloading something to your desktop, it should actually be downloaded to your desktop.  On that point, we agree.

---

### Post by jwkungfu on 2008-05-17
> **ugm6hr said:**
> As you say - going in cirlces...

The problem here is that you have misunderstood what Firefox has told you.  This is a bit difficult to explain in text, but I'll give it a try.

When you click (left-click) on a file that is not a regular web page, Firefox will always ask what to do with it (the first time it encounters that type of file), since it has no idea what it might be (including a virus etc), or how to open it.  You can specify what to do with file types, but you have to tell it what to do with every different type of file (e.g. .pdf, .doc, .iso etc).  Firefox can try and guess what you *might* want to do with the file, but will always check in case it is not clever enough.

This is because left-click means browse to / open rather than save (which is why when you click on web-links, the web page changes as you would expect).

If you right-click on a link, Firefox gives you *choices* as to what to do with the linked file (including Save etc).

Going back to left-clicking on an .iso file again... Firefox doesn't know what it is for certain, but thinks it is a CD image (which is what it is).  Ubuntu defaults to trying to burn a CD of an .iso image if you try to "run" an .iso image (e.g. double-click in Nautilus).  Hence, when you try to open an iso file from Firefox it offers options of: Open with CD burning application; Save to location (default desktop); sometimes it will offer option of Save with (variety of download managers).

At this point, you have obviously clicked open with CD burner - hence the temporary download, and Ubuntu's attempt to burn a CD.  When you click cancel, and reboot, the temporary files are all deleted.

I hope that explains things.

Many many thanks for such a detailed and accurate answer!!

I guess I have a problem with any machine that guesses....?
Any time, any place, any reason.... ever.....

As with any whinge it must come with an answer, otherwise is is just a whinge....

Here is the way I would like systems/applications to be...

a/ computer never guesses
b/ takes me through the process step by step
c/ asks me if I want to save the procedure to save time in the future

That way the newbie will be shown what is going on and what is required to get the application to work.
In time the newbie will learn... the computer will be set up in the way the user/newbie wants it to run thus saving time.

Obviously, developers and programmers are 100 steps in front of me in this regard, however, speaking as a newbie myself who is not technophobic, I really believe the gap between newbie and happy/confident user is still just as large as the pre-GUI days...
The only difference these days is that the ordinary person has fancy buttons to click and mess things up with... instead of looking at a terminal window and not knowing what the hell is going on....

Maybe if the programmers and developers could be made more aware of the current situation then more effort could be made in making computers do as they are told...
Although, there is no money in going backwards and changing the way things are today....

That's enough drivel from me!

:lolflag::popcorn:

---

### Post by Malac on 2008-05-18
I think the problem is a lot of developers assume the newbie knows something "obvious" because to them it *is* obvious. As a newbie it isn't, so it needs to be explained what each step is doing (this is where the forum is invaluable).
Sometimes prompts/question forms are misleading unless you already know what they mean. I am a programmer myself and am guilty of this on occasion despite my best efforts to avoid it. Some users however are guilty of just clicking that OK button without reading what the prompt is telling them in their eagerness to get done what they want.... *now*.

Sometimes repeating the process, slower, will reveal that the program has done exactly what you asked of it, you just asked it to do the wrong thing in your haste. I have done this myself clicking OK buttons saying, "yes, Yes, YES, oh come on, get on with it."

I hope you have sorted out your download issues, if not, pictures are often more use than words.
[ATTACH]70549[/ATTACH]Make sure that "Save File" is Checked then hit OK.

---

### Post by Stefanie on 2008-05-18
it's not nice when this happens, but it isn't a disaster and from now on it'll never happen again. 

when i was burning hardy to cd, i left the room for a while and when i came back i needed a terminal. i was in a hurry so i opened the first terminal i saw and i hit control C to kill the ongoing process. oops, that terminal was running nautilus so it stopped burning my cd... :lolflag: my cd was worthless and i could start all over again, but it was my own fault and i don't think i'll make the same mistake again :-)

---

### Post by jwkungfu on 2008-05-18
> **Malac said:**
> I think the problem is a lot of developers assume the newbie knows something "obvious" because to them it *is* obvious. As a newbie it isn't, so it needs to be explained what each step is doing (this is where the forum is invaluable).
Sometimes prompts/question forms are misleading unless you already know what they mean. I am a programmer myself and am guilty of this on occasion despite my best efforts to avoid it. Some users however are guilty of just clicking that OK button without reading what the prompt is telling them in their eagerness to get done what they want.... *now*.

Sometimes repeating the process, slower, will reveal that the program has done exactly what you asked of it, you just asked it to do the wrong thing in your haste. I have done this myself clicking OK buttons saying, "yes, Yes, YES, oh come on, get on with it."

I hope you have sorted out your download issues, if not, pictures are often more use than words.
[ATTACH]70549[/ATTACH]Make sure that "Save File" is Checked then hit OK.

Thank you so much for this reply!
It confirmed my theories on why computers can seem to be so difficult to use!
I am determined to learn more and hopefully get to a point where I will be able to assist other newbs and perhaps influence programmers & developers to adopt a FAR more BASIC and logical view of how to set up the GUI....

:KS

---

