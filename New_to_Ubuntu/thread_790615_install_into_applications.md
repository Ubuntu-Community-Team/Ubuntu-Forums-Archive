---
title: "install into applications"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-11
I get the following message when I am trying to install real player.

Welcome to the RealPlayer (11.0.0.4028) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/shawn/Desktop/RealPlayer]: 

How do I specify that I want this in my Applications?

---

### Post by nowshining on 2008-05-11
create  a folder in home either hidden .realplayer or shown realplayer or whetname u wnt and then when asked  inpuut for example.

/home/shawn/.realplayer/


u can use the TAB key for completion.

and then hit enter.

---

### Post by saskatchewan on 2008-05-11
I think that something did not work out quite right.

There is nothing in my RealPlayer file and the message that I get is:

mkdir: cannot create directory `/home/shawn/.kde': Permission denied
..Succeeded.
Configuring Mozilla...
Installing .mo locale files...
.Setting selinux context...
/usr/share or /usr/bin no write-permission...skip.

RealPlayer installation is complete.
Cleaning up installation files...
Done.

shawn@shawn-laptop:~/Desktop$

---

### Post by imT on 2008-05-11
try Helix player 	;)  
see [this]("https://player.helixcommunity.org/2004/unix/helixrealfaq.html")

---

### Post by saskatchewan on 2008-05-11
I tried this site but I don't see an answer to what I am looking for.

---

### Post by HotShotDJ on 2008-05-11
[LIST=1]
[*]Get the RPM for RealPlayer 11 Gold [here]("https://player.helixcommunity.org/Image:2005/downloads"). NOT Helix Player 11.
[*]Using Synaptic Package Manager, install "alien" (or "sudo apt-get install alien" from the command line)
[*]From a terminal, navigate to the location of the RPM file you just downloaded ("cd path/to/file")
[*]In the terminal, type "alien HelixPlayer-11.0.0.4052-20080318.i586.rpm --scripts"
[*]Exit the terminal.  Open Places --> Home Folder, navigate to the location of the RPM and the new DEB file.  Double-Click on the DEB file to install (Note: You may get a script error.  It is safe to ignore the error)
[*]The executable is /opt/helix/HelixPlayer/hxplayer
[*]You may manually add it to your Applications Menu.
[/LIST]

---

### Post by saskatchewan on 2008-05-11
I do not understand step 3 of the instructions you just gave

---

### Post by saskatchewan on 2008-05-11
THis is the message that I get:

ldconfig deferred processing now taking place
shawn@shawn-laptop:~$ cd path/to/file
bash: cd: path/to/file: No such file or directory
shawn@shawn-laptop:~$ cd path/to/realplayer
bash: cd: path/to/realplayer: No such file or directory
shawn@shawn-laptop:~$

---

### Post by saskatchewan on 2008-05-11
There is an icon in my Applications menu but when I click it I get 

Failed to execute child process "realplay" (No such file or directory)

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> THis is the message that I get:

ldconfig deferred processing now taking place
shawn@shawn-laptop:~$ cd path/to/file
bash: cd: path/to/file: No such file or directory
shawn@shawn-laptop:~$ cd path/to/realplayer
bash: cd: path/to/realplayer: No such file or directory
shawn@shawn-laptop:~$
No, no, no.... you need to replace path/to/file with the actual location of the file.  I have no way of knowing what that path might be.

---

### Post by SunnyRabbiera on 2008-05-11
well if you just want realplayer you can grab it here:
[this topic]("http://ubuntuforums.org/showthread.php?p=4737528")

the plug in should work too.

---

### Post by saskatchewan on 2008-05-11
What is the actual location?

I have no idea where things went?

I created a file RealPlayer but it is empty

---

### Post by HotShotDJ on 2008-05-11
> **SunnyRabbiera said:**
> well if you just want realplayer you can grab it here:
[this topic]("http://ubuntuforums.org/showthread.php?p=4737528")

the plug in should work too.True.  But what happens next time the OP wants to work with an application that is distributed only in RPM or BIN format?

"Give a man a package, he installs for a day.  Give a man a packager, he installs for a lifetime."  :)

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> What is the actual location?

I have no idea where things went?

I created a file RealPlayer but it is emptyI have absolutely no way of knowing where you downloaded the file.  It might be in your home directory.  Check there first.  What do you mean "I created a file RealPlayer" ??

---

### Post by saskatchewan on 2008-05-11
I downloaded the bin file to the desk top but have no idea where things went afte that

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> I downloaded the bin file to the desk top but have no idea where things went afte thatFirst of all, if you are using the steps I gave you, the bin file will do you no good.  It is the RPM file that you need.  If you did actually download it to your desktop, it would be located in /home/USER/Desktop  (replace USER with your actual user name).  But you would also be able to see an icon for it on your desktop.

But like I said, the bin file will not help you using the steps I gave you.  You need the RPM file.

---

### Post by SunnyRabbiera on 2008-05-11
> **HotShotDJ said:**
> True.  But what happens next time the OP wants to work with an application that is distributed only in RPM or BIN format?

"Give a man a package, he installs for a day.  Give a man a packager, he installs for a lifetime."  :)

you mean the hard way...

well converting a package from a rpm to a debian installer is easy if you know how, but it can be a pain sometimes.

---

### Post by HotShotDJ on 2008-05-11
> **SunnyRabbiera said:**
> well converting a package from a rpm to a debian installer is easy if you know how, but it can be a pain sometimes.Its usually very easy.  Here, the problem would not be solved by downloading the actual DEB file, since the main issue is that the OP is unable to locate the downloaded files.  Once we get over that hurdle, the rest should be easy (famous last words, I know!)

---

### Post by saskatchewan on 2008-05-11
I downloaded the RPM file and ran the instructions now this  is the message that I get.

shawn@shawn-laptop:~$ cd ~/Desktop/realplayer.rpm
bash: cd: /home/shawn/Desktop/realplayer.rpm: No such file or directory
shawn@shawn-laptop:~$ sudo apt-get install alien
[sudo] password for shawn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shawn@shawn-laptop:~$

---

### Post by saskatchewan on 2008-05-11
what do I do now?

---

### Post by SunnyRabbiera on 2008-05-11
alright you have alien, thats a start...
Now what I want you to do is to place your downloaded realplayer rpm into a directory you feel good with like your home directory.
after this you may want to install nautilus-open-terminal, as it will help, you can install it in the terminal if you with.
after that is installed log out and log back in, and tell me when you do so.

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> I downloaded the RPM file and ran the instructions now this  is the message that I get.

shawn@shawn-laptop:~$ cd ~/Desktop/realplayer.rpm
bash: cd: /home/shawn/Desktop/realplayer.rpm: No such file or directory
shawn@shawn-laptop:~$ sudo apt-get install alien
[sudo] password for shawn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shawn@shawn-laptop:~$
Well.. you need the actual name of the file. Just typing in the name that you think it should be won't help. :) The name of the file is HelixPlayer-11.0.0.4052-20080318.i586.rpm
Are you SURE that file exists in your Desktop folder?  You can find out using the "ls" command (without quotes) in your terminal.

---

### Post by HotShotDJ on 2008-05-11
> **SunnyRabbiera said:**
> 
after this you may want to install nautilus-open-terminalYes. Nautilus-open-terminal is a wonderful thing!

---

### Post by saskatchewan on 2008-05-11
After typing 1s is says that there is a RealPlayer file on my desktop.

And I installed the nautilus open terminal thing but don't know what to do with it.

---

### Post by saskatchewan on 2008-05-11
Here is another message that I got:

shawn@shawn-laptop:~$ alien HelixPlayer-11.0.0.4052-20080318.i586.rpm
Must run as root to convert to deb format (or you may use fakeroot).
shawn@shawn-laptop:~$

---

### Post by SunnyRabbiera on 2008-05-11
alright if you got it installed, then do as I said and take that realplayer .rpm file and open up your home directory and put it in there.
now that the nautilus terminal is in there go up to "file" and select "open in terminal"
then type in ls (small L)
then type in sudo alien HelixPlayer-11.0.0.4052-20080318.i586.rpm
after its done it should create a debian installer file.

---

### Post by HotShotDJ on 2008-05-11
Hang on.  I screwed up. :redface:  The file name should be "RealPlayer11GOLD.rpm"   Sorry about that.

---

### Post by saskatchewan on 2008-05-11
This is the message that I got:

shawn@shawn-laptop:~$ sudo alien HelixPlayer-11.0.0.4052-20080318.i586.rpm
[sudo] password for shawn: 
File "HelixPlayer-11.0.0.4052-20080318.i586.rpm" not found.
shawn@shawn-laptop:~$ sudo alien HelixPlayer-11.0.0.4052-20080318.i586.rpm
File "HelixPlayer-11.0.0.4052-20080318.i586.rpm" not found.
shawn@shawn-laptop:~$ sudo alien RealPlayer11GOLD.rpm
File "RealPlayer11GOLD.rpm" not found.
shawn@shawn-laptop:~$ 


\

---

### Post by saskatchewan on 2008-05-11
Now I have a folder on my desktop called RealPlayer-11.0.0.4028

What do I do with it?

I already have a real player icon in my applications but when I click it it just gives an error

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> This is the message that I got:

shawn@shawn-laptop:~$ sudo alien HelixPlayer-11.0.0.4052-20080318.i586.rpm
[sudo] password for shawn: 
File "HelixPlayer-11.0.0.4052-20080318.i586.rpm" not found.
shawn@shawn-laptop:~$ sudo alien HelixPlayer-11.0.0.4052-20080318.i586.rpm
File "HelixPlayer-11.0.0.4052-20080318.i586.rpm" not found.
shawn@shawn-laptop:~$ sudo alien RealPlayer11GOLD.rpm
File "RealPlayer11GOLD.rpm" not found.
shawn@shawn-laptop:~$ 
Ok.  Go to Places --> Home Folder.  Look in that window.  Does the file "RealPlayer11GOLD.rpm" appear in there anywhere?  The EXACT file name, not just any file or fold that happens to contain the name "realplayer" in it.

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> Now I have a folder on my desktop called RealPlayer-11.0.0.4028

What do I do with it?

I already have a real player icon in my applications but when I click it it just gives an errorThat looks like it might be the DEB file that were are trying to get.  Please VERIFY.  Make SURE the complete file name is "realplayer_11.0.0.4028-20080226_i386.deb"  Not ANYTHING else.

---

### Post by saskatchewan on 2008-05-11
THere is a folder called realplayer_11.0.0.4028-20080226_i386.deb on the desktop

---

### Post by saskatchewan on 2008-05-11
could this installation possibly be any worse?

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> could this installation possibly be any worse?Sure it could.  Back in the day, after I finished walking to school in the snow, barefooted and up hill both ways, I used to have to compile things from source. :)

Ok... you should be able to just double-click on that file to start the gdebi installer.

After it is installed, you'll have to start it from the terminal (for now, we can fix that later) with the command: ```
 /opt/real/RealPlayer/realplay
```

---

### Post by saskatchewan on 2008-05-11
Hey

I get an error message when I click the icon.  However, I do have an executable pathway, I just don't know how to associate it with the icons.  

When I enter /opt/real/RealPlayer/realplay in the terminal it runs.

How do I make the association?

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> When I enter /opt/real/RealPlayer/realplay in the terminal it runs.

How do I make the association?Ok... when you say "make the association," I assume you want to add it to Applications --> Sound & Video (which is a perfectly sensible thing to do)


[LIST=1]
[*]RIGHT click on Applications
[*]Highlight "Sound & Video" in the left panel
[*]On the right side of the dialog box, click "New Item"
[*]Create Launcher dialog will appear
[*]In the Name box... type Real Player
[*]In the command box, type /opt/real/RealPlayer/realplay
[*]In the comment box, type Play Real Media content
[*]Now, click Choose Icon button
[*]Click "Browse" and browse to /opt/real/RealPlayer/share/icons
[*]Click Open
[*]Choose an Icon
[*]Click Ok, the Ok again.
[*]Now close the menu editor.
[*]Done
[/LIST]

OH... while your in there, delete the Real Player menu item that isn't working.

---

### Post by saskatchewan on 2008-05-11
How do I move the RealPlayer file from my desktop to my Home Folder?  It says that I do not have permission

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> How do I move the RealPlayer file from my desktop to my Home Folder?  It says that I do not have permissionRemember, that file is only the installer.  You can actually delete it.  But if you want to save it, in a terminal, type```
mv Desktop/name-of-file /home/USER/.
```IMPORTANT:  Replace "name-of-file" with the actual, compete name of the file.  Replace "USER" with your user name.  Don't forget the "dot" at the end of the command.

If you get a permission error with that command, add sudo to the beginning of it.

---

### Post by saskatchewan on 2008-05-11
It won't let me delete it either.

This is the message I get when I try to move it.

shawn@shawn-laptop:~$ mv Desktop/RealPlayer-11.0.0.4028/home/shawn/.
mv: missing destination file operand after `Desktop/RealPlayer-11.0.0.4028/home/shawn/.'
Try `mv --help' for more information.

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> It won't let me delete it either.

This is the message I get when I try to move it.

shawn@shawn-laptop:~$ mv Desktop/RealPlayer-11.0.0.4028/home/shawn/.
mv: missing destination file operand after `Desktop/RealPlayer-11.0.0.4028/home/shawn/.'
Try `mv --help' for more information.Right.  First, that is not the complete file name.  Second, your forgot to put a space between the the old file and the new one.  Try this command:
```
sudo mv Desktop/realplayer_11.0.0.4028-20080226_i386.deb /home/shawn/.
```
Don't forget the space between "deb" and "/home"

---

### Post by saskatchewan on 2008-05-11
It says that I do not have permission to do anything to the file because the owner is "root".

How do I get rid of this thing?

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> It says that I do not have permission to do anything to the file because the owner is "root".

How do I get rid of this thing?You'll need to do it from the terminal.  Go back to my previous post.  Notice my comment to add "sudo" to the beginning of the command to resolve the problem with permissions.

---

### Post by saskatchewan on 2008-05-11
What is the command for delete?

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> What is the command for delete?rm

---

### Post by saskatchewan on 2008-05-11
shawn@shawn-laptop:~$ cd Desktop
shawn@shawn-laptop:~/Desktop$ rm RealPlayer-11.0.0.4028
rm: cannot remove `RealPlayer-11.0.0.4028': Is a directory
shawn@shawn-laptop:~/Desktop$ 

This is what it says

---

### Post by saskatchewan on 2008-05-11
It just keeps saying that there is no such directory even though it is right on the desktop.

RealPlayer-11.0.0.4028$

---

### Post by HotShotDJ on 2008-05-11
> **saskatchewan said:**
> shawn@shawn-laptop:~$ cd Desktop
shawn@shawn-laptop:~/Desktop$ rm RealPlayer-11.0.0.4028
rm: cannot remove `RealPlayer-11.0.0.4028': Is a directory
shawn@shawn-laptop:~/Desktop$ 

This is what it saysNow I'm confused.  Where did that directory come from?  Oh well.  At this point, the EASIEST thing to do is to install midnight commander to deal with this.

Open a terminal.  Type sudo apt-get install mc
Next, run mc as root... sudo mc
Use your curser up and down buttons to navigate to /Desktop
Press Enter
Highlight the directory to delete (using cursor up and down buttons)
Press F8
Type exit to exit

---

### Post by nowshining on 2008-05-12
for directories u put

sudo (if owned by root) rm -rf pathtofile/directory

---

### Post by Sean4000 on 2008-05-15
Hello I have a similar problem. I'm on hardy xubuntu 64. I am trying to install nuke, shake, Maya, pixel, and light zone but I get this message when i click the executables.::


Failed to open "Nuke5.0v1-5748-linux-x86-release-32-installer".
Failed to execute child process "/home/spburns/Desktop/Nuke5.0v1-5748-linux-x86-release-32-installer" (No such file or directory).

The message is the same for the other apps but the names of the aps change obviously.

I am at a loss and very upset because I need these apps up and running asap.

Any help would be hot.

---

### Post by Xiong Chiamiov on 2008-05-15
> **Sean4000 said:**
> Hello I have a similar problem. I'm on hardy xubuntu 64. I am trying to install nuke, shake, Maya, pixel, and light zone but I get this message when i click the executables.::


Failed to open "Nuke5.0v1-5748-linux-x86-release-32-installer".
Failed to execute child process "/home/spburns/Desktop/Nuke5.0v1-5748-linux-x86-release-32-installer" (No such file or directory).

The message is the same for the other apps but the names of the aps change obviously.

I am at a loss and very upset because I need these apps up and running asap.

Any help would be hot.
It'd really be better to start a new thread with a link to this one, because
a) this thread is really long - most people won't read it because they think someone's already answering questions
b) it's easier to get a grasp on your specific problem if we don't have to skip over 5 pages

That said, you may have to either add executable permissions to the files, or launch them through the terminal.  You should most definitely take a read of [this guide]("http://monkeyblog.org/ubuntu/installing/"), as well.

---

### Post by nowshining on 2008-05-15
Xiong Chiamiov u could increase the # of pages shown per page thru the Control Panel -- options sections, etc..

---

