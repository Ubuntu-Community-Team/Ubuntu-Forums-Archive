---
title: "Posting/Uploading split-archive binaries to UseNet - The GUI way."
date: 2013-05-03
forum: New to Ubuntu
---

### Post by DenHeldert on 2013-05-03
In this guide I will explain how to upload split-(rar)archives to UseNet without using the terminal.
OK, you need to use the terminal a little bit to set it all up. But once that is done, we can click-click-click our files to UseNet.


The following software is used:

*rar*
- Used to create archives using the rar-format.
*File-Roller*
- Used to make split-rar-archives.
*PyPar2*
- Used to generate parity-files.
*JBinUp*
- Java-based program to actually upload the files.
*dconf-editor*
- Used for many purposes, but we will just use it to set the compression leven of file-roller. (to be more precise: disable compression)
This wil speed up the generation of archives significantly.


**The Setup**

rar, File-Roller, and PyPar2 are available in the software-centre. So fire it up and install them one by one. (File-Roller shows up as 'Archive-Manager')
PyPar2 is obviously written in Python, so it will install some dependicies. Be sure NOT to uncheck them.

dconf-editor is installed using the terminal
```
sudo apt-get install dconf-editor
```

JBinUp is available [online]("http://www.jbinup.com").
Click on the link next to 'Actuelle Version' , scroll down and download the latest version.
After this is done, extract the downloaded zip-file and assign  the files a nice permanent location on your hard drive.
After this, right-click JBinUp.jar choose Properties and place a checkmark next to 'Is executable' 
Click OK to save the settings and exit the dialog.

Now we are going to set the compression level of file-roller to 0.

```
dconf-editor
```

Navigate your way to org -> gnome -> file-roller -> general
Set the value for compression-level to very-fast ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBdlhSelhMZVVSVzg/edit?usp=sharing"))

So far our setup, let's get to it!

[B]
Creating a split-archive[/B]

Launch file-roller.
Click the green + sign.
Give your archive a name.
Choose the .rar format from the drop-down list
Click 'Other Options'
PLace a checkmark next to 'Split into volumes of' and choose a size between ~50-100MB ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBbGtlMGNEek5vd2M/edit?usp=sharing"))
Click the 'Create' button. 
Drag the files into the newly opened window and it starts packing them right away.
Sit back and wait patiently for file-roller to finish. ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBR05Eck1sWGoxTzA/edit?usp=sharing"))


**Generating parity (PAR2) files**

Launch PyPar2
Choose the tab labeled Create
Right-click in the white square and choose 'Add Files'
Select the entire archive you just made and click the 'Open' button.
Click 'Go'
Click 'Save' in the newly opened Window.
Sit back and wait patiently for PyPar2 to finish. ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBM2twXy1hbDhhTXc/edit?usp=sharing"))


**Creating a nfo-file** (optional)

Open your favorite text-editor.
Give some relevant info on what you are posting. ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBY29LeTFrc2JMblU/edit?usp=sharing"))
Save the file as *.nfo
Place it in the same folder as your archive and PAR2-files.

You should now have your PAR's, the splitted rar-archive and an optional nfo ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBUkl0SkU1WV9UZjQ/edit?usp=sharing"))


**Posting it all on UseNet**

Navigate to the folder where you saved JBinUp.
Right-click 'JBinUp.jar -> Open With -> OpenJDK Java 7 Runtime. ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBRlFkemh3dTRNSHc/edit?usp=sharing"))
Answer the nag-screen and choose File -> Settings

*Obviously, you only have to do the following 3 steps once:*

Server Settings: ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBcnh5dWpmbG5ZcG8/edit?usp=sharing"))
Add the data provided by your UseNet-Provider*****
Place a checkmark next to 'Use Server for Uploads'
Place a checkmark un the 'Active' colomn.

Poster Settings: ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBTllEbFNqVlJHYU0/edit?usp=sharing"))
Click 'Add Sender'
Choose a nickname and a fake email-address.
Place a checkmark next to 'Default'
Click 'OK'

Newsgroup Settings: ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBYlRWaV9TbVZJTHc/edit?usp=sharing"))
Add some groups you'll be likeliy to post to.
Add them one by one.
Delete the entry 'alt.binaries.jbinup.test'

***** [SIZE=1]Usually one only needs to [SIZE=1]set[/SIZE] the Server Address, number of connections, username, password and an optional nickname for the server configuration.
There is no way I can help you with that, as every UseNet-Provider uses different settings.[/SIZE]


After all of this is done, click 'OK' to save the settings and exit the settings configurator.

Click the + sign.
Enter a name for the job.
Click 'Add'
Choose your archive, PAR2 files, and the (optional) nfo.
Place them in a nice order using 'Move file up' and 'Move file down' buttons.
The unwritten rule on UseNet is: nfo first, the empty parity file second, your archive third and then the PAR2 files in ascending order. ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBbjhhejR2T2FtazA/edit?usp=sharing"))

Click 'Forward'
Choose the group(s) you want to post to.

The header settings are just fine, only edit them unless you know what you are doing. If you do not know the consequences of editing these settings, leave them.

Click 'Add job'
Click either the play-button to start uploading your files, or add another job to to queue. ([screen]("https://docs.google.com/file/d/0B3fLyJeN1WiBNjlEMk5VZVYyN2s/edit?usp=sharing"))



That's it, [DONE]("http://www.nzbindex.nl/search/?q=denheldert&age=&max=25&minage=&sort=agedesc&minsize=&maxsize=&dq=&poster=&nfo=&hidespam=0&hidespam=1&more=0")!
Hope it helps some click-loving newbies like me.


Regards, DenHeldert.

---

