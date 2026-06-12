---
title: "Newton Desktop Wiki - Testers Needed"
date: 2005-05-25
forum: Programming Talk
---

### Post by dcraven on 2005-05-25
Hi, 

**INSTALL NOTE:** Since this is a GNOME applet, you must specify the install prefix when you run the configure script. This means run configure like this:
```
./configure --prefix=/usr
```

I have no idea where this type of post should go, but Programming Talk sounded as appropriate as any. I am in the midst of writing a desktop wiki applet for GNOME, and it has come time that I need testers.

Basically, this thing is a notetaking applet like any other, but it uses an embedded Mozilla widget and wiki syntax. It could be used for similar purposes as apps like Tomboy or Notemeister. You enter your text in a simple wiki-like syntax, it renders the document in HTML.

The homepage is on SourceForge [here](http://newton.sourceforge.net)  and it has a list of known dependancies and instructions for how to install Newton on your Ubuntu box.

Please let me know if you have any issues installing and using this tarball. I'll try to get a deb made ASAP once I know that the code works on other machines than mine :)

Cheers,
~djc

---

### Post by Swab on 2005-05-25
I'm getting the following error when I try to add the applet to my panel....

The panel encountered a problem while loading "OAFIID:GNOME_NewtonApplet".

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]I'm getting the following error when I try to add the applet to my panel....

The panel encountered a problem while loading "OAFIID:GNOME_NewtonApplet".[/QUOTE]
 Any chance you didn't specify the install prefix? It's important since it's an applet that files get placed in this prefix. Basically this means that you should run the configure script like this:
```

./configure --prefix=/usr

```

I probably should make that clear in the original post.

Cheers,
~djc

---

### Post by Swab on 2005-05-25
[QUOTE=dcraven]Any chance you didn't specify the install prefix? It's important since it's an applet that files get placed in this prefix. Basically this means that you should run the configure script like this:
```

./configure --prefix=/usr

```
[/QUOTE]

I did do that yes.  Just tried again to make sure, same thing.

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]I did do that yes.  Just tried again to make sure, same thing.[/QUOTE]

Okay, well you can run it in test mode to see what the problem is. That will make it run with the applet in its own window, and any errors will appear in the terminal. Other than the applet not appearing on the panel, running it this way is functionally equivalent. Run this in a terminal:
```
/usr/libexec/newton test
```

Then you can paste the error you are getting to this thread. This error will be much more meaningful.

Thanks for the help,
~djc

---

### Post by Swab on 2005-05-25
Traceback (most recent call last):
  File "/usr/libexec/newton", line 3, in ?
    from newton import NewtonApplet
  File "/usr/lib/python2.4/site-packages/newton/NewtonApplet.py", line 20, in ?
    from NewtonGui import AppletButton
  File "/usr/lib/python2.4/site-packages/newton/NewtonGui.py", line 6, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]Traceback (most recent call last):
  File "/usr/libexec/newton", line 3, in ?
    from newton import NewtonApplet
  File "/usr/lib/python2.4/site-packages/newton/NewtonApplet.py", line 20, in ?
    from NewtonGui import AppletButton
  File "/usr/lib/python2.4/site-packages/newton/NewtonGui.py", line 6, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory[/QUOTE]

It looks like you don't have mozilla installed? That file is provided by both the "mozilla-browser" and the "mozilla-firefox" packages. I'm not sure which one Newton is using on my system.

I hadn't thought of that dependancy... To obvious I guess ;P

Cheers,
~djc

---

### Post by Swab on 2005-05-25
I have Firefox... but not the version from Ubuntu repositories...  I have 1.0.4 direct from Mozilla.

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]I have Firefox... but not the version from Ubuntu repositories...  I have 1.0.4 direct from Mozilla.[/QUOTE]

Can you do a 
```
locate libgtkembedmoz.so
```
to see if you have the file somewhere, just not in the place that Newton is looking. Probably making a symlink will suffice if that is the case. Mine is located in /usr/lib/mozilla/ (from the mozilla-browser package) and /usr/lib/mozilla-firefox (from the mozilla-firefox package).

I'm curious to see where yours is located. I'm going to have to accomodate this somehow I guess. Hmmm.

~djc

---

### Post by brickbat on 2005-05-25
It only showed up as an option in the panel after I did a

killall gnome-panel

ciao
bb

---

### Post by Swab on 2005-05-25
[QUOTE=dcraven]Can you do a 
```
locate libgtkembedmoz.so
```
to see if you have the file somewhere, just not in the place that Newton is looking. Probably making a symlink will suffice if that is the case. Mine is located in /usr/lib/mozilla/ (from the mozilla-browser package) and /usr/lib/mozilla-firefox (from the mozilla-firefox package).

I'm curious to see where yours is located. I'm going to have to accomodate this somehow I guess. Hmmm.

~djc[/QUOTE]

I don't have that file anywhere, even if i apt-get mozilla-firefox.

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]I don't have that file anywhere, even if i apt-get mozilla-firefox.[/QUOTE]
 Wha?? Any chance you didn't "updatedb" after you did your 'apt-get install mozilla-browser'? Apt is telling me that the file in question comes in those packages... If you installed the mozilla-firefox package, try running
```
ls /usr/lib/mozilla-firefox/ | grep libgtkembedmoz.so
```
and it'll be there.

~djc

---

### Post by Swab on 2005-05-25
Even installing the mozilla-browser package does not give me the file.

---

### Post by Swab on 2005-05-25
[QUOTE=dcraven]Wha?? Any chance you didn't "updatedb" after you did your 'apt-get install mozilla-browser'? Apt is telling me that the file in question comes in those packages... If you installed the mozilla-firefox package, try running
```
ls /usr/lib/mozilla-firefox/ | grep libgtkembedmoz.so
```
and it'll be there.

~djc[/QUOTE]

Yeah, that would be it!   OK, so now its working :)

---

### Post by dcraven on 2005-05-25
```

dcraven@sigma:~ $ dpkg -L mozilla-browser | grep libgtkembed
/usr/lib/mozilla/libgtkembedmoz.so
dcraven@sigma:~ $

```

If you don't get the same, then I'm confused. Anyone know if the command above can be decieving somehow?

~djc

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]Yeah, that would be it!   OK, so now its working :)[/QUOTE]
 Cool!  \\:D/ 

Thanks,
~djc

---

### Post by brickbat on 2005-05-25
Does the upload button actually do anything?  It doesn't for me.  Anyway,  it seems like a good start.  

Also, could you please put printing high up on the to do list?

ciao
bb

---

### Post by dcraven on 2005-05-25
[QUOTE=brickbat]Does the upload button actually do anything?  It doesn't for me.  Anyway,  it seems like a good start.  [/QUOTE]

When you click the button, does a file chooser dialog not open? Even if it does, that feature is still a little confusing and it's one of the features that I'm still hashing out.

What the "Upload Media" feature does, is simply make a copy of any file on your filesystem to the wiki directories. The directories that Newton stores your data in is ~/.newton/data/ for actual wiki pages, and ~/.newton/media for media files. Styles (css) are kept in ~/.newton/styles. Anyway it works like this:

You want to embed a pdf (called example.pdf) file into your wiki page. Right now it's in your home directory, but you don't want to link to it there because it might not be a permanent location for it. Instead, you can "upload" it to the wiki, and link it by putting "{{example.pdf}}" in a wiki page. Now it's in the wiki and the chances may be less that it is deleted. Clicking on your new embedded pdf link will open the pdf in gpdf or evince or whatever your default application for pdfs is.

I'm not sure how to make that feature work... I like the idea, but it is confusing. I need to think about it more. Any ideas?

[QUOTE=brickbat]
Also, could you please put printing high up on the to do list?[/QUOTE]

I think I read that printing is being worked on as part of the embedded Mozilla widget. Once that is implemented, it'll be part of Newton almost immediately. It's pretty important to me as well. I will have a look around to see if there is an interim way to print. Even if I have to export the html so that it can be printed in Firefox, it's better than nothing. I'd also like to export to things like LaTeX too. I don't think that would be a huge thing to implement.

Cheers,
~djc

---

### Post by Swab on 2005-05-25
This thing is pretty cool, really great way to take down quick notes in an organised fashion.  I can think of loads of ways I could use this.  Just a couple of questions.

If I actually want an HTML page generated from one of my wiki pages, how do i do that?  

Also it seems like I can't copy and paste from pages, is that something that will change?

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]This thing is pretty cool, really great way to take down quick notes in an organised fashion.  I can think of loads of ways I could use this.[/QUOTE]
I'm glad you might find it useful.

> 
If I actually want an HTML page generated from one of my wiki pages, how do i do that?  
Not yet possible. This will not be difficult for me to implement though. In fact it would only be a few more lines of code. But there are some considerations to be made before including this feature. For example, what about pages that the exported page links to? What about embedded media? Should these simply be ignored or should they be exported as well.. Maybe all in a tarball? I'll probably soon add the ability to save a plain ol' flat html file (with the CSS included), but these questions still need to be hashed out.

> 
Also it seems like I can't copy and paste from pages, is that something that will change?
Can you be more specific? I'm able to copy by highlighting text and paste by middle mouse button just like in any other X application. I'll probably add a proper clipboard in time if need be. I'll assume for now that I can make a right click context menu appear on the mozembed widget. If you are trying to copy/paste with the Ctrl-C/Ctrl-V idiom, that's not gonna work just yet :)

Cheers,
~djc

---

### Post by dcraven on 2005-05-25
[QUOTE=Swab]If I actually want an HTML page generated from one of my wiki pages, how do i do that?  
[/QUOTE]

Okay, I just implemented the ability to export a wiki page to an HTML file on the local filesystem. It just writes the file as is, but embeds the current CSS style in the page so that it looks like it does in Newton. The new option is in the "File" menu.

At least now you can print from Firefox or any other browser. That'll have to do until I can get the whole printing thing figured out :) I hope that will satisfy brickbat for the time being too.

The OP and the page [here](http://arker.homelinux.org/~dcraven/newton-deps.html) have been updated accordingly.

Cheers,
~djc

---

### Post by Swab on 2005-05-25
[QUOTE=dcraven]Okay, I just implemented the ability to export a wiki page to an HTML file on the local filesystem. It just writes the file as is, but embeds the current CSS style in the page so that it looks like it does in Newton. The new option is in the "File" menu.

At least now you can print from Firefox or any other browser. That'll have to do until I can get the whole printing thing figured out :) I hope that will satisfy brickbat for the time being too.

The OP and the page [here](http://arker.homelinux.org/~dcraven/newton-deps.html) have been updated accordingly. I'll also attach the new tarball to this post.

Cheers,
~djc[/QUOTE]

Am I going to lose all my pages if I install the new version?  How can I backup first?  Oh, and I didn't realise that one could highlight and middle click to copy!

Edit: Cool it kept my pages, except it reverted to the default NewtonHome page.

Edit again:  And the export function works perfectly, very nice!

---

### Post by dcraven on 2005-05-26
[QUOTE=Swab]Edit: Cool it kept my pages, except it reverted to the default NewtonHome page.
[/QUOTE]
Yikes! That wasn't supposed to happen.. I'll have a look. Thanks for the heads up!

~djc

**EDIT:** I think this is fixed now. The tarball as SF and in the original post have been refreshed to reflect the changes.

---

### Post by brickbat on 2005-05-26
This probably seems petty but I'll leave that decision to you.

The apple icon is smaller than all of the others.  It's not optimal but I can accept it.  However, the outline doesn't takes up the full space that is available.

Here is a screenshot.

ciao
bb

---

### Post by dcraven on 2005-05-26
[QUOTE=brickbat]
The apple icon is smaller than all of the others.  It's not optimal but I can accept it.  However, the outline doesn't takes up the full space that is available.
[/QUOTE]
Yes that is a problem. Right now I have it scaling to 16x16 which of course looks fine on my panel so I never noticed. I'll look into setting the size based on the depth of the panel. Thanks.

~djc

**EDIT:** I think this is fixed now. I'm not sure I implemented it properly, but it now seems to mimic the behavior of the volume applet. The tarball at SF and in the original post have been updated to reflect the changes.

---

### Post by rjs on 2005-05-27
This is a freaking awesome idea. Unfortunatley the link to the tarball doesnt seem to be working for me atm, but ill try again later.

Just a question - the apple icon and the name newton; was that mac inspired? If not what was the inspiration?

is there an edit history?
if not that would be my feature request.

btw, what lang is it written in, and where can we download the source?

paz y amor,
-rjs.

---

### Post by Swab on 2005-05-27
[QUOTE=rjs]
Just a question - the apple icon and the name newton; was that mac inspired? If not what was the inspiration?
[/QUOTE]

We can only assume he was minding his own business and it just hit him :)

---

### Post by rjs on 2005-05-27
rofl

---

### Post by dcraven on 2005-05-27
> **rjs]This is a freaking awesome idea. Unfortunatley the link to the tarball doesnt seem to be working for me atm, but ill try again later.[/QUOTE]
Any luck with this? The tarball is hosted at sourceforge AND attached to the original post in this thread. One of the have to work.

> 
Just a question - the apple icon and the name newton said:**
> 
It was named after Sir Isaac actually. My server is also named Newton. And we all know the story of Newton and the apple. :)

[QUOTE]
is there an edit history?
if not that would be my feature request.
There is no edit history at the moment. I didn't think an edit history would be of much use given that the wiki is not shared. This feature is useful when there are several people editing the wiki so that you can see the changes the others have done, but when it's one person?

[QUOTE]
btw, what lang is it written in, and where can we download the source?
The language is Python, and the tarball **is** the source.

I hope you like it,
~djc

---

### Post by rjs on 2005-05-28
[QUOTE=dcraven]
There is no edit history at the moment. I didn't think an edit history would be of much use given that the wiki is not shared. This feature is useful when there are several people editing the wiki so that you can see the changes the others have done, but when it's one person?
[/QUOTE]

the single feature i use the most in gimp is "undo". The feature i use the most in firefox is "back". A full edit history is going to add a whole heap to the size of the database, but being able to look up stuff ive done in the past is so very, very useful.

paz y amor,
-rjs.

ps im just about to try and get the tarball now, ill tell you how it goes

---

### Post by rjs on 2005-05-29
well, i just got it, and it works a charm. Two minor things. Perhaps the main page should be [[home]] rather than [[NewtonHome]], just cause its easier and quicker to write; but then again, one probably won't be linking to the home page that often.
And also about the applet pic; is it possible to make it's background transperant?

Otherwise an awesome idea well executed.

paz y amor,
-rjs.

---

### Post by rjs on 2005-05-29
My first bug report:

my wiki syntax is this:
```

* set up
** ''sudo apt-get build-essential apt-file''
** ''sudo apt-file update'' (proxy probs -> not necessary)
** ''sudo chown username /usr/local/src''
** ''u+rwx /usr/local/src''
* main
** download tar ball to ''usr/local/src''
** extract (unzip):
*** for tar.gz ''tar xzvf tarballname.tar.gz''
*** for tar.bz2 ''tar xjvf tarballname.tar.bz2''
*** OR just click on it and use the gui extracter
** check website for a dependices list and ''apt-get'' them
** ''cd /usr/local/src/foo'' foo is the subdirectory that the program was extracted to.
** ''./configure'' 
*** if this yeilds ''blah blah config.status: creating Makefile'' go to the next step
*** if not then you are in //dependency hell//
**** directly above the line that says ''configure: error: Library requirements (gobbletygook) not met, blah blah blah'' there will be the names of files it can't find.
**** ''apt-file search missingfilename'' (need to set up proxy for ''apt-file'' first. Dont know how yet)
**** this will tell you what the ubuntu package name(s) are. ''apt-get'' these.
**** go back to ''./configure'' and hope it works
** ''make''
** ''sudo make install''

(more info at [[[http://www.ubuntulinux.org/wiki/CompilingEasyHowTo]]](http://www.ubuntulinux.org/wiki/CompilingEasyHowTo]]))

```

but if you look at the screenshot below, "make" the second-last dotpoint acts like it is *** (3) rather than ** (2)

if i insert a blank *** (3) before it, then it acts as a ** (2) again. So it seems that unordered (and possibly ordered, i dont know) list cant change thier level of indentation by more than one * per line.

paz y amor,
-rjs.

---

### Post by dcraven on 2005-05-29
> Two minor things. Perhaps the main page should be [[home]] rather than [[NewtonHome]], just cause its easier and quicker to write; but then again, one probably won't be linking to the home page that often.
Yeah, I assume people won't be linking the home page that often so it wouldn't be a big deal. I'll ponder that.

> And also about the applet pic; is it possible to make it's background transperant?
Good catch. Damn me and my default panel settings!! heh. Hmm.. At the moment I'm just creating an icon from the svg on the fly. I do that because I assume it scales better. There is probably a way I can tell it to make the background transparent, and I'll have a look at that. Otherwise there is always the option to use a png with a transparent background. I'll see which works better.

> if i insert a blank *** (3) before it, then it acts as a ** (2) again. So it seems that unordered (and possibly ordered, i dont know) list cant change thier level of indentation by more than one * per line.
Definately a bug, and your assessment is correct. The code assumes a one level decrement in list levels. I'll fix that right now. Silly me :)

Your feedback and bug reports are appreciated,
~djc

---

### Post by dcraven on 2005-05-29
Okay, the ordered/unordered list code is fixed now (I think). The tarball attached to the original post in this thread reflects the changes, but **not** the tarball at Sourceforge just yet. 

Before you install this new tarball, please backup your wiki pages like this "tar cvzf newton_backup.tar.gz ~/.newton/" because there was a report earlier in the thread of the NewtonHome page being overwritten. I'm confident that this has been fixed, but I don't want you to lose any data. Let me know if the upgrade works without incident.

I'm still looking into the transparent applet bit. I'm now convinced that the svg to pixmap conversion **is** in fact keeping the image's background transparent, and that the grey area you see is actually the toggle button. I used a toggle button for usability reasons so that it was apparent that the window was open or closed at any time. In hindsight, I think I'll probably lose the toggle button and just use an image. I don't think there is a need to know whether the window is open or not, and this might just solve the transparency issue. I do want to get this fixed as I know how prettiness is important to most users. 

Cheers,
~djc

---

### Post by rjs on 2005-05-29
hmmm... i think it might be useful to have it as a toogle button (i hadn't realised it was one) so that it is always open and ready for one to scribble something in. With gaim and rhythymbox they have normal buttons for starting up and when it is open it puts a little toggle button in the "Notification area", so that might be a stone that kills two birds.

paz y amor,
-rjs.

btw, what is does cvzf (or xvzf or xjvf) mean? who came up with commands which are so damn unmemorable?

---

### Post by rjs on 2005-05-29
The prob doesnt seem to have been fixed for me, but then again, i wouldnt be suprised if i somehow managed to screw up the install.

I was kind of expecting that at some point it would ask me if i was sure i wanted to overwrite a file with the same name, but it didnt.

On the upside i didnt lose any data, including that on [[NewtonHome]]

paz y amor,
-rjs.

---

### Post by dcraven on 2005-05-29
> hmmm... i think it might be useful to have it as a toogle button (i hadn't realised it was one) so that it is always open and ready for one to scribble something in. With gaim and rhythymbox they have normal buttons for starting up and when it is open it puts a little toggle button in the "Notification area", so that might be a stone that kills two birds.
As far as I'm concerned (and the GNOME HIG), both of those programs abuse the notification area. That is why I made an applet intead. The alternative to the toggle button would still be visible on the panel, but more like the volume control applet. Just a flat button with no visible feedback. Right now with the toggle button there is a visible depression when the window is open, otherwise the window is closed.

> btw, what is does cvzf (or xvzf or xjvf) mean? who came up with commands which are so damn unmemorable?
See "man tar" for information about those and the many more switches available for the tar command.

> The prob doesnt seem to have been fixed for me, but then again, i wouldnt be suprised if i somehow managed to screw up the install.
Double check your install. I don't claim that it's bugfree now, but it does work with the data you pasted in the thread.

> I was kind of expecting that at some point it would ask me if i was sure i wanted to overwrite a file with the same name, but it didnt.

On the upside i didnt lose any data, including that on [[NewtonHome]]
No, I never want to overwrite anyone's data. Or even ask to do so. The only thing I'm not sure of is if I will have to overwrite the NewtonSyntax page as it will expand from release to release, and need to be updated. I still don't know if it is safe to do or not. Maybe a dialog asking for permission like you suggest is a good idea in that case.

Cheers,
~djc

---

### Post by brickbat on 2005-05-30
Works perfect.  Thanks.

[QUOTE=dcraven]Yes that is a problem. Right now I have it scaling to 16x16 which of course looks fine on my panel so I never noticed. I'll look into setting the size based on the depth of the panel. Thanks.

~djc

**EDIT:** I think this is fixed now. I'm not sure I implemented it properly, but it now seems to mimic the behavior of the volume applet. The tarball at SF and in the original post have been updated to reflect the changes.[/QUOTE]

---

### Post by brickbat on 2005-05-31
Hi,

Instead of the "upload media" button, Is it possible to add a "media browser" button that lets add/remove uploaded files to the system.

ciao
bb

---

### Post by dcraven on 2005-05-31
There is a new release available for download [here](https://sourceforge.net/projects/newton/) and the official website is now finally online [here](http://newton.sourceforge.net). The website is nothing too fancy, but it'll do for now. I didn't want to spend my whole day on it :) . The new tarball is also attached to the original post of this thread.

New in this release is a search/find feature. Type in your search word and Newton will show all notes that contain that word. From there, click on one of the resulting links and view that page with all instances of your search word highlighted. Also new is a formatting toolbar found in the edit screen. This is an attempt to make formatting simpler just like the toolbar buttons available when editing/writing forum posts. One click insertion of locale-friendly date/time is also available. The new release includes everything that the old tarball included too, of course, including the scaling panel applet etc...

New screenshots are available on the website that show off the new features. I'm not sure if the search feature is good from a usability standpoint or not. It's the best I could think of (ie. the entry widget not always visible). 

**IMPORTANT:** The default CSS styles that came with Newton will be overwritten. This is necessary to facilitate the new features (ie. things like highlighted text). If you have made changes to these styles, I suggest you rename or move the style files to a new name, otherwise you will lose your changes. Renaming the files to "whatever.css" will work, and your custome style will still appear in the preferences dialog as long as it appears in the ~/.newton/styles/ directory.

Your feedback on this and anything else is very welcomed.

Cheers,
~djc

---

### Post by dcraven on 2005-05-31
[QUOTE=brickbat]Instead of the "upload media" button, Is it possible to add a "media browser" button that lets add/remove uploaded files to the system.
[/QUOTE]
I agree that something needs to be done with the upload media thing... What if a nautilus window opened directly at your media directory upon clicking that button. That seems like a reasonable solution maybe. Sounds better than me having to basically implement spatial nautilus in python just for this program..haha The file previews in nautilus kick arse too so it would be cool to take advantage of that.

Is that sort of what you had in mind? Basically a spatial nautilus-like media browser?

Cheers,
~djc

---

### Post by brickbat on 2005-05-31
Yup, thats what I had in mind.

---

### Post by rjs on 2005-05-31
*lightbulb*

i just worked out why the upgrade didnt work last time; i have to remove newton from the panel, and then put it back on for it to work. Ah, now i feel stupid...

paz y amor,
-rjs.

---

### Post by dcraven on 2005-05-31
[QUOTE=brickbat]Yup, thats what I had in mind.[/QUOTE]
Try the tarball attached to the original post of this thread. Maybe that's better.

I have been thinking though, maybe it would be better to just toss this whole "media directory" business out the window and allow the user to link to files anywhere on the local filesystem instead, for example [[/home/brickbat/Documents/myfile.pdf|Click me]]. They could manage their own media files. This raises several points:
[list]
[*]Right now Newton depends on the user having nautilus installed. Although this is likely, it will cause problems when I start supporting other desktops outside of GNOME.
[*]The user would be responsible for their own media files as they could be anywhere on the filesystem, including a location that eventually gets deleted. In this case, the link would turn red to notify the user that it is a dead link.
[*]The way it is now, it is likely that there are two copies of the same file on the user's drive.
[/list] 

I'm starting to lean towards getting rid of this idea altogether now. It's confusing and quite likely unessecary. Thoughts?

---

### Post by Swab on 2005-06-01
[QUOTE=dcraven]Try the tarball attached to the original post of this thread. Maybe that's better.

I have been thinking though, maybe it would be better to just toss this whole "media directory" business out the window and allow the user to link to files anywhere on the local filesystem instead, for example [[/home/brickbat/Documents/myfile.pdf|Click me]]. They could manage their own media files. This raises several points:
[list]
[*]Right now Newton depends on the user having nautilus installed. Although this is likely, it will cause problems when I start supporting other desktops outside of GNOME.
[*]The user would be responsible for their own media files as they could be anywhere on the filesystem, including a location that eventually gets deleted. In this case, the link would turn red to notify the user that it is a dead link.
[*]The way it is now, it is likely that there are two copies of the same file on the user's drive.
[/list] 

I'm starting to lean towards getting rid of this idea altogether now. It's confusing and quite likely unessecary. Thoughts?[/QUOTE]


I would definitely prefer if I could just link to files on the local filesystem. 

Also just thought I'd let you know that the NewtonHome page was overwritten again when upgrading to 0.0.7

---

### Post by brickbat on 2005-06-01
Hi. For some reason it is not starting a new paragraph properly.  See the screenshots.

ciao
bb

---

### Post by dcraven on 2005-06-01
[QUOTE=Swab]I would definitely prefer if I could just link to files on the local filesystem.[/QUOTE]
That's probably exactly what I'll do.

> Also just thought I'd let you know that the NewtonHome page was overwritten again when upgrading to 0.0.7
Dammit.. Sorry about that :(. I'll go hunting for that bug right now. It's probably something silly.

[QUOTE=brickbat]Hi. For some reason it is not starting a new paragraph properly.  See the screenshots.[/QUOTE]
Well that's weird. I can't reproduce that even when using the same data. See attached.

---

### Post by rjs on 2005-06-01
[QUOTE=Swab]I would definitely prefer if I could just link to files on the local filesystem. 

Also just thought I'd let you know that the NewtonHome page was overwritten again when upgrading to 0.0.7[/QUOTE]

It didnt overwrite mine...


paz y amor,
-rjs.

ps the search function is quite nifty.

---

### Post by dcraven on 2005-06-01
[QUOTE=Swab]Also just thought I'd let you know that the NewtonHome page was overwritten again when upgrading to 0.0.7[/QUOTE]
I can't reproduce this either. The NewtonHome page (according to my intentions) is only supposed to be written using the default text if the page does not exist when the program is run. This page is in the file ~/.newton/data/NewtonHome. So if for some reason that file doesn't exist, it is recreated. But in that case it's not being overwritten since it never existed in the first place.. haha.

[QUOTE=rjs]ps the search function is quite nifty.[/QUOTE]
Glad you like it. I'm hoping the highlights will suffice. I'm unaware of a way to scroll to the occurances of the search word automatically given that I'm using the gtkmozembed widget. I don't think there is any concept of position. 

Just out of curiousity, rjs and swab, are you seeing any paragraph formatting issues like the ones brickbat is seeing? I'm having no luck reproducing it here, but the paragraph code is a bit of a #%^@* admittedly so there is no doubt a bug or two :)

Also I've just ripped out the silly "media directory" stuff. I think I'm just going to let links go to anywhere on the filesystem. That's less confusing. If the file being linked to does not exist then the link will be red, and an appropriate dialog is displayed when it's clicked. I just want to do more testing first, then I'll upload it to the thread.

Thanks again for the comments guys,
~djc

---

### Post by dcraven on 2005-06-02
Okay, I'm going to upload the new version (0.0.8-test) to the original post in this thread now. Some changes include the loss of the "Upload/Browse" media crap and all references to a media directory. Instead, you can link to any file on the local filesystem.

The implementation of embedding images is also now ready for testing. Users can embed images anywhere, with a variety of positions (float-left, float-right, and center) and scale to any size they desire. Both local and remote (Internet) images are supported. Also an "Insert Image" edit tool has been added to the edit screen if you need help. It will need some testing as well. The dialog itself also needs some layout/organizational work, but I'm no usability expert :P

The NewtonHome and NewtonSyntax pages are both updated to reflect the newer features, but if you already have a NewtonHome (if you are upgrading) you will only get a new NewtonSyntax page. The NewtonSyntax has to be updated on everyone's install obviously because they have to be able to see the new syntax and how to use it.

On a side note, Newton has gotten some pretty nice ratings and a few encouraging comments at [Gnome-Files](http://www.gnome-files.com). If any of you are among those who contributed to this, many thanks!

Comments and bug reports are, as always, appreciated.
~djc

---

### Post by Artis on 2005-06-12
Why doesn't Newton follow the Gnome setting for monospaced font?

---

### Post by dcraven on 2005-06-15
[QUOTE=Artis]Why doesn't Newton follow the Gnome setting for monospaced font?[/QUOTE]
 Could you be more specific? Do you mean the monospaced font that you see when viewing the Wiki page or the one you see when editing the page?

The editing font is set to "monospace 10" in the code, and the rendered font (in the gecko viewer) is probably whatever it is set at in Mozilla or Firefox. I'm curious now.

~djc

---

### Post by Artis on 2005-06-16
[QUOTE=dcraven]Could you be more specific? Do you mean the monospaced font that you see when viewing the Wiki page or the one you see when editing the page?[/QUOTE]Both.

> 
The editing font is set to "monospace 10" in the code, and the rendered font (in the gecko viewer) is probably whatever it is set at in Mozilla or Firefox."Monospace 10" seems to be what I'm seeing, I tried changing both Firefox and Mozilla fonts but it does not seem to make a difference.

---

### Post by dcraven on 2005-06-17
[QUOTE=Artis]Both.

"Monospace 10" seems to be what I'm seeing, I tried changing both Firefox and Mozilla fonts but it does not seem to make a difference.[/QUOTE]
 Okay, well I suspect then that the rendered font (in the Gecko widget) is set in the CSS styles in ~/.newton/styles/ then. But be careful editing those as upgrading to a new version will overwrite your changes. You can copy one of the styles to a new name though and it should still appear in the Newton preferences as long as it is in that directory.

As for the editing font, yes, it is explicitly set to Monospace 10. I'm not exactly sure how to get the system monospaced font at the moment, but I've made a note to find out. That would be a much better thing to do than what I do at the moment.

Edit: Maybe you are saying that you don't want a monospaced font when you edit? I'm having trouble deciphering what you are asking to be honest. I thought that editing was awkward with the default variable width font, so I made it monospaced which I thought was better. This could be an option if that is what you are saying though.

Cheers,
~djc

---

### Post by Artis on 2005-06-17
[QUOTE=dcraven]Okay, well I suspect then that the rendered font (in the Gecko widget) is set in the CSS styles in ~/.newton/styles/ then.[/QUOTE]Seems to work. Using system settings would be much better of course. :neutral:

[QUOTE=dcraven]Maybe you are saying that you don't want a monospaced font when you edit?[/QUOTE]No, just a readable monospaced font. :) Monospace 10 is just too small. I also like a consistent look in all applications.

Edit: BTW, in the CSS you have "font:" instead of "font-family:" in "pre.pre", "pre.code" and "code".

---

### Post by dcraven on 2005-06-17
[QUOTE=Artis]BTW, in the CSS you have "font:" instead of "font-family:" in "pre.pre", "pre.code" and "code".[/QUOTE]
Fixed, fixed, and fixed. Thanks for the tip. I'm still learning CSS ;)

See next release,
~djc

---

### Post by dcraven on 2005-06-18
Post edited out because topic is now irrelevant... ;)

~djc

---

### Post by timczer on 2005-06-21
I cannot get imbedded files to open when clicked on.  I can get a picture file to open, some spreadsheet files, but not all.  I can't get any word type files to open (either saved as .doc, or openoffice extensions).  It doesn't appear that where the file is saved makes a difference, as I can open a .xls file from a folder but not a text file from the same folder.  The files are listed in grey, so they are known to be there.  What am I doing wrong?

---

### Post by dcraven on 2005-06-22
[QUOTE=timczer]I cannot get imbedded files to open when clicked on.  I can get a picture file to open, some spreadsheet files, but not all.  I can't get any word type files to open (either saved as .doc, or openoffice extensions).  It doesn't appear that where the file is saved makes a difference, as I can open a .xls file from a folder but not a text file from the same folder.  The files are listed in grey, so they are known to be there.  What am I doing wrong?[/QUOTE]
 Can you open these mystery files by clicking on them in nautilus? Newton uses the "gnome-open" command, which I thought always opened the document with the registered GNOME program for that mime type. How it does this, I'm not quite sure.

When Newton can't open one of your files, try opening that file in a terminal with "gnome-open filename" and see what happens. If it opens fine, then there is something wrong with Newton. Otherwise, hopefully you will get a meaningful error message.

I have not encountered this problem yet, but I did wonder if/when it would come up :)

Cheers,
~djc

---

### Post by timczer on 2005-06-22
I found the issue with opening files.  It was the issue of the file names, spaces, punctuation etc.  A Windows habit of just naming things using spaces and punctuation.  Lot's of excel and word files emailed to me from work are the same thing.  Once I renamed them with no extra stuff it worked fine.

---

### Post by dcraven on 2005-06-23
[QUOTE=timczer]I found the issue with opening files.  It was the issue of the file names, spaces, punctuation etc.  A Windows habit of just naming things using spaces and punctuation.  Lot's of excel and word files emailed to me from work are the same thing.  Once I renamed them with no extra stuff it worked fine.[/QUOTE]
 Thanks for the tip, I'll put the filenames in quotes and it should work fine then.

---

### Post by rjs on 2005-06-28
G'day,

I just moved over to the dark side (KDE) and still want to be able to use newton, since ive become a bit of a newton junkie. Is there anyway of running a gnome applet in KDE? If there is no easy way, what would i have to do/learn to make it work?

Thanks heaps,
-rjs.

---

### Post by dcraven on 2005-06-29
[QUOTE=rjs]G'day,

I just moved over to the dark side (KDE) and still want to be able to use newton, since ive become a bit of a newton junkie. Is there anyway of running a gnome applet in KDE? If there is no easy way, what would i have to do/learn to make it work?

Thanks heaps,
-rjs.[/QUOTE]
 I don't think there is a way yet, but I'm not certain. After I finish adding category support (almost there), the next major feature will be support for other desktops. Basically, when you install Newton, you will be able to run it either by menus or by adding the applet to your GNOME panel. If run from the menu, there will be no applet, but it will have the option of a tray icon. This option will work in other environments like KDE and xfce in theory.

I guess this means I should hurry up ;). I should have implemented this feature first maybe.. In the meantime, you should be able to run it (assuming you still have the GNOME libs installed) by typing "newton test" in a terminal or by creating a launcher  that executes that command. When run like that, you'll have the applet floating in it's own tiny little window which is probably a drag, but at leat it runs for now ;P

Cheers,
~djc

---

### Post by rjs on 2005-06-29
thanks, you're a legend

paz y amor
-rjs.

---

### Post by dcraven on 2005-08-16
Just a couple of things to add to the thread:

[list=1]
[*]The Newton SVN is now open to the public instructions to follow.
[*]Newton is available for translation via the Rosetta project.
[/list] 

To get the latest development code, install Subversion and type:
```
svn co http://arker.homelinux.org/Pub/newton/trunk newton
```
This will download the svn version to a directory called "newton" at your current location.

Newton's Launchpad Overview page is located [here](https://launchpad.net/products/newton) if you would like to translate the program to your native language, click on the "    *   Template "newton" in Newton HEAD (development)" link on the left side of that page.

Cheers,
~djc

---

### Post by Galoot on 2005-08-31
I'm loving this! A small and simple desktop wiki is something I've wanted for a long time, and so far I've not run into any problems. Thanks for writing it.

</useless bug report>

---

### Post by dcraven on 2005-08-31
[QUOTE=Galoot]I'm loving this! A small and simple desktop wiki is something I've wanted for a long time, and so far I've not run into any problems. Thanks for writing it.
[/QUOTE]

Glad you like it :P

I just noticed in the post prior to yours that I had not updated the location of the new  svn repository for Newton. So in case that is what you are using, you should probably update with the new repository. If you got the location from Newton's homepage, then you are golden.

I edited the post above to reflect the new location. I probably should also mention here that there is a Newton Trac page [here](http://arker.homelinux.org/projects/newton) that you can file bugs and requests at.

Cheers,
~djc

---

### Post by Galoot on 2005-09-01
[QUOTE=dcraven]I just noticed in the post prior to yours that I had not updated the location of the new  svn repository for Newton. So in case that is what you are using, you should probably update with the new repository. If you got the location from Newton's homepage, then you are golden.[/QUOTE]I'm not quite confident enough in my Linux ability yet to start with svn. Maybe in another few months... I used the [newton_0.0.9-2_all.deb](http://prdownloads.sourceforge.net/newton/newton_0.0.9-2_all.deb?download) file from sourceforge, which I thank you for providing.> I probably should also mention here that there is a Newton Trac page [here](http://arker.homelinux.org/projects/newton) that you can file bugs and requests at.This I'll make use of. Hmmm. I wonder if I can find a tool somewhere to note these things down... :-k

---

### Post by dcraven on 2005-09-02
Just thought I'd post an update here for anyone that wants to use Newton and who isn't using GNOME (eg. rjs).

I've finally gotten off my lazy behind and made Newton work as a stand-alone application if you so choose. The svn version has both an entry in the Applet menu and an entry in the regular applications menu (under Accessories for now..). This means that it should work in other menus like KDE etc... In theory. Essentially, now you have a choice between running Newton as an applet or not (GNOME libs still required).

Testers and reports are appreciated. I still primarily use it as an applet, but I think I've made all of the applet code apply **only** to the applet version. If you are using it as a regular app, please let me know if you find anything strange.

Cheers,
~djc

---

### Post by ardchoille on 2005-12-16
post edited out due to being irrelevant now.

Awesome work on Newton!!! Thank you for writing it.

---

### Post by ardchoille on 2005-12-16
OK, I just downloaded NEwton from [https://sourceforge.net/project/showfiles.php?group_id=131243](https://sourceforge.net/project/showfiles.php?group_id=131243)

I installed it with

```

sudo dpkg -i newton_0.0.9-2_all.deb

```

There is no menu entry in the gnome menus, so I ran it from a term and got no error. However, I did not get my prompt back and CTRL+C didn't do anything. Newton does not start up. 

How do I run/use Newton?

---

### Post by ardchoille on 2005-12-16
[QUOTE=dcraven]Just thought I'd post an update here for anyone that wants to use Newton and who isn't using GNOME (eg. rjs).

I've finally gotten off my lazy behind and made Newton work as a stand-alone application if you so choose. The svn version has both an entry in the Applet menu and an entry in the regular applications menu (under Accessories for now..). This means that it should work in other menus like KDE etc... In theory. Essentially, now you have a choice between running Newton as an applet or not (GNOME libs still required).

Testers and reports are appreciated. I still primarily use it as an applet, but I think I've made all of the applet code apply **only** to the applet version. If you are using it as a regular app, please let me know if you find anything strange.

Cheers,
~djc[/QUOTE]
OK, it seems I can run NEwton as a panel applet and all is well. However, I dislike panel applets and prefer to not have them at all. Newton will not run as a full app.

How do I make Newton work as a stand-alone application? Is the svn version the only one able to do this at this time?

---

### Post by Gandalf on 2005-12-17
Hello

the proggy is very very cool and usefull i like it and use it, it's actualy Cool :D anyway I have found a bug i though maybe informing you here, actuallt when i try to type xml code inside a code (two space before the code) it will still not be pasted, so i had to replace < with &lt; and > with &gt; manually

anyway Thx for this program i like it :D

---

### Post by dcraven on 2005-12-18
> **Gandalf]the proggy is very very cool and usefull i like it and use it, it's actualy Cool :D anyway I have found a bug i though maybe informing you here, actuallt when i try to type xml code inside a code (two space before the code) it will still not be pasted, so i had to replace < with &lt said:**
> 
This has also been fixed in the SVN version. I'd suggest using it if possible.
[quote=Gandalf]anyway Thx for this program i like it :D
I'm glad you like it, and you're welcome. :)

ardchoille, have you had any luck with the SVN version?

~djc

---

### Post by rpaller on 2005-12-20
I am using Newton in 5.04 and it is working as expected.

---

### Post by mondi0924 on 2006-01-03
cool app, have one comment though. I stored a chat session and the carriage returns weren't included its tedious for me to insert a new line on every chat message. is there a way for me to copy raw text and paste it in without losing text formatting?

---

### Post by dcraven on 2006-01-03
[QUOTE=mondi0924]cool app, have one comment though. I stored a chat session and the carriage returns weren't included its tedious for me to insert a new line on every chat message. is there a way for me to copy raw text and paste it in without losing text formatting?[/QUOTE]
I think in version 0.0.9, raw text could be entered by starting each line with two spaces. This wasn't all that practical for copy/paste situations. In the SVN version, raw text can be framed with '%%%'. So for example:
```

%%%
This is raw text.
%%%
```
When entered in this manner, text formatting will not be lost.

Cheers,
~djc

---

### Post by mondi0924 on 2006-01-07
I've recently upgraded to dapper. unfortunately newton is one of the apps not running. whenever I start it up it runs fine on the taskbar but when I click on the icon to pull up the main window the program crashes.

---

### Post by mrmcctt on 2006-01-24
Ok.  I watched the flash demo on the source forge site and the one thing I have been unable to do is create an new category.

I installed the *.deb package 0.0.9.2 in Breezy using dpkg -i *.deb package.  I can create new pages but either I can't or don't know how to create new categories.

Is this a bug or a screw up on my part?  From the demo it appeared that all you had to do was right click on the tree on the left to get a list allowing you to create a new category and then name it.  The only options I get are 'Delete Page', 'Rename Page' and 'Export".

Thanks

Edit:  I can create new pages, just not new categories.

---

### Post by dcraven on 2006-01-24
[QUOTE=mrmcctt]Ok.  I watched the flash demo on the source forge site and the one thing I have been unable to do is create an new category.

I installed the *.deb package 0.0.9.2 in Breezy using dpkg -i *.deb package.  I can create new pages but either I can't or don't know how to create new categories.

Is this a bug or a screw up on my part?  From the demo it appeared that all you had to do was right click on the tree on the left to get a list allowing you to create a new category and then name it.  The only options I get are 'Delete Page', 'Rename Page' and 'Export".

Thanks

Edit:  I can create new pages, just not new categories.[/QUOTE]
Not a screw up, just a misunderstanding. The flash demo you watched was a demonstration of the development code from the Subversion repo. Version 0.0.9 has no support for categories at all. Instructions for getting and installing the Subversion development code is available from the Newton homepage.

Cheers,
~djc

---

### Post by dcraven on 2006-01-24
[QUOTE=mondi0924]I've recently upgraded to dapper. unfortunately newton is one of the apps not running. whenever I start it up it runs fine on the taskbar but when I click on the icon to pull up the main window the program crashes.[/QUOTE]
Same. The new Firefox seems to break the embedded widget used in Newton. I'm not sure if the bug is in Firefox itself, or if it is in the Python wrappers. Help in this arena would be appreciated. 

Has anyone had any luck using Newton with Dapper?

Cheers,
~djc

---

### Post by mrmcctt on 2006-01-25
[QUOTE=dcraven]Not a screw up, just a misunderstanding. The flash demo you watched was a demonstration of the development code from the Subversion repo. Version 0.0.9 has no support for categories at all. Instructions for getting and installing the Subversion development code is available from the Newton homepage.

Cheers,
~djc[/QUOTE]

Thanks much.  I got the svn installed painlessly and everything is so far working as I had hoped it would.

Very nice program.

---

### Post by dpm on 2006-04-24
[quote=mrmcctt]Thanks much.  I got the svn installed painlessly and everything is so far working as I had hoped it would.

Very nice program.[/quote] 
Unfortunately here it didn't work.

Using Dapper, uninstalled the previous Breezy package with synaptic, downloaded the last newton revision from svn and followed the instructions from the newton page (although I had to download config.status and config.sub and include the appropriate m4 macros to the aclocal file as instructed by the warnings when running autogen the first time):

```
./autogen.sh --prefix=/usr 
sudo make install
``` 
Everything compiled and installed without trouble. However, when trying to start newton, I get the cryptic "The Application "Newton" has quit unexpectedly" message.

Bummer.

---

### Post by mrmcctt on 2006-04-24
Well...........

I get to go through most of the Breezy setup again myself, including Newton.

My laptop had to go in for some warranty work and they re-imaged the hard drive and wiped everything to include partitions out.  Funny thing was, none of the work involved the hard drive.

Oh well.........May give me a reason to try Dapper again.  Tried the LiveCD on two systems and got a panic both times.

---

### Post by toothpaste on 2006-05-16
[QUOTE=dcraven]Same. The new Firefox seems to break the embedded widget used in Newton. I'm not sure if the bug is in Firefox itself, or if it is in the Python wrappers. Help in this arena would be appreciated. 

Has anyone had any luck using Newton with Dapper?

Cheers,
~djc[/QUOTE]

Guys, this is an awesome piece of software which I really miss since I upgraded to dapper. Same crash as everyone else is seeing on dapper. I went through the newton tickets and this issue is up there but no solution AFAIK. 

I must congratulate the author. I used to use tomboy but shifted to newton since it's so much better but unfortunately now i'm back on tomboy. 

cheers,
amitb

---

### Post by dpm on 2006-05-16
[quote=toothpaste]Guys, this is an awesome piece of software which I really miss since I upgraded to dapper. Same crash as everyone else is seeing on dapper. I went through the newton tickets and this issue is up there but no solution AFAIK. 

I must congratulate the author. I used to use tomboy but shifted to newton since it's so much better but unfortunately now i'm back on tomboy. 

cheers,
amitb[/quote] 
You don't know how well I understand you, mate. I've been missing Newton ever since I installed Dapper. I had really got used to it for all my notes, and yes, it is so much better than Tomboy!

The problem seems to be related to this bug in Firefox,

[https://launchpad.net/products/firefox/+bug/26436]("https://launchpad.net/products/firefox/+bug/26436")

i.e. with gtkmozembed, which Newton uses.

It's been there for some time now, and unless it is fixed before Dapper release, I think we'll have to wait 6 months for the Dapper+1 release to get an official fix...

---

### Post by toothpaste on 2006-05-23
[QUOTE=desp]
It's been there for some time now, and unless it is fixed before Dapper release, I think we'll have to wait 6 months for the Dapper+1 release to get an official fix...[/QUOTE]

Such a shame  - Meanwhile, any suggestions for a newton replacement besides tomboy/gjots ? 

Cheers,
Amitb

---

### Post by dpm on 2006-05-23
[quote=toothpaste]Such a shame  - Meanwhile, any suggestions for a newton replacement besides tomboy/gjots ? 

Cheers,
Amitb[/quote] 
Someone on the newton user lists suggested a program called **zim.** It is on the *universe* repos and it is apparently not as nice as Newton, but I haven't tried it myself.

Or...

If you are feeling adventurous you could try this shameless hack to the Newton sources 8);

[http://sourceforge.net/mailarchive/forum.php?thread_id=10461661&forum_id=45438]("http://sourceforge.net/mailarchive/forum.php?thread_id=10461661&forum_id=45438")

Please read the three previous posts at 

[http://sourceforge.net/mailarchive/forum.php?forum_id=45438]("http://sourceforge.net/mailarchive/forum.php?forum_id=45438")

in case some background information is required (it is actually the same post, only that for some reason, sometimes replying from gmail to a user list seems to start a new thread).

Cheers.

---

### Post by mcarlson on 2006-05-28
I've been looking into the [gtkmozembed bug]("https://launchpad.net/products/firefox/+bug/26436") and it seems to have started when someone "fixed" [this bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=299988") to use libxul/xulrunner (not really sure what any of that is).

Is it possible to get an older version of this library and use it instead?

Or if any of you are better at reading mozilla code than I (which would be just about anyone) you might want to take a look to see if you can find out what's going on.  Spacificly why mozWidget=0  and both mInternalWidget and mParentWidget are 0 (which seems to be causing the seg fault).

I'd really like to try out Newton ;)

---

### Post by dpm on 2006-05-28
[quote=mcarlson]I've been looking into the [gtkmozembed bug]("https://launchpad.net/products/firefox/+bug/26436") and it seems to have started when someone "fixed" [this bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=299988") to use libxul/xulrunner (not really sure what any of that is).

Is it possible to get an older version of this library and use it instead?

Or if any of you are better at reading mozilla code than I (which would be just about anyone) you might want to take a look to see if you can find out what's going on.  Spacificly why mozWidget=0  and both mInternalWidget and mParentWidget are 0 (which seems to be causing the seg fault).

I'd really like to try out Newton ;)[/quote]

mcarlson,

thanks for your comment. Would you mind adding your last post as a comment to the [gtkmozembed bug]("https://launchpad.net/products/firefox/+bug/26436") in Malone? I've never had a look at the mozilla code myself, but I think your comments would be really helpful in order to point the ubuntu developers in the right direction.

Otherwise this information will be lost -developers look at bug reports, not at the forum. 

Cheers.

---

### Post by leFloyd on 2006-05-28
[QUOTE=desp]Someone on the newton user lists suggested a program called **zim.** It is on the *universe* repos and it is apparently not as nice as Newton, but I haven't tried it myself.
[/QUOTE]

The version in *universe* is rather old. But go to the [homepage]("http://zoidberg.student.utwente.nl/zim/index.shtml") of zim there you will find more and a link to Ubuntu packages for breezy and dapper.

It is small, easy - I actually like it. But I never tried Newton..

---

### Post by dpm on 2006-06-02
Hi,

Well, after reading the comments on the gtkmozembed bug report  ([https://launchpad.net/bugs/26436]("https://launchpad.net/bugs/26436")), I figured out a way to get Newton running.

It is a very simple fix, which I've described at the HOWTO section of the forums. There:

[http://www.ubuntuforums.org/showthread.php?t=185972]("http://www.ubuntuforums.org/showthread.php?t=185972")

As I say, the "fix" is quite simple, do not let the length of the HOWTO scare you off, I've just tried it to make it as clear as possible for everyone.

If anyone happens to read it and test it, please post a comment there to let me know whether this actually helped anyone.

Cheers.

---

