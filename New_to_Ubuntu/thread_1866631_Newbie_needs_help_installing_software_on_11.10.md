---
title: "Newbie needs help installing software on 11.10"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by Carlynn on 2011-10-21
Yesterday I went to the software center and installed 7zip, it told me that it was installed but I could not see it anywhere when I looked for it. It showed up in the launcher as a grey box with a question mark on it but when you hold the mouse over it it said 7 zip. I tried to unzip a rar file but it would not work.

Today I searched online and found another program to use named winrar for ubuntu, I them downloaded it and there were 3 different methods to install and none of them would work.

This is the last one I tried.

1. Download WinRAR for Linux and latest WinRAR @ [www.rarlab.co&#65279;m](www.rarlab.co&#65279;m)

2. Then extract WinRARLinux.tar.gz

3. Open the extracted folder and place the wrar*.exe in the WinRAR Installers folder

4. Then Run WinRAR.sh and click Install (select the setup)

I followed these instructions and when I did it said it was installed and a box to click ok came up, then it said to run the program.
After clicking ok the same box came up with install and run but the run was greyed out so you could not run the program.
I just kept going around in circles and it does not show up anywhere that it is installed.

This leaves me feeling this program is not going to be for installing stuff to if it is this difficult.
Do you have any suggestions for help on installing stuff.

I did finally get a disk burned after spending all day trying with Brasero yesterday.

Sorry for the long post but I understand so much more now I don't want to give up on this now but the installing stuff has me stumped.

---

### Post by Paqman on 2011-10-21
You did the right thing with 7zip, Software Centre is always the best place to look for software. You'll find rar/unrar is available there as well.

On Linux we get pretty much all our software from the official repositories through package management apps like Ubuntu Software Centre. Going to random sites and manually downloading install packages is the Windows way of doing it, and you'll soon realise what a sucky way to handle software it really is.

---

### Post by critin on 2011-10-21
> **Carlynn said:**
> Yesterday I went to the software center and installed 7zip, it told me that it was installed but I could not see it anywhere when I looked for it. It showed up in the launcher as a grey box with a question mark on it but when you hold the mouse over it it said 7 zip. I tried to unzip a rar file but it would not work.

Today I searched online and found another program to use named winrar for ubuntu, I them downloaded it and there were 3 different methods to install and none of them would work.

This is the last one I tried.

1. Download WinRAR for Linux and latest WinRAR @ [www.rarlab.co&#65279;m]("http://www.rarlab.co%EF%BB%BFm")

2. Then extract WinRARLinux.tar.gz

3. Open the extracted folder and place the wrar*.exe in the WinRAR Installers folder

4. Then Run WinRAR.sh and click Install (select the setup)

I followed these instructions and when I did it said it was installed and a box to click ok came up, then it said to run the program.
After clicking ok the same box came up with install and run but the run was greyed out so you could not run the program.
I just kept going around in circles and it does not show up anywhere that it is installed.

This leaves me feeling this program is not going to be for installing stuff to if it is this difficult.
Do you have any suggestions for help on installing stuff.

I did finally get a disk burned after spending all day trying with Brasero yesterday.

Sorry for the long post but I understand so much more now I don't want to give up on this now but the installing stuff has me stumped.

Hi, Carlynn;

Did you search Software Center for whatever you're looking for?  Most everything is there so you might not have to install from 7zip or winrar.  When I do have to download and install something, a right click will give me the option to have Software Center do the installing.  Most of the work is done by Software Center.

critin

---

### Post by old_yarrow on 2011-10-21
As critin said, the software centre is the simplest way to go to install software.

If you still need to access rar files, then the stock ubuntu file-roller utility can be used.  Note - 'rar' must be installed.  Install this through the software centre.  After this, just double click on rar files and you should be good to go.

---

### Post by Carlynn on 2011-10-21
Thanks for your help.  I did the double click and was able to upzip my file.  I did install it from the software center but I thought it was not working because I can not find either the 7 zip or the Rar compression in my applications.

I have been reading web pages all day and there seems to be other people who wonder this same question as to why some things do not show up in the applications.

I tried about a dozen different things to see if I could get see if they were installed but all of them failed.  There is so many different versions I guess the instructions were for a different version.  I have the newest 11.10.

I am a newbie to ubuntu so have so find out so many things.

---

### Post by bodhi.zazen on 2011-10-21
For additional information see:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

In general you should install applications from the package manager (apt) if at all possible.

You can install from soruce if the package is not in the ubuntu repositories or if a new version exists (new version not in the repos), however, if you do so you then become responsible for maintaining the package, including reading the README and using the packages mailing list for support if needed ;

---

### Post by oldos2er on 2011-10-22
> **Carlynn said:**
> I have been reading web pages all day and there seems to be other people who wonder this same question as to why some things do not show up in the applications.

Both rar/unrar and 7zip are command line applications, which is why they don't show up on any GUI menu.

I don't use Unity or Gnome 3, but see if there's an graphical app called Archive Manager. It's able to use any CLI compression tools you may install.

---

### Post by critin on 2011-10-22
> **Carlynn said:**
> Thanks for your help.  I did the double click and was able to upzip my file.  I did install it from the software center but I thought it was not working because I can not find either the 7 zip or the Rar compression in my applications.

I have been reading web pages all day and there seems to be other people who wonder this same question as to why some things do not show up in the applications.

I tried about a dozen different things to see if I could get see if they were installed but all of them failed.  There is so many different versions I guess the instructions were for a different version.  I have the newest 11.10.

I am a newbie to ubuntu so have so find out so many things.

Search in Software Center for 'Display a list of all applications' or, awn-applet-main-menu
It's in my 11.04 SCenter, I haven't checked in 11.10.  You may be able to add it through synaptic though if it's not.

critin

---

### Post by egalvan on 2011-10-22
> **Carlynn said:**
> 
I have been reading web pages all day and there seems to be other people who wonder this same question as to **why some things do not show up in the applications.**
[B]
I tried about a dozen different things to see if I could get see if they were installed but all of them failed.[/B]
  There is so many different versions I guess the instructions were for a different version.  I have the newest 11.10.

I am a newbie to ubuntu so have so find out so many things.

Some software is command-line only, so it does not normally show on th menus, which, by default, show only GUI-oriented apps.

"Ubuntu Software Center" has an "**Installed Software"** menu item.
Its on the left side of the box.
Click on the "show technical" option to expand the listing.

"Synaptic Package Manager" also has an "**Installed Packages**" option..
this will show everything installed on your system...


Synaptic also has a "History" menu item which will show you
"**History of installed, upgraded and removed software packages.**"

---

### Post by d4m1r on 2011-10-22
Search Software Centre for "rar" and someone with a lot of ratings should come up...It is basically a plugin to the built in Ubuntu extractor app that does have a GUI (same one when you open a .zip) and basically adds the ability to read/open/extract .rar's

---

### Post by 3rdalbum on 2011-10-23
As said before, 7zip and Unrar are GUI programs on Windows. On Windows, you end off needing about seven different archive managers, one for each format.

On Linux, the 7zip and Unrar packages merely plug into the standard GUI archive manager program, so it now supports those different file types.

So basically it's easier than Windows!

---

