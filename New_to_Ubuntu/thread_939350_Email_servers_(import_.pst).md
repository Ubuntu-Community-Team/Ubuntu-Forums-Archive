---
title: "Email servers (import .pst)"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Dunchillin on 2008-10-05
Hi. I apologise for posting a question I know has been asked before, but I have been unable to find an answer and am desperate!
Having been finally forced to convert to Ubuntu after a spectacular crash of Windows (ptooi) I am in need of an email server that can import a .pst file.  I have no copy of Windows (ptooi) anywhere - nor do I ever want to see one again - just the backed up .pst files. 

Please, please can anyone help?! 

I look forward to discovering Ubuntu :)

Cheers

---

### Post by patrickballeux on 2008-10-05
I was able to recover my mails and calendar using the "readpst" package.

It is not perfect, but it saved my life :)

Also, you could install a Windows inside a vmware/virtualbox, import your PST in there and then move your mails with a google account...  

Good luck!

---

### Post by Dunchillin on 2008-10-05
Wow that was a quick reply - thanks!  I have downloaded the readpst package, but now what?!  How do I get it to do...anything?
Does it work with Evolution?

---

### Post by ayenack on 2008-10-05
You could try this. It's old but should work. Only runs on windows.

[http://outport.sourceforge.net/](http://outport.sourceforge.net/)

Another way to do this would be to install Mozilla suite on windows then use Mozilla to import the files for outlook then export from Mozilla to mbox format then import to Evolution on Ubuntu.

If you happen to have the E-mails saved on google you could use imap to download them.

---

### Post by Dunchillin on 2008-10-05
I can't access Windows at all.  All I have are the back up files on an external drive.  I tried to plug the external into a friend's comp still running Windows but since I mounted it in Ubuntu it won't show up in Windows.

I still can't figure out readpst either.  It seemed to install automatically but then what does it do and how do I make it do it?  Sorry I'm such a novice...

---

### Post by patrickballeux on 2008-10-06
It is a command line software...  

Open a terminal, and type in "man readpst".  You will see all the options that you can setup on the command line...

> mkdir outputfolder
> readpst -cv -S -o outputfolder mypstfile.pst

It will extract all your mails into the subfolder outputfolder.  After that, you can import that folder into Evolution.  the "-S" options is giving the the options to create the folders that you had in your Exchange account (if you had any...)

As I said, it is not perfect, but can save your butt... :)


Good luck!

---

### Post by Dunchillin on 2008-10-07
> **ayenack said:**
> 

Another way to do this would be to install Mozilla suite on windows then use Mozilla to import the files for outlook then export from Mozilla to mbox format then import to Evolution on Ubuntu.

Sorry, but how do I do this?  I have successfully accessed my files through a friends laptop and now have them installed once more their Outlook awaiting my next move.

A beer to the first one who helps!

---

### Post by Dunchillin on 2008-10-08
Okay, what I have done is import all my contacts, emails etc into thunderbird on the windows computer, and then copied the entire profile folder contents onto an external drive.  Now what I want to do is replace all the profile files on this computer (running Ubuntu) with my saved ones, but I have no idea how to find the profile folder in Ubuntu.  Please tell me this and I swear I won't ask any more email related questions!

---

### Post by MystikIncarnate on 2008-10-22
the email files are all hidden as "." files in your home folder, simply go to the view menu and select the show hidden files checkbox in your file explorer window-y type thing in ubuntu and you should see a pile of folders pop up... now it's just a matter of figuring out which one is the data folder for the email client, dropping the backup files from thunderbird into there, and firing up the email client in the gui... it should pickup the new files as if they were it's own (as long as the client is compatible with the files... eg. another thunderbird).

good luck

---

### Post by cariboo on 2008-10-22
The directory you want is ~/.mozilla-thunderbird, all you emails,contcts and seeting are located in xxxxxxxx.default where x is a random string of numbers and letters, just copy the default folder from window to to ~/.moailla-thunderbird and then edit profile.ini to use you just copied default folder.

Jim

---

### Post by Dunchillin on 2008-11-04
Tried all this and it didn't work!
I copied the folder over, changed the .ini, but then thunderbird refused to start up, saying  a version of it was already running.  I've restarted the comp, removed the old profile file but no difference.

I'm enjoying ubuntu, but am finding it quite hard to work out.  Programs I download through the synaptic package manager don't install properly (something to do with possibly non-existent /havp folders...I've asked on another thread!) and I don't really know how to phrase my questions on here (cos I don't understand the fkin problem half the time!) so generally sit here aimlessly searching and typing things in terminal til I've caused god knows what mischeif to my computer and forgotten what the bloody issue was in the first place!

Anyway, thanks for all your help :)

---

