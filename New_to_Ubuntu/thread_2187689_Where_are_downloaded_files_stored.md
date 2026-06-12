---
title: "Where are downloaded files stored?"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by fwrun2011 on 2013-11-13
Hi;
I thought I wanted to install Open Office on Ubuntu 12.04. I downloaded the .tar.gz file using Firefox in Ubuntu. When it was done downloading, a popup opened, showing the folder "etc" under "/". I attempted to extract the files but there was an error. Eventually, I decided to abandon the install, and wanted to remove the files from my system. When I right-clicked on the folder where the files were located, the delete option was greyed out. I then tried to go up to a higher level folder so I could see where the files were, but could not. It appears that the files were downloaded to the home folder, yet I could not find them there.
So where does Firefox/Ubuntu put downloaded archive files?

Thanks for your help

FW

---

### Post by Dennis N on 2013-11-13
Look at **Preferences > General > Downloads**  in Firefox to see where downloads are going.

You can't work with (modify, add, delete, etc) files in /etc because of permissions. Sudo would be required.

---

### Post by Bucky Ball on 2013-11-13
> **Dennis N said:**
> Look at **Preferences > General > Downloads**  in Firefox to see where downloads are going.

You can't work with (modify, add, delete, etc) files in /etc because of permissions. Sudo would be required.

+1. Open a file manager, go to /etc and move the tar.gz to your /Downloads folder which is in /home.

---

### Post by ajgreeny on 2013-11-13
But it is almost impossible for firefox to have saved an archive of Open Office anywhere in /etc unless you were running firefox with root permissions, something that is definitely not a good idea for security reasons, so there should be no need to move the file from /etc to your /home.

---

### Post by deadflowr on 2013-11-13
Moving the tar from /etc to /home/user is half the problem you'll face.
If you want to install openoffice, you'll need to remove libreoffice first.
They have a common file that conflicts with each other and will cause the installation to bork.

---

### Post by Johan De Cauwer on 2013-11-13
> **fwrun2011 said:**
> Hi;

So where does Firefox/Ubuntu put downloaded archive files?

FW

Standard that's in the Download directory in you Home directory.  To make that understandable next to /etc there is a /home and under that is a directory with your username, and that directory is your Home. Within that space you're king. 

Now if you ask the question where does Firefox download it's certainly in /home/username/Downloads/ You can change that place, but you didn't or you would know it. 

A possibility is that when you were downloading you got the question what do you want to do with the file. Save as... (and then it goes to Downloads) or open with an archive manager and there the default for extraction may have been / (root) and for a user /etc isn't a bad choise as name, but only that's the place where the system configuration files reside, and since you didn't have write permissions the extraction failed.

All this to say the probable place where the tar file was placed is /tmp - the placeholder for the file during the extraction.

If not, you'll have to download it again... :-)

---

### Post by Bucky Ball on 2013-11-13
> **deadflowr said:**
> Moving the tar from /etc to /home/user is half the problem you'll face.
If you want to install openoffice, you'll need to remove libreoffice first.
They have a common file that conflicts with each other and will cause the installation to bork.

+1. Even then I found it a complete pain. They are virtually identical so what has OO got that Libreoffice hasn't, just out of curiousity?

---

### Post by Johan De Cauwer on 2013-11-13
> **Bucky Ball said:**
> +1. Even then I found it a complete pain. They are virtually identical so what has OO got that Libreoffice hasn't, just out of curiousity?
I believe it's the reverse: OO moves slower, so if you're used to it... ;-) But ok, in Linux it's the voyage that counts, not the destination.

---

### Post by deadflowr on 2013-11-13
> **Bucky Ball said:**
> +1. Even then I found it a complete pain. They are virtually identical so what has OO got that Libreoffice hasn't, just out of curiousity?

Beats me.
Probably some arcane function that only 1 in 1000 users actually utilizes and when the other version doesn't have that function complains that the other is garbage.

Back on topic though, the simplest thing the OP can do is to copy the tar from where ever it is and paste it into anywhere in the home folder.
No need to run as root if you copy into the home folder.

Then you can delete the original whenever you want, if you want. 

Does sound like the OP ran firefox as root, though.
Makes the most sense.

---

### Post by fwrun2011 on 2013-11-13
Hey guys;
Thanks for all the help. I think I was mistaken when I said the download went to /etc. Firefox is set to download to /downloads, but the file(s) is not there. I probably did select the archive manager option when I attempted to install. I don't think anything could have been saved to /root, since I would have been asked to provide the root password, right? Actually, I did create one, but even when I did log in as root, I could not see the contents of the root directory.
Could it be possible that I never actually downloaded anything? What i saw was the popup window with a folder labeled as / with the folder icon immediately following. When I clicked that, I saw the folders and files that I thought I had downloaded. Then I attempted to extract a couple of them, and got the error message (I don't recall what error it was, except that extraction failed).
I don't really need Open Office, but I thought it might be able to open a MS Access 2010 .accdb file, since LibreOffice could not. I believe it can open an .mdb file though,so I can save the .accdb file as .mdb for read-only purposes. 

I haven't had much experience with Ubuntu, or any other Linux distro, so I went to the library today and picked up a book, which covers Ubuntu 12.04, which is what I have installed.

FW

---

### Post by deadflowr on 2013-11-13
I'm clueless on what you've actually done.
But for future notes, you can set firefox to either save in a specific place or ask you when it wants to save a file.
look in edit > preferences  > general.
You can also look in tools > downloads to see if the file was downloaded.

The generic folder that files are downloaded to is not simply /downloads, but /home/username/Downloads.
Signifying that the file is in the users Home folder.

However that goes to pot if running as root.
Root has it's own home, /root.
And how firefox works/saves while running root is something I would never know, because I would never run firefox as root.(On purpose)

Again, though, I don't really know what you've done, so...

---

### Post by Dennis N on 2013-11-13
Here is a way to find a downloaded file if it is still around:

With Firefox running, CTRL+SHIFT+Y will bring up the downloads window which shows all recently downloaded files (until you clear it out). Your downloaded file will be shown there, most recent at the top. Right-click and select 'open containing folder' and your file should be there, unless it has been deleted with the file manager sometime after the download.

---

### Post by Dennis N on 2013-11-13
Here's what likely happened:

**Firefox does not always save files by default.** In some cases, it will show a dialog offering to open the file with a particular application as the default action. For archives, it offers to open them in archive manager. See attached image.

To save the file, you have to select the 'Save File' option. Then, it will be saved to the downloads folder instead.

If you chose the default action to open with the archive manager, the files/folders can then be extracted with the 'Extract' Button to your home folder (or some subfolder). You also have the option to also save the download with Archive > Save. Otherwise, unless saved, the only copy is in /tmp from which it will disappear.

Firefox behavior regarding files is set in **Preferences > Applications**

---

### Post by Bucky Ball on 2013-11-14
... or, in Firefox, you could click the downward pointing arrow in the top right corner of the screen. You will see your download. Right click and 'Open folder'. That easy.

---

### Post by 3rdalbum on 2013-11-14
As others have mentioned, if you just "open" a downloaded file in Firefox it won't save the file anywhere. That's a bit of a gotcha and it's tripped me up once or twice.

Openoffice is Libreoffice but with fewer features, so unfortunately I don't foresee your file opening on Openoffice.

---

