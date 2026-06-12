---
title: "How to Backup iGoogle with Ubuntu + create portable thumb drive"
date: 2008-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by dwanders on 2008-03-14
I have come to love Ubuntu, I also have come to love Google: Gmail, Calendars, Doc Spread sheets etc... cannot be beat for ease of use and availability. But everything eventually will need a back up to restore from... eventually. So I came up with this. I originally set something similar up for my Wife to use for her Windows, I liked it so much I wanted to do it with Linux/Ubuntu as the main OS - so when I got this set up working for myself now, I just felt the need to share it. On the topic of backing up your iGoogle account. If the Google Gods in all their wisdom ever:

 1. come up with a simple - multi platform - way to have everything in my iGoogle account backed up
 2. make it so I can automate the process (e.g. cron a nightly backup of my stuff from iGoogle to my local PC (or wherever I choose)
    
I may just get rid of my numerous PC's and use it exclusively. Until then, I feel the following is just plain common sense for anyone who from time to time:

 1. Cannot access the Internet (for what ever reason)
 2. Cannot access Google servers (for whatever reason)
 3. Just plain wants to backup their stuff they consider important enough for backup.

So call me a wimp! { "Only wimps use backup: _real_ men just upload their important stuff on FTP, and let the rest of the world mirror it ;)" - Linus Torvalds } here is my means of backing up iGoogle email & calendars:

Note the following is specific for a Linux user - this can be done easier with Windows (go figure, kills me that it is easier to set up portable native Linux/Open source stuff on Windows than Linux but go figure!) Any way - this is what I do:

 1. Get a big Thumb Drive (cause I like to keep things with me) I use a WD 160G external USB drive 
 2. Download alpine - I am sure this is just wrong, so everybody yell at me at once! But here is what I did and it worked, so there:
>>> I use Ubuntu so I downloaded the alpine_1.00_i386.deb
>>> I used Applications -> Accessories -> Archive manager to open the deb
>>> Then I opened data.tar.gz and I extract the /bin folder to my thumb
>>> now I have /Programs/alpine/bin on my thumb drive and it contains: alpine, mailutil, pico, pilot, rpdump, rpload all small self contained executables for Linux that are currently running great!
 3. No you need a little script to download all your mail to the thumb drive - I use this:

```

#!/bin/bash                              <- your bash splat
work_dir=$(pwd)                          <- need to get the current dir
cd "$work_dir/Programs/alpine"           <- change to that dir
mailutilhome="$work_dir/BackUP"          <- set the backup dir
HOME=$mailutilhome ; export HOME         <- set $HOME so it goes to your backup dir then run the command
./bin/mailutil transfer "{imap.gmail.com/ssl/user=id@gmail.com}" mailarch/ -v

```

If all is well, the above will run and prompt you for your gmail account password - then it will download all your mail to a folder mailarch in the folder BackUP. All the downloaded messages are stored in mbox format which is pretty much readable or importable to most mail client. 

That's it for mail, you have all your Gmail email stored in mbox format on your thumb drive. Now lets get the calendar.

 1. Open your Gmail account
 2. Go to the Calendar
 3. Click the down arrow next to your Calendar you want backed up
 4. Select Calendar Settings
 5. Click ICAL in private address
 6. Click the Link that pops up (not the OK button - the link)
 7. When prompted, save to your Thumb Drive - I used /BackUP/Calendars
 8. When the download is done, click OK to close the dialog
 9. You now have a backup ics file of that calendar, if you want others, repeat steps 3 - 8 for all calendars, make sure to name them something different each time.

Thats it, you now have a back up of your calendars, and emails. If you backup regularly, or any time you make a major change you should have no problems recovering. I try to perform these steps when ever I think of it, or after I have added a lot to a specific calendar stuff or received an email I do not want to loose. 

Now thats great for a backup, and you will always have it with you (and if your smart - you will back up Thumb Drive from time to time for when it crashes ;) but I am not here to scold anyone  about their particular backup process! So now that we have that - wouldn't it be totally cool if we also had a way to view that stuff we just down loaded without needing to leave the thumb drive or import it into some other application?
 
Well yes indeedy it would! 

Of course - nobody wants to have a back up that we need to wade through with a text editor! However - if that works for you, you've already got it! 
From a console or terminal try:

```

cd "thumb drive"/Programs/alpine
./pilot              <-- This is a little self contained file browser navigate to your back up folder (where you calendar & mbox files are) highlight one of you calendar files or mbox files
E for edit           <-- this will launch your system default editor for the local host computer system

```

If you would prefer to "stay in your thumb drive" try this instead:

```

cd "thumb drive"/Programs/alpine
./pico               <-- this is a little self contained editor  
^R                   <-- (thats control R) to open a file
^T                   <-- control T to browse for the file
Navigate to your BackUP folder 
Open the calendar file or mbox file you need

```
    
The reason I do my scripts like this, is because most of these applications try to helpfully automatically goto your HOME folder to store everything. I don't want to use my real HOME, I want to use the thumb drive. So my thumb drive ends up looking like this:

```
    
"thumb drive path"
       |-- /
           /Personal
           /Programs
           /Data
           alpine     <-- this is the one we made earlier
           tbird      <-- this is the script above

```
      
The biggest problem that I have encountered is that "thumb drive path" can change depending on the system you plug into, so for each script we determine that and then we run the program telling it where we want our "HOME" to be so it does not have to figure it out. Just a little FYI - my entire thumb drive looks like this:
```

"thumb drive path"
       |-- /
           /Launch_win    <-- In here I keep batch/cmd files much like my bash scripts for Linux but for Win
           /Personal      <-- Keep my personal data here
           /Programs      <-- Keep all my programs here
           /Software      <-- Keep installers and app larchives
           /work_stuff    <-- Keep m,y work stuff here
           alpine         <-- bash scritp to launch alpine
           dxfviewer      <-- Java dxfviewer bash launcher
           jedit          <-- The best editor in the world bash launcher
           jfig           <-- Java fig editor (I love XFig this is JFig)
           mailutil       <-- bash script to launch my Email backup
           yed            <-- The best Java Graph editor in the world

```
            
You may notice another pattern, if there is something Java (true portable mutli platform Java that is) application available, I try to use it just in case I am forced to use Windows, I still have my apps pre-configured the way I like them on my drive - I just plug it in and run. And I used this method to moved from a 1G Sony thumb drive, to a 2G Memorex drive, to my current 160GB WD drive simply by dragging and dropping everything from one to the other. Me liky very much!

Boy this got kinda long, sorry - but this is how I back up my iGoogle account!

---

