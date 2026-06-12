---
title: "Another migrant trying to find a replacement for dreamweaver"
date: 2007-04-17
forum: Programming Talk
---

### Post by 1tiger1 on 2007-04-17
Evening all, 

I am an old system V and solaris guy who had been pushed into the microsoft desktop world for a number of years. Now that I am a little older and more in the drivers seat, I want to dump MS and it's minions completely. 

That being said, I have read a few posts pertaining to Dreamweaver and any potential candidates for replacing it. I am on Feisty Fawn beta (mainly because I bought a BRAND new MB and processor) and have run into a few failures already. 

I am not a WYSIWYG coder at all- I am a php guy. I am looking for something that will:

a. Display files that I am editing on one side and a list of files in my site in another
b. Keep a local copy of the site and ONLY publish them to a server (FTP is preferred) if I tell it to
c. NOT give me errors because I forgot to put a <head> tag on a library file. (or similar formatting errors on files that are not meant for reading)

I have tried Eclipse with PHPeclipse, Screem, Geany, NVU, Kompozer, gPHPedit (why would anyone only want to just edit a php file and close it?) and Quanta. Most of them were pretty frustrating to work with, and when I tried to use instructions found in variuos locations on the web, most either didn't work or didn't actually add the feature I was looking for. 

A similar thread like this was opened about a year ago but it hasn't had activity in a while, so I am opening a new one. 

Anyone have any ideas where a guy with at least a good understanding of linux can find tools for php development that don't require opening three or more different applications to edit and publish?

Thanks in advance (and sorry if I have a little attitude- Two weeks of searching on my own for what I thought was a basic need for web developers has worn me a little thin),

-1tiger1

---

### Post by Mirrorball on 2007-04-17
If you drop the FTP requirement, you'll be satisfied much more easily. Just open an FTP client, this will give you two open applications, hardly unmanageable for your brand new motherboard and processor. ;) For PHP editing, the best editor in my opinion is Eclipse + PDT plugin (**not** PHPeclipse).

---

### Post by MikeDX on 2007-04-17
Crossover (or wine) plus dreamweaver8.....

it works brilliantly, only you need a working installation already on a windows machine to transfer it from.

---

### Post by 1tiger1 on 2007-04-17
I call it three because I need firefox and an IDE open (one for coding, one for viewing/testing) and I guess I may have to re-learn my methodology (alt-tab and put rather than put from a button). I didn't mention that I tried PDT because I first went through the dependancy hell of trying to get that to work on my existing Eclipse installation, then I tried the bundled package from the website and that wouldn't even start. 

I also saw the post about dreamweaver 8 (which is what I use), and I guess I will give that a go when I get wine installed on my Feisty box. 

Again, sorry for the 'tude earlier, I was also in broadband purgatory as my cable provider was nice enough to hook up my entire neighborhood (and all of their zombie computers) to my node in the last month so I was getting the 122MB Eclipse at a blazing 12kb/s. Reinstalling and downloading became the root of frustration. 

Thanks,

-1tiger1

---

### Post by Mirrorball on 2007-04-17
> **1tiger1 said:**
> I call it three because I need firefox and an IDE open (one for coding, one for viewing/testing) and I guess I may have to re-learn my methodology (alt-tab and put rather than put from a button).
Why don't you test your PHP code locally? Then you only need to upload your files in the end, when you are done with viewing/testing.

---

### Post by 1tiger1 on 2007-04-17
> **Mirrorball said:**
> Why don't you test your PHP code locally? Then you only need to upload your files in the end, when you are done with viewing/testing.

Because I have learned one thing in my life: My local system is != my hosting provider's system. I am running Apache and MySQL locally, and I do test locally, but about three to four times a week, I get mystery errors that occur remotely that I don't get locally. (@work, I have a windows workstation running XAMPP vs. SLES10 running apache2 and mysql for our servers, happens there too)

Tonight I am going to try either WINE or maybe dust off the old windows box and run a remote desktop.

---

### Post by Mirrorball on 2007-04-17
> **1tiger1 said:**
> I get mystery errors that occur remotely that I don't get locally.
Maybe people are just doing things with your application that you haven't anticipated. They all have this annoying habit.
> **1tiger1 said:**
> Tonight I am going to try either WINE or maybe dust off the old windows box and run a remote desktop.
To me, having three applications running at the same time is a lot easier than running Dreamweaver on wine or, especially, setting up a remote desktop. Is having an integrated FTP client really necessary? Isn't it just something you are used to but offers no real advantages? You can do the job just fine without Dreamweaver. After a week working with different apps, you won't even remember it exists. It's just a different way of doing the same thing and just as efficient.

---

### Post by 1tiger1 on 2007-04-17
Well, aren't I just the flippant tool. 

I tried again from the top of my list to the bottom (the thought of going back to windows for anything other than a game was too much to stomach) and I reinstalled everything. 

I finally found success with Quanta Plus 3.5.6. I just have to hit "F8" and enter and my modified stuff is published. As it turns out, the installation was broken the first time I tried it and the FTP opetion was making it lock up (so I gave up). What a difference a day makes. 

Thanks for listening to me rant and rave.

---

### Post by MKR. on 2007-04-18
I've always just used Kate and konqueror's FTP functionality. You might want to try that out too.

Kate has "sessions", which are functionally similar to "Sites" in dreamweaver.

---

### Post by boteeka on 2007-04-18
I'm also a PHP guy and at work unfortunately I'm forced on Windows :( , where we use Zend Studio for php editing and Dreamweaver 8 for html and javascript. I have to say I like them both, I like ZendStudio's INSTANT code completition feature (don't have to press CTRL+SPACE) and the project based aproach of the whole thing, and Dreamweaver's splitview (it makes navigating in the code window much easier).

At home I'm dual booting between Windows and Feisty and I already tryed a dozen of programs for web development, the majority mentioned in above posts. Finally I settled down at Eclipse+PDT (which I managed to install simply using Eclipse's built-in updater and now works flawlessly) for PHP editing, Firefox for testing and previewing and FireFTP (a Firefox extension) for uploading files. This FTP client has a VERY useful feature, it keeps local and remote directories in sync. So you only have to change directory on one side (be it local or remote) and the other side changes automatically if the directory with the same name exists on both sides.
As for HTML editing, I haven't found anything with the capabilities of Dreamweaver. I've tried Bluefish, Screem, Quanta, NVU, which I remember, but none of them convinced me.

I don't know how is this possible, when the majority of web servers run on top of Linux, and the Linux community still doesn't have the refined free tools for web development.

Or maybe my expectations are too high?

---

### Post by Mirrorball on 2007-04-18
Zend Studio runs on Linux too. The only web development tool that we don't have is a WYSIWYG editor as good as Dreamweaver's, but I believe in writing HTML by hand to produce the best semantic code. A lot of web designers never heard of web standards, semantic code, tableless layout; all they know is how to use Dreamweaver's WYSIWYG editor. But all you need to create the best design is a text editor. The best web designers I know don't use Dreamweaver's WYSIWYG editor. Most use simple HTML editors for MacOS X and they are as good as kate, Quanta, Bluefish... Please learn about web standards, you can start here:
[http://www.456bereastreet.com/lab/developing_with_web_standards/](http://www.456bereastreet.com/lab/developing_with_web_standards/)
[http://www.456bereastreet.com/archive/200512/ten_reasons_to_learn_and_use_web_standards/](http://www.456bereastreet.com/archive/200512/ten_reasons_to_learn_and_use_web_standards/)
Then learn HTML for real and you'll never need a WYSIWYG editor again. Especially after you see what kind of code it produces.

---

### Post by 1tiger1 on 2007-04-18
I hear ya on the WYSIWYG development folks. We have a dual environment at work (PHP and Cold Fusion on Linux) and we have a camp of people who use only the Dreamweaver buttons for database development and my phone number for troubleshooting. 

I haven't opened the visual editor on Dreamweaver since 2005, when I inadvertantly opened it when I was trying to drag my VLC window out of the way of my playlist and it caught on the edge of the code view :)

I haven't used Zend Studio (although we run Zend Core on many of our servers), but I hear it is pretty good. For only $300, maybe I should give it a stab.

---

### Post by _tms on 2007-04-18
Using an editor that supports gnome-vfs will make editing remote files easy. I manage a small PHP site by editing the files on-line with gedit (really dislike PHP though). Only thing it will not do for you is to keep a local mirror but you can copy the files over to the local disk easily.

---

### Post by 1tiger1 on 2007-04-19
> **_tms said:**
> Using an editor that supports gnome-vfs will make editing remote files easy. I manage a small PHP site by editing the files on-line with gedit (really dislike PHP though). Only thing it will not do for you is to keep a local mirror but you can copy the files over to the local disk easily.

I get that totally. I was a VI guy for years (I still hit escape and colon when I am in notepad or gedit on occasion). 

A side note for Quanta Plus: Hitting "F8" brings up the FTP window unless you have Beryl Enabled. Guess I have to re-map those hot-keys :)

---

### Post by barmazal on 2007-04-19
try Aptana baby, ftp works html/xhtml/css works  javascript not so but it's much cooler than any dreamweaver

it can run as stand alone or eclipse plugin


[http://www.aptana.com/](http://www.aptana.com/)

---

### Post by RedSquirrel on 2007-04-20
> **Mirrorball said:**
> Zend Studio runs on Linux too. The only web development tool that we don't have is a WYSIWYG editor as good as Dreamweaver's, but I believe in writing HTML by hand to produce the best semantic code. A lot of web designers never heard of web standards, semantic code, tableless layout; all they know is how to use Dreamweaver's WYSIWYG editor. But all you need to create the best design is a text editor. The best web designers I know don't use Dreamweaver's WYSIWYG editor. Most use simple HTML editors for MacOS X and they are as good as kate, Quanta, Bluefish... Please learn about web standards, you can start here:
[http://www.456bereastreet.com/lab/developing_with_web_standards/](http://www.456bereastreet.com/lab/developing_with_web_standards/)
[http://www.456bereastreet.com/archive/200512/ten_reasons_to_learn_and_use_web_standards/](http://www.456bereastreet.com/archive/200512/ten_reasons_to_learn_and_use_web_standards/)
Then learn HTML for real and you'll never need a WYSIWYG editor again. Especially after you see what kind of code it produces.

I agree 100%.

When you code by hand, you can guarantee that your layers of structure, presentation, and behaviour are separate. Also, when you use id/class attributes, you can give them meaningful names, which makes maintenance a great deal easier (both for yourself and the developers who come along after you).

---

### Post by JustDave on 2007-04-25
I keep hitting road blocks on getting eclipse and pdt installed. I'm running feisty and have eclipse 3.2 installed. I'm wondering how exactly you got pdt installed. I used the update management to install GEF and EMF but JEM and WTP need other dependencies. PDT needs all four of these to be installed.

I have ZendStudio on my main machine. (dapper, will be doing a fresh install of feisty soon)

Any help is much appreciated. :)

---

### Post by barmazal on 2007-04-25
this ain't easy, since Eclipse make errors on Windows and Linux while trying to update to PDT via IDE itself. My best bet is install Eclipse via add/remove programs in Ubuntu and then download full PDT from Eclipse website and just overwrite existing Eclipse directories.

This is my bet though, works on Windows.

---

### Post by dougmorin on 2008-09-08
If you develop on windows, or dont mind running wine on linux, then I really suggest that you try Notepad++.  It has FTP support... which runs a little better than dreamweavers...  and syntax highlighting, word completion, etc...

The word completion is not that good though, and the syntax highlighting you need to modify yourself to get it how you really want (if your picky like me).  I work full time for a web development company, so i need things to work my way for me to work efficiently.

Oh yeah, Notepad++ doesn't have wysiwyg, but oh well... i usually debug in firefox/ie... dreamweaver doesn't really cut it in that department.

I am looking for a development tool to use with linux though, I love notepad++ but don't feel like simulating it with wine... going to have to try Quanta like a previous post said.  Thanks for the suggestion.

Hope this helps.

---

### Post by cb951303 on 2008-09-09
For PHP, all I use is Eclipse + PDT + FTP Plugin. I think it's wonderful. BTW I never had problem running PDT. Just download the bundled package from their site. But since eclipse 3.4.0 came out and PDT still works with 3.3.2 you might want to wait a little (29 December) to get the updated core.

Anyway if you don't want to wait here's the [bundled 3.3.2 version]("http://download.eclipse.org/tools/pdt/downloads/release.php?release=R20080603") with PDT 1.0.3. Get the file pdt-all-in-one-R20080603-linux-gtk.tar.gz
I assure you it works. If that doesn't work it means there is something wrong on your side (bad java installation maybe?)

---

### Post by 1tiger1 on 2008-09-09
Thanks for the extra feedback. I should mention that I got Dreamweaver 2004MX to work in wine, so the problem is solved for now. 

I have used Notepad++ (One of my co-workers swears by it) and will dive into eclipse when I have some time (other co-workers use it on their Macs... but that is another story)

---

### Post by cacycleworks on 2009-01-07
OK this is ancient, but I have a couple thoughts that would benefit anyone "new-ish" to linux and web dev in linux.

I'm a KDE3 guy and use Kate or KDevelop a lot. However, I normally use sshfs instead of ftp. I have found it to be more reliable, if a little slower.

From my desktop, I can edit files on our live site or any of our dev boxes by opening files from my "home" folder ...

example:
$ cd
$ mkdir livehost
$ mkdir dev1
$ mkdir dev2
$ sshfs [email]loginname@livehost.com[/email]: livehost
$ sshfs dev1:/www dev1
$ sshfs dev2:/home/www dev2

And now all 3 of those "remote" machines appear as local. I also do this for "windows shares" via sambafs, only I made a bash script to do that as it was stupid to try and remember all the jibberish to type in. :D 

I just have to be real careful to exit out of my editors when I leave home or work so there aren't any collisions. yeah, I should SVN....

:) Chris

PS - oh, I'm trying to figure out a Zend issue and found this thread talking about zend. Zend Studio is pretty amazing... can't wait to get my problem solved. :) I will probably try to start using ZF and MVC for site design. Not sure about my normal php/mysql coding though... kate/kdevelop are pretty amazing.

---

### Post by 1tiger1 on 2009-01-07
We use MVC pretty heavily where I work, good stuff.

---

