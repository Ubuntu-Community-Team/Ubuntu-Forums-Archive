---
title: "HOWTO: Install Mozilla Sunbird"
date: 2006-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by DCM36 on 2006-10-15
Mozilla Sunbird is now installable by using Synaptic or apt-get. This is the recommended installation method for most users.


Here's an easy, straight-forward install of Mozilla Sunbird.

Open a terminal

We're going to install it to the /opt directory, so:

```
cd /opt
```

Then download Sunbird
```
sudo wget ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.7rc3/linux-i686/en-US/sunbird-0.7rc3.en-US.linux-i686.tar.gz

```

Now extract Sunbird to a folder named sunbird in /opt
```
sudo tar -xvf sunbird-0.7rc3.en-US.linux-i686.tar.gz
```

This gives ownership of the sunbird directory to root.
```
sudo chown -R root:root /opt/sunbird/
```

Now make a script to redirect to sunbird folder in /opt
```
sudo gedit /usr/bin/sunbird.sh
``` 

In the document that opens, copy this into it:
```
cd /opt/sunbird/
./sunbird
```
Save and close the document.

Now make the script that was just made executable
```
sudo chmod +x /usr/bin/sunbird.sh
```

Now create a entry in the appilcations menu
```
sudo gedit /usr/share/applications/sunbird.desktop
```

In the document that opens, enter:
```
[Desktop Entry]
Name=Sunbird
Comment=Calendar Application
Exec=sunbird.sh
Icon=/opt/sunbird/chrome/icons/default/default.xpm
Terminal=false
Type=Application
Categories=Application;Office;
```
Save the document and enjoy.

*Howto courtesy of knowledge76.com*

---

### Post by domino on 2006-10-16
Thanks for the info. Now I have Windows, Linux, and Mac sharing webdav and local calendars. The only thing missing now is a Pocket PC version :)

---

### Post by Xter on 2006-10-20
My goodness it works!:D 
Thank you DCM36!

---

### Post by MyNameUhBorat on 2006-10-23
Works great thank you very much.

---

### Post by lyly on 2006-10-24
Is there any package?

---

### Post by DCM36 on 2006-10-28
> **lyly said:**
> Is there any package?

Not at the moment.. I might have some time to do it in a bit, and if I do I'll post back.

---

### Post by bionnaki on 2006-10-28
nice. worked perfectly. thanks.

---

### Post by SuperGrover21 on 2006-11-09
Yeah! Worked great! Is this a general outline to installing other programs not in Synaptic?

---

### Post by Scunizi on 2006-11-10
Another way is to load the extension for sunbird into thunderbird.  I've done it on windows but not on my linux box yet.  Looks good in windows.

---

### Post by --chris-- on 2006-12-11
Excellent. Worked like a charm. Learned a few things too about Linux programs in the process. Thank you!

---

### Post by anaconda on 2007-01-19
Thanks!
Worked perfectly. in Dapper 6.06

Althought I was worried about the linux-i686 part (I have k7 kernel, not i686 or doesnt it matter?)

---

### Post by tombott on 2007-01-24
Cheers that worked a treat, then I found out there is a Thunderbird Extension called Lightning that is a plug-in version of Sunbird.
Hey ho!

[Lightning]("http://www.mozilla.org/projects/calendar/releases/lightning0.3.html")

---

### Post by bg1256 on 2007-01-26
Thanks for making this so easy! It works great!

---

### Post by DCM36 on 2007-01-29
> **anaconda said:**
> Thanks!
Worked perfectly. in Dapper 6.06

Althought I was worried about the linux-i686 part (I have k7 kernel, not i686 or doesnt it matter?)

It really doesn't matter from my understanding.. The k7 processor understands i686 code, therefore everything is fine.. Anyways, the only time that processor type is important is if the code has been complied for a x86_64 or PowerPC processor.

---

### Post by oyvindaa on 2007-01-31
DCM36, thank you.

---

### Post by Athanasius on 2007-02-01
I used this to install Thunderbird 2 Beta, works perfectly!

---

### Post by skoalman88 on 2007-02-02
Works great! This forum rocks.

---

### Post by Madmoose on 2007-02-11
Hello, 

is there something wrong with the server? I installed this on my laptop maybe Friday or so, but now I get this when trying to install it on my desktop:

> --16:37:40--  [ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.3rc2/linux-i686/en-US/sunbird-0.3.en-US.linux-i686.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.3rc2/linux-i686/en-US/sunbird-0.3.en-US.linux-i686.tar.bz2)
           => `sunbird-0.3.en-US.linux-i686.tar.bz2'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/calendar/sunbird/releases/0.3rc2/linux-i686/en-US ... 
No such directory `pub/mozilla.org/calendar/sunbird/releases/0.3rc2/linux-i686/en-US'.


Can someone help me with this issue?

---

### Post by Daviey on 2007-02-13
Try:

```
sudo wget ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.3.1rc2/linux-i686/en-US/sunbird-0.3.1.en-US.linux-i686.tar.bz2
```

It's a newer release (different filename aswell)

---

### Post by DCM36 on 2007-02-17
thank you daviey.. updated instructions accordingly..

---

### Post by rudeboyskunk on 2007-02-27
thanks a lot, worked like a charm.  will sunbird be standard in feisty?

---

### Post by Madmoose on 2007-03-05
Odd. Did what you said, but the first time I started her up it didn't do anything. Restarted the computer, and then started it up and got a Netscape info thingy. Then nothing, and now tried it again I'm not getting anything. 


Any ideas?:confused:

---

### Post by cisforcojo on 2007-03-06
Think I'm the only person this DIDN'T work for. 
This is the error I'm getting when I run sunbird.
Any ideas?

cojones@tipping-point:/opt/sunbird$ ./sunbird
./run-mozilla.sh: line 131: 26902 Segmentation fault      "$prog" ${1+"$@"}


Thanks for the help!

---

### Post by cisforcojo on 2007-03-06
Solved it.

Add this to run-mozilla.sh before the first line of code:
GTK_IM_MODULE=scim-bridge

Viola!


The problem is caused by SCIM.

---

### Post by Madmoose on 2007-03-11
> **Madmoose said:**
> Odd. Did what you said, but the first time I started her up it didn't do anything. Restarted the computer, and then started it up and got a Netscape info thingy. Then nothing, and now tried it again I'm not getting anything. 


Any ideas?:confused:


ttt

---

### Post by serendipity576 on 2007-03-15
AFter getting Sunbird in the second step, I get this output:

clay@Clay:/opt$ sudo tar -xvf sunbird-0.3.en-US.linux-i686.tar.bz2
tar: sunbird-0.3.en-US.linux-i686.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


Not sure how to proceed??

Clay

---

### Post by serendipity576 on 2007-03-15
anyone??

---

### Post by DCM36 on 2007-03-15
it should work know.. i updated the instructions, forgot to update the untar command

---

### Post by serendipity576 on 2007-03-16
like a charm!  Thanks much. :KS

---

### Post by matchstich on 2007-04-05
thanks. it worked for me.

---

### Post by l1oyd on 2007-04-23
Thank you!

Only just installed my first Linux OS and as such found this thread to be most helpful in understanding more than just the install of Sunbird.

Thank you again

---

### Post by macogw on 2007-04-23
Is it just me or does Ubuntu lack a /opt?  I put mine in /usr/bin when I did it, then learned that installing as sudo makes the profile file in the home drive have root permissions so sunbird doesn't work right without sudo... (I didn't follow the directions, but I did it pretty much the same).

---

### Post by nightfrost on 2007-05-01
Thanks for the instructions. I've used them to write a little script.

I've never really liked installing stuff system wide that are not packaged since it might lead to complications later on. For this reason I've written a small script that downloads and installs sunbird in the user's home directory and adds an entry in the menus. It's quite simple and crude, it should be very easy to add an uninstall bit to it as well. Perhaps it could be neat to rewrite it to use zenity and be more dynamic so it can install other precompiled applications in the user's home-dir with the ability to uninstall them again.

Anyway, here it is, in case you might want to use it:

```
#!/bin/bash
msg() {
                echo -e "\033[1;32m==>\033[1;0m \033[1;1m$1\033[1;0m" >&2
}

msg "This script will download and install sunbird 0.3.1 locally for this user"
msg "Press Enter to continue"
read

START_DIR="`pwd`"

# Create the local share-dir if it doesn't exist
if [ ! -d $HOME/.local/share ]; then
	msg "Creating $HOME/.local/share" && sleep 1
	mkdir -p $HOME/.local/share/
fi

# Download and extract sunbird
msg "Downloading sunbird 0.3.1" && sleep 1s
cd $HOME/.local/share
wget ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.3.1/linux-i686/en-US/sunbird-0.3.1.en-US.linux-i686.tar.bz2
msg "Extracting sunbird" && sleep 1s
tar xvjf sunbird-0.3.1.en-US.linux-i686.tar.bz2
msg "removing downloaded file" && sleep 1s
rm sunbird-0.3.1.en-US.linux-i686.tar.bz2

# Makes sure the local bin-dir is in PATH
BIN_IN_PATH=`echo $PATH | grep $HOME/.local/bin | wc -l`
if [ "$BIN_IN_PATH" = "0" ]; then
	msg "adding $HOME/.local/bin to PATH" && sleep 1
	echo "# Adding local binary path to the path array" >> $HOME/.bashrc
	echo "export PATH=\$PATH:$HOME/.local/bin" >> $HOME/.bashrc
	source ~/.bashrc
fi

# Create the execution script
msg "Creating Sunbird execution script" && sleep 1
if [ ! -d $HOME/.local/bin ]; then
	mkdir -p $HOME/.local/bin/
fi

cd $HOME/.local/bin
echo "#!/bin/bash" >> sunbird.sh
echo "cd $HOME/.local/share/sunbird/" >> sunbird.sh
echo "./sunbird" >> sunbird.sh
echo "cd -" >> sunbird.sh
chmod +x sunbird.sh

# Create .desktop-file
msg "Creating Sunbird desktop file entry" && sleep 1
if [ ! -d $HOME/.local/share/applications ]; then
	mkdir -p $HOME/.local/share/applications
fi
cd $HOME/.local/share/applications

echo "[Desktop Entry]" >> sunbird.desktop
echo "Name=Sunbird" >> sunbird.desktop
echo "Comment=Calendar Application" >> sunbird.desktop
echo "Exec=$HOME/.local/bin/sunbird.sh" >> sunbird.desktop
echo "Icon=$HOME/.local/share/sunbird/chrome/icons/default/default.xpm" >> sunbird.desktop
echo "Terminal=false" >> sunbird.desktop
echo "Type=Application" >> sunbird.desktop
echo "Categories=Application;Office;" >> sunbird.desktop

msg "Done and Done. Sunbird should now be added to the GNOME menu." && sleep 1
cd "$START_DIR"

```

Make sure to chmod +x the file and then run it. For some reason "sh $FILENAME" gives some errors...

---

### Post by justynbutler on 2007-05-01
Instead of creating a script called sunbird.sh, I used a symbolic link to /usr/bin.

After unpacking the sunbird folder in /opt, this command:

sudo ln -s /opt/sunbird/sunbird /usr/bin/sunbird

So sunbird runs using the command sunbird.

---

### Post by newpants2003 on 2007-05-15
thanx a lot

---

### Post by kstella on 2007-05-21
This is great! Thanks!

---

### Post by Kaobear on 2007-05-21
Easy and simple, nice one indeed.

---

### Post by nickbooker on 2007-05-28
> **nightfrost said:**
> Make sure to chmod +x the file and then run it. For some reason "sh $FILENAME" gives some errors...

Just FYI...

The only thing I can think of that would cause this is because Edgy and above use dash, not bash, as the default shell.  Dash is smaller and less full-featured than bash.

```
nick@deepthought:~$ ls -l `which sh`
lrwxrwxrwx 1 root root 4 2007-04-28 16:41 /bin/sh -> dash
```

Assuming this is the cause => it will work if you call ```
bash $FILENAME
``` directly.

---

### Post by madmetal on 2007-06-07
hey! this works fine! 
thanks for the how-to!
:KS

---

### Post by nightfrost on 2007-06-10
> **nickbooker said:**
> Just FYI...

The only thing I can think of that would cause this is because Edgy and above use dash, not bash, as the default shell.  Dash is smaller and less full-featured than bash.

```
nick@deepthought:~$ ls -l `which sh`
lrwxrwxrwx 1 root root 4 2007-04-28 16:41 /bin/sh -> dash
```

Assuming this is the cause => it will work if you call ```
bash $FILENAME
``` directly.

Yes, you're right about that! Thanks for the info!

---

### Post by Frizguru on 2007-06-11
That was so incredibly easy and you said exactly what each step was doing before you said the code. You should make more for all kinds of things. Maybe an easy to use manual. I have referred this to countless Linux users now. Keep it up!

---

### Post by pt123 on 2007-06-28
Does this work for 0.5 too?

---

### Post by coyotepod on 2007-06-28
I've got Sunbird installed in /opt and it excutes OK except every time it runs it ask me to setup a new profile. The default folder cannot be written to, so I setup a profile folder in a local user folder and then it works. The profile is there and can be used, but I have to manually choose the folder every time. Is there a way to move the profile or gain permission to where Sunbird wants to look? i'm a linux n00b, so thanks for any help

---

### Post by coyotepod on 2007-07-01
here's a screenshot of the error i get. then i end up choosing a different folder for the profile. thanks

---

### Post by Weav on 2007-07-02
Thanks for the tutorial, works great!

---

### Post by Kundalinux on 2007-07-05
How come mine isn't working? I followed your instructions and apparently got it installed. Even the launcher is on the Applications menu, but when I click it the program does not launch. Help

---

### Post by Carbon Tiger on 2007-07-06
Worked like a charm. Thanks so much.

---

### Post by ceccaaan on 2007-07-14
Didn't work for me:(
Sunbird won't execute.

---

### Post by DCM36 on 2007-07-18
I've updated the orginal post to the latest verison available.. Post back if there's any problems with it..

---

### Post by ColinIam on 2007-07-20
Wow!  That worked really nicely.

---

### Post by stinger30au on 2007-07-20
> **Scunizi said:**
> Another way is to load the extension for sunbird into thunderbird.  I've done it on windows but not on my linux box yet.  Looks good in windows.

looks great indeed, i went looking and found it

[http://www.mozilla.org/projects/calendar/](http://www.mozilla.org/projects/calendar/)

thanks

---

### Post by rainontin on 2007-07-21
Thanks, works like a charm, and for spanish users and everyone else: you just have to change sunbird-0.5.en-US.linux-i686.tar.gz for sunbird-0.5.es-ES.linux-i686.tar.gz, take the en-US as a variable.

---

### Post by D 0 R K TRONIKS on 2007-07-22
This was a very helpful tutorial. Thanks a lot.

---

### Post by Artimusp on 2007-07-31
DCM36 Your a genius! Thank you.

---

### Post by UbuWu on 2007-08-06
For everyone using Gutsy: sunbird is in the ubuntu repositories now.

---

### Post by tegwilym on 2007-08-16
Installed flawlessly on my machine using the intructions in the start of the thread.

Ok, now that it's working does anyone know of a good HowTo that shows how to set this up to save/share calendars on a network web server?  I get it to save the ICS file to the WebDAV server, but strange things happen, I lose the data in the local calendar, and it just dosen't seem to upload/download correctly.  

Anyone?

Tom

---

### Post by FiremothPilot on 2007-08-20
Amazing what this OS can do. 

Thanks a million.

---

### Post by michael37 on 2007-08-22
[LIST]
[*]Updated [Sunbird](https://help.ubuntu.com/community/Sunbird) Wiki help page with the new 0.5 version of Sunbird
[*]Added new page for [ Mozilla Calendar](https://help.ubuntu.com/community/MozillaCalendar)
[*]Added cross-links between Lightning and Sunbird Wiki help pages
[/LIST]

---

### Post by michael37 on 2007-08-22
> **tegwilym said:**
> Installed flawlessly on my machine using the intructions in the start of the thread.

Ok, now that it's working does anyone know of a good HowTo that shows how to set this up to save/share calendars on a network web server?  I get it to save the ICS file to the WebDAV server, but strange things happen, I lose the data in the local calendar, and it just dosen't seem to upload/download correctly.  

Anyone?

Tom

Well, let's do an example with Google calendar.

Go to calendar.google.com

In the calendar list on the left, click on the down-arrow next to the appropriate calendar and select "Calendar settings." (Alternatively, click on "Manage Calendars" at the bottom of the calendar list, then click on the name of the appropriate calendar.)

On the bottom of the page, in the section named "Private Address:", find the ICAL green button.

Right click on ICAL green button and select "Copy Link Location"

Go to Sunbird or Lightning.

Under Calendars, click on "New"

In the wizard, select "On the network", "Next"

Select format "iCalendar (ICS)"
and paste the link you copied above.  It should end on .ics.  Click on "Next".

Give your calendar a meaningful name (e.g. Joe's Google Calendar). 

Complete the wizard.

Your calendar is now set up!

---

### Post by bailewen on 2007-08-23
> **cisforcojo said:**
> Solved it.

Add this to run-mozilla.sh before the first line of code:
GTK_IM_MODULE=scim-bridge

Viola!


The problem is caused by SCIM.

How do you do that?

That advice is completely over my head. Right now I've got sunbird installed from the advice at the beggining of the thread but clicking on the icon it created does nothing. The program just doesn't launch and I really can't understand the advice posted above.

Help?

---

### Post by michael37 on 2007-08-23
> **bailewen said:**
> How do you do that?

That advice is completely over my head. Right now I've got sunbird installed from the advice at the beggining of the thread but clicking on the icon it created does nothing. The program just doesn't launch and I really can't understand the advice posted above.

Help?

Open the terminal and type 
```

sunbird

```

If it says something like **core dumped**, then you need to follow the above suggestion.   Where is the file?  Go to Applications/Accessories/Text Editor.  Open file /opt/sunbird/run_mozilla.sh

---

### Post by bailewen on 2007-08-23
When I type "sunbird" into a command prompt, it just says, "command not found".

:confused:

But thanks for showing me how to find that file.

I added GTK_IM_MODULE=scim-bridge to the first line. I am supposed to still put the little # sign in front of it? Anyways, even with that done, still...."command not found"

Feeling frustrated as this is really going to be an issue if I want to stop using windows. If I can't synch up stuff online then I'll be forced to keep going back to windows all the time to keep up with my class schedule, work etc. A good calender program like this is crucial. Koffice is pretty sweet or Kschedule or whatever it was...looks the same as sunbird basically but without the ability to synch up with other computers.

*grrrr*

---

### Post by michael37 on 2007-08-23
> **bailewen said:**
> When I type "sunbird" into a command prompt, it just says, "command not found".

:confused:

But thanks for showing me how to find that file.

I added GTK_IM_MODULE=scim-bridge to the first line. I am supposed to still put the little # sign in front of it? Anyways, even with that done, still...."command not found"


No, you don't need the # sign.  That's a sign of a comment.  So, if you put it in, get rid of it.

Once you save the file, type 
```

cd /opt/sunbird/
./sunbird

```
in the terminal.  (btw, that's on the first page -- that's what I meant).  Is that any better?

---

### Post by bailewen on 2007-08-24
Just couldn't get it to work. Spent hours on it but I eventually found a much better solution.

Thunderbird is right there in the "Add/Remove" program selection that comes with Ubuntu. Don't even need Synaptec. Then once you've got Thunderbird, the process for adding in Lightning is WAAAAY easier than for Sunbird. Just download the extension and add it in through the menu. It's got all the funtionality of Sunbird (arguably more) is integrated better etc.

---

### Post by michael37 on 2007-08-24
> **bailewen said:**
> Just couldn't get it to work. Spent hours on it but I eventually found a much better solution.

Thunderbird is right there in the "Add/Remove" program selection that comes with Ubuntu. Don't even need Synaptec. Then once you've got Thunderbird, the process for adding in Lightning is WAAAAY easier than for Sunbird. Just download the extension and add it in through the menu. It's got all the funtionality of Sunbird (arguably more) is integrated better etc.

Thanks for the hint.  I will add your suggestion to the Wiki page.

For posterity: This solution works only for the 32-bit Ubuntu.  It's slightly more complicated for 64-bit (AMD64) Ubuntu.

---

### Post by topher920 on 2007-09-11
great tutorial! thanks!!!

:guitar:

---

### Post by aduff on 2007-09-12
Works like it should. Your efforts are very much appreciated. Many thanks

---

### Post by tobbilla on 2007-09-13
Thanks its working

---

### Post by zhimlpe on 2007-09-13
great tutorial very helpful  i learn a lot:) thanks

Avelyn
WebMaster
[s9.com]("http://www.s9.com") - Biographical Dictionary contains information on 33000 notable people from ancient times to the present day.

---

### Post by Wikzo on 2007-09-14
The guide worked ... but how do I get other languages support as well? How do I install the Danish language plug-in?

---

### Post by michael37 on 2007-09-14
> **Wikzo said:**
> The guide worked ... but how do I get other languages support as well? How do I install the Danish language plug-in?

You downloaded and installed sunbird-0.5.en-US.linux-i686.tar.gz per this guide.

I think the language selection is pretty self-explanatory.

If you want other languages, you need to download and install another package which matches your language.

Browse this link: [http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.5/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.5/linux-i686/) to see supported languages in Sunbird.  Then, pick the package fory our language (I am guessing it will be [http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.5/linux-i686/da/sunbird-0.5.da.linux-i686.tar.gz](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.5/linux-i686/da/sunbird-0.5.da.linux-i686.tar.gz))

---

### Post by dcolombara on 2007-10-01
I followed DCM36's instructions to install Thunderbird 2.0.0.6 perfectly on ubuntu 7.04. 

I then tried following the same instructions for Sunbird 0.5 on the same system and it doesn't work. A window pops up titled "Close Sunbird" and says, "**Sunbird is already running, but is not responding. To open a new window, you must first close the existing Sunbird process, or restart your system**." Below is a single button saying "OK".

I looked in the system processes but didn't see it listed. I restarted the system but it didn't help. In desperation went back and deleted everything that I 'think' was installed (/opt/sunbird, /usr/bin/sunbird.sh, /usr/share/applications/sunbird.desktop) and tried to do the install again. I received the same error. 

I gave up and tried to get around this problem by using the lightning plugin in Thunderbird. It installs but doesn't display properly in the month view.

Does anyone have any suggestions for getting Sunbird work (or if not, then lightning)?

I'm a total newbie so any help would be great. Thanks in advance.

---

### Post by bigken on 2007-10-01
worked a treat for me cheers :)

---

### Post by michael37 on 2007-10-01
> **dcolombara said:**
> I followed DCM36's instructions to install Thunderbird 2.0.0.6 perfectly on ubuntu 7.04. 

I then tried following the same instructions for Sunbird 0.5 on the same system and it doesn't work. A window pops up titled "Close Sunbird" and says, "**Sunbird is already running, but is not responding. To open a new window, you must first close the existing Sunbird process, or restart your system**." Below is a single button saying "OK".

I looked in the system processes but didn't see it listed. I restarted the system but it didn't help. In desperation went back and deleted everything that I 'think' was installed (/opt/sunbird, /usr/bin/sunbird.sh, /usr/share/applications/sunbird.desktop) and tried to do the install again. I received the same error. 

I gave up and tried to get around this problem by using the lightning plugin in Thunderbird. It installs but doesn't display properly in the month view.

Does anyone have any suggestions for getting Sunbird work (or if not, then lightning)?

I'm a total newbie so any help would be great. Thanks in advance.

Is your computer 32-bit or 64-bit?  If not sure, run 
```

uname -m

```

---

### Post by dcolombara on 2007-10-02
> **michael37 said:**
> Is your computer 32-bit or 64-bit?  If not sure, run 
```

uname -m

```

thanks for the quick response ... 
it said "i686", which I think means 32-bit, right?

btw, i installed the windows version through wine. Though it's slow to open and way ugly, but it works. That is to say, if this is going to be complicated for you ... don't worry about it.

---

### Post by michael37 on 2007-10-05
> **dcolombara said:**
> thanks for the quick response ... 
it said "i686", which I think means 32-bit, right?

btw, i installed the windows version through wine. Though it's slow to open and way ugly, but it works. That is to say, if this is going to be complicated for you ... don't worry about it.

Yes, that does mean you are running 32-bit.  My only recommendation is to uninstall Lightning extension, then upgrade Thunderbird to version 2.0 (see [ThunderbirdNewVersion howto](https://help.ubuntu.com/community/ThunderbirdNewVersion)) and then install Lighting extension directly from [ addons.mozilla.org](https://addons.mozilla.org/en-US/thunderbird/addon/2313)

In addition, make sure you reboot your computer before starting Thunderbird 2.  I am concerned whether you have some Sunbird junk still in your memory.

---

### Post by dcolombara on 2007-10-07
> **michael37 said:**
> Yes, that does mean you are running 32-bit.  My only recommendation is to uninstall Lightning extension, then upgrade Thunderbird to version 2.0 (see [ThunderbirdNewVersion howto](https://help.ubuntu.com/community/ThunderbirdNewVersion)) and then install Lighting extension directly from [ addons.mozilla.org](https://addons.mozilla.org/en-US/thunderbird/addon/2313)

In addition, make sure you reboot your computer before starting Thunderbird 2.  I am concerned whether you have some Sunbird junk still in your memory.

Okay, thanks a bunch. I'll try it. If it doesn't work, I'll stick with my wine/windows hack until 7.10 is released.

---

### Post by Niscrome on 2007-10-09
Thanks dude! It worked perfectly:biggrin:!

---

### Post by carolinamagi on 2007-10-15
I keep running into a problem . . .

The connection times out, three times, and then the installation/download hangs up.

Nothing happens after the "sudo wget . . . ." command. The connections times out and all I see is  "==> PASV . . ."


Any ideas?

---

### Post by michael37 on 2007-10-15
> **carolinamagi said:**
> I keep running into a problem . . .

The connection times out, three times, and then the installation/download hangs up.

Nothing happens after the "sudo wget . . . ." command. The connections times out and all I see is  "==> PASV . . ."


Any ideas?

Try to download the file using the web browser.   Go to 

[http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.5/linux-i686/en-US/](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.5/linux-i686/en-US/)

right click on the file sunbird-0.5.en-US.linux-i686.tar.gz and select "Save As".

---

### Post by carolinamagi on 2007-10-16
> **carolinamagi said:**
> I keep running into a problem . . .

The connection times out, three times, and then the installation/download hangs up.

Nothing happens after the "sudo wget . . . ." command. The connections times out and all I see is  "==> PASV . . ."


Any ideas?

Hey all! Figured it out.
For some reason, the wireless connection I was using my problem
I tried the instructions on a wired connection and had no problems at all.
THANKS!

---

### Post by MeltingPlastic on 2007-10-26
Hey guys,

I'm running into a problem with Sunbird.  I had it working just fine and had my calender set up and everything.  Outta nowhere when i opened it one day it just froze and i had to forcequit..  I figured it might be corrupt install and uninstalled, rebooted and reinstalled and still the same thing.  Figured it might be a corrupt profile so i backed up my old one and sunbird loaded up asking for to import from evolution, told it no,  it showed the calender and then froze.  What is going on here?  how can i get sunbird working again.  I'm new to Linux and all i seem to keep running into is problems with Ubuntu

---

### Post by pt123 on 2007-10-26
does this script work with the 0.7 version and Gusty?

---

### Post by pt123 on 2007-10-26
When I installed 0.7 using the script,

I get this dialog box saying the chrome failed when I run Sunbird,

but then Sunbird starts after that.

attached is the error dialog box.

---

### Post by Philk on 2007-11-01
Thank you, DCM36, tremendously.  I just installed Sunbird into my 7.10 setup and it worked right off the bat - as so many others have said.  I had seen my wife using Sunbird in Windows and liking it there.  I don't particularly like the Evolution products.

This will be a very useful addition. :popcorn:[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

Phil

---

### Post by DCM36 on 2007-11-14
I've updated the first post to the latest verison of Sunbird. I can't confirm if it works properly or not, as I don't have a Ubuntu install up at the moment but I will within the next few hours and I will test ASAP and work out any bugs.

I also read though the thread and saw that Sunbird is now available in the apt repositories, but I will continue to update this howto as this is version 0.7rc3, compared to apt's 0.5-0ubuntu4. 

Report back with any bugs.

---

### Post by Kundalinux on 2007-11-14
Hi people. If you have installed the new Ubuntu 7.10, Sunbird is in Sinaptic, so you can installed from there and it runs perfectly! :)

---

### Post by MCrittenden on 2007-12-02
EDIT: Nevermind. I'm stupid.

---

### Post by EmilyRose on 2007-12-07
Right, so I first tried installing sunbird via synaptic but I got vs 0.5 and couldn't update it (update wouldn't do anything) so i uninstalled and tried the how-to... and now its not starting... thoughts?

am running 7.10

---

### Post by pt123 on 2007-12-07
You should post the error messages when running it through the terminal

---

### Post by EmilyRose on 2007-12-07
well, when I type sunbird in terminal it says :

bash: /usr/bin/sunbird: No such file or directory

same thing when I'm in /opt/sunbird 

when I doublickc on the sunbird file and click 'run in terminal' a terminal flashes and then closes and nothing... so I really don't know what to post??

ETA: '

./sunbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


get that after trying sunbird.sh ... so am installing libstdc++5 via synaptic??

Yay! that fixed it!! execpt I get something about chrome registrartion failure at every start up??

---

### Post by pt123 on 2007-12-08
I got the chrome registration error message on my first load of the application, and when I install a new extension. 

It is probably better to check this error on a Mozilla forum,

---

### Post by macogw on 2007-12-16
Oh do the Sunbird nightlies work on Ubuntu now?  They haven't worked for me since March or April.  Whenever it was that 0.6 stopped getting updates because it couldn't find the internet, their nightly 0.6 and then 0.7builds were unusable.  I currently use a version of Sunbird that I pulled from CVS, attempted to compile, got an error on the *make install* (not "make"?!) and commented out the offending code, and now it works.

OK yeah so uh I just downloaded the 0.7 release, and it's just a segfault, like every release and nightly I've tried in the last 9 months (I tried like 10 of them...some from April, some in May, some in June, some in September...)

---

### Post by pt123 on 2007-12-16
There is deb for Linux Mint of 0.7 that has been working for me.

[http://ubuntuforums.org/showthread.php?t=597441](http://ubuntuforums.org/showthread.php?t=597441)

---

### Post by realbiga on 2008-01-07
worked like a charm, thanks!

---

### Post by MaxVK on 2008-01-08
I followed the instructions and everything went exactly to plan, however, when I first ran Sunbird I got an error about the chrome and it closed. Since then, when I try to open the program, it flashes up onto the desktop, usually as simple a black square, although sometimes it shows the main window contents in black and white, and then it vanishes again.

I fear that this is my own fault for following the instructions before I read the whole thread - had I done so I would have seen that Sunbird is in Synaptic.

In any case, can anyone explain now I can REMOVE this installation of Sunbird, allowing me to then install from Synaptic?

Many thanks

Max

---

### Post by DarinB on 2008-01-28
i found a post to try lightning in thunderbird so i will give it a try 
it looks just like sunbird and is present every time i go to email.
thanks to who ever put that up i can't find it again

---

### Post by salmanal on 2008-02-08
I get the icon in my APPS folder, but I click on it and nothing
executes. I'm wondering if the version I downloaded was 32-bit only.
I run off Athlon 64.......

Yesterday, I copied the instructions and pasted them into
a terminal window.

---

### Post by salmanal on 2008-02-08
I copied all the instructions and pasted them into a terminal.
I see Sunbird in my APPS menu, but it won't execute.

I run Ubuntu 7.04 on an AMD64 with a Gig of RAM.

Thanks :(

---

### Post by djinn1973 on 2008-03-04
Thank you

---

### Post by swat253 on 2008-03-12
I'm a total Linux Noob and only installed Ubuntu 7.10 today. It's workin great although I'm at a complete loss as to the first step of installing Sunbird.

I d-loaded the Sunbird Linux version today and extracted the files.

Where/How do I get to the first step of the instructions, ie; opening the first terminal to write in the scripts? From all the posts, I gather that the instructions are fantastic and they've worked for 99% of the board users. I just need help gettin to the terminal part and need to now what to do with the files I've already extracted.

Thanks All!

---

### Post by swat253 on 2008-03-12
> **swat253 said:**
> I'm a total Linux Noob and only installed Ubuntu 7.10 today. It's workin great although I'm at a complete loss as to the first step of installing Sunbird.

I d-loaded the Sunbird Linux version today and extracted the files.

Where/How do I get to the first step of the instructions, ie; opening the first terminal to write in the scripts? From all the posts, I gather that the instructions are fantastic and they've worked for 99% of the board users. I just need help gettin to the terminal part and need to now what to do with the files I've already extracted.

Thanks All!

OK - Like I said - total Linux Noob...  I finally opened a terminal from the Applications/Accessories tab and will post accordingly after I follow the original post's instructions... [-o<

---

### Post by xsilvergs on 2008-03-19
Sorry to ask a question but I am new to Ubuntu but have been running Sunbird on my home network, using Windows, for some time.

All my PC's access common calendar files on a windows PC using file://///pcname/folder/calendarfile.ics. In Sunbird on my Ubuntu PC if I do File > New Calendar > On the Network  , what do I write in the Location: box,  file://///pcname/folder/file.ics does not work?

I'm trying to access an .ics file on an NTFS partition on a Widows PC from Ubunto, is it possible?

Thanks

Tony

---

### Post by pt123 on 2008-03-19
> **xsilvergs said:**
> New Calendar > On the Network  , what do I write in the Location: box,  file://///pcname/folder/file.ics does not work?


You can try : smb://pcname or smb://lanIP
But you need Samba installed and set up so that these addresses work in Nautilus. 

Or you can mount the network share on to your computer and use it as a Local file.

---

### Post by xsilvergs on 2008-03-20
pt123

Thanks for reply, I'm very new to Ubuntu so still learning. 

I have Samba installed and have tried smb://pcname/folder/file, when I try this method no calendar appears in the calendar list. 

I have a shortcut on the desktop to the folder containing the .ics file, this has a little SMB in the bottom corner. I'm not sure how this appeared on the desktop, it must have been during previous attempts.

You mention setting up Samba like Nautilus, could you explain more please?

Thanks again

---

### Post by pt123 on 2008-03-20
> **xsilvergs said:**
> pt123
I have a shortcut on the desktop to the folder containing the .ics file, this has a little SMB in the bottom corner. I'm not sure how this appeared on the desktop, it must have been during previous attempts.
That is most likely you browsed the network in Nautilus. 

> 
You mention setting up Samba like Nautilus, could you explain more please?
Thanks again

In Nautilius - >  Go> Network 

Either computer names or Windows Network should appear

either way navigate to the samba share with the ICS.

Now press Ctrl + L
That should show the location

what ever it is post it here

--------
The other method is mounting the samba share
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_permanently_mount_a_samba_share](http://easylinux.info/wiki/Ubuntu_dapper#How_to_permanently_mount_a_samba_share)

---

### Post by xsilvergs on 2008-03-27
pt123
Sorry for delay, been away over Easter.

Ctrl + L gives Network:///

I have noticed that the folder permissions says "The permissions of xxxx could not be determined"
Is this the problem, if so how do I change it?

If I explore my network from Ubuntu and try to open the .ics file with Text Editor it opens, but if I "Open with other application" and choose Sunbird, Sunbird opens but no calendar appears.

If I copy the .ics and paste on my Ubuntu desktop the file opens ok.

---

### Post by pt123 on 2008-03-27
you have to browse to the computer then folder where you have this file shared, otherwise you can't expect sunbird to find. 

Maybe it is better if post screenshots of Nautilus in when Netowrk is opened.

---

### Post by xsilvergs on 2008-03-27
Does this help?

---

### Post by SkonesMickLoud on 2008-03-31
```
sudo apt-get install sunbird
```

Works too.

[edit] It's also in Synaptic.

---

### Post by pt123 on 2008-04-01
i tried using smb:// and it didn't work

so try mounting the folder by this command
sudo mount //vectra/GCALDaemon /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777

Then in Sunbird browse to the folder  /media/sharename

---

### Post by hezuo on 2008-07-21
thx! it helped me a lot

---

### Post by Kenn11 on 2008-08-01
IMHO, a couple of improvements could be made to make this How to slicker than owl stuff.

First, I think a couple of preliminarily notes could be made to insure SB would load and run.  Insure that "libstdc++5" and sun-java6-jre, sun-java6-bin are present.  And second,

if somebody could update the wget address to get sunbird 0.8 from mozilla it sure would be easier.(It only took me three hours to get it right)

Ken

---

### Post by QwUo173Hy on 2008-08-12
Kenn11, could you supply the commands you used? I also want to install 0.8 as the Mozilla download page recommends not using older versions for security / stability issues as well as problems with data loss and corruption

[Link]("http://www.mozilla.org/projects/calendar/sunbird/download.html")

---

### Post by xen-uno on 2008-08-24
I used the how-to here (identical to DCM's) ...

[http://www.aloke.info/2008/07/22/how-to-install-mozilla-sunbird-in-ubuntu/](http://www.aloke.info/2008/07/22/how-to-install-mozilla-sunbird-in-ubuntu/)

and installed the 64 bit version available here ...

[http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.8/contrib/linux-x86_64/sunbird-0.8.en-US.linux-x86_64.tar.gz](http://releases.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.8/contrib/linux-x86_64/sunbird-0.8.en-US.linux-x86_64.tar.gz)

Follow DCM's steps exactly until you reach ...

The **sudo wget ...** line as it is unnecessary if you DL direct from the Mozilla page or use the x64 link above. *Do not run/extract* ... save the *.gz file to a known directory & path (I used Desktop) then run either of the following (instead of DCM's **sudo tar** line) from Terminal:

64 bit:

**sudo tar -xvf [color=red]/home/jan/Desktop[/color]/sunbird-0.8.en-US.linux-x86_64.tar.gz**

32 bit:

**sudo tar -xvf [color=red]/home/jan/Desktop[/color]/sunbird-0.8.en-US.linux-i686.tar.gz**

^^^ in either case, replace /home/jan/Desktop with your path to the *.gz ^^^

Now continue with the rest of his script.

You may get a chrome error on 1st run (I did). On 2nd attempt, error went away and it runs good.

---

### Post by natedawg88 on 2009-10-07
this isnt working for me

this is what i get when i enter the second code


--2009-10-07 16:57:56--  [ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.7rc3/linux-i686/en-US/sunbird-0.7rc3.en-US.linux-i686.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/releases/0.7rc3/linux-i686/en-US/sunbird-0.7rc3.en-US.linux-i686.tar.gz)
           => `sunbird-0.7rc3.en-US.linux-i686.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/calendar/sunbird/releases/0.7rc3/linux-i686/en-US ... 
No such directory `pub/mozilla.org/calendar/sunbird/releases/0.7rc3/linux-i686/en-US'.

---

### Post by ptrlow on 2010-04-30
Thanks for the tip.

---

### Post by cha0s on 2010-05-11
Hey, just wanted to point out that it appears Mozilla isn't developing Sunbird anymore. On [Mozilla's Sunbird download page]("http://www.mozilla.org/projects/calendar/sunbird/download.html") it says:

> This is the last public Sunbird release by the Calendar Project.
We recommend upgrading to [Thunderbird 3]("http://www.mozillamessaging.com/") and [Lightning 1.0 beta1]("https://addons.mozilla.org/thunderbird/2313/").

However, the link there didn't work for me (I'm on 64-bit), so I looked around Mozilla's servers and I found

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/contrib/linux-x86_64/lightning.xpi](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/contrib/linux-x86_64/lightning.xpi)

, which seems to be working! I haven't test it that much so no guarantees. Just wanted to help out my fellow open source friends. :)

---

### Post by Sapienso on 2010-06-19
Thanks a lot, DCM36. 

I was looking just for these kind of instructions, since I am just a final user, and did not know how to install a package that you download. 

In ubuntu 10.04 sunbird does not appear in synaptic package manager. 

It was not possible to use sudo apt-get install sunbird either. 

I downlowaded it from [http://www.mozilla.org/projects/calendar/sunbird/l10n_download.html](http://www.mozilla.org/projects/calendar/sunbird/l10n_download.html)  in Spanish, mi native language. 

So what I did was to follow the instructions by DCM36 once I moved my file (called sunbird-1.0b1.tar.bz2) to the opt directory. 

I was wondering if the tar command would work here (since it is not a tar.gz file), but it did. 

Thanks again,

---

### Post by Carlo_Delft on 2010-07-05
It works perfectly even with the new version of Sunbird. 
Thank you very much for your guide. 

CG

---

### Post by Flos Headford on 2010-08-25
In my opinion, Sunbird is unfit for use. If I change view, all events disappear from view; I can't copy events from one calendar to another; I can't synchronise with Google Calendar; the Properties dialogue presents very few settings, and I can't change the Calendar Location.
I've wasted days on this.
Phil

---

### Post by mrkazoodle on 2010-10-10
> **Flos Headford said:**
> In my opinion, Sunbird is unfit for use. If I change view, all events disappear from view; I can't copy events from one calendar to another; I can't synchronise with Google Calendar; the Properties dialogue presents very few settings, and I can't change the Calendar Location.
I've wasted days on this.
Phil

You can sync with google calendar, of that I am very sure. And I think it is possible to copy paste events.

---

