---
title: "FTP tools needed"
date: 2006-11-02
forum: Programming Talk
---

### Post by smithveg on 2006-11-02
Hi.

I need a FTP tools in ubuntu. Before this, i have try to use the 'Connect to Server' which is come with the ubuntu default installation. I noticed that is no way for me the change the file permission.

I know a tools SmartFTP, that i'm using previously in windows platform, That allows me to right click on any file and change the permission, and do the file upload and download.

By now, i can not find a suitable FTP tools that allows me the change the file permission. Anyone have any suggestion?

Your reply would be appreciate. Thanks.

Smith

---

### Post by kidders on 2006-11-02
Hi there,

The FTP protocol doesn't provide a means of controlling permissions. Perhaps you are thinking of something else?

---

### Post by supirman on 2006-11-02
You mean you need an FTP client, which is what smartFTP is.  Try gftp in ubuntu.

You can install it via the cli or through synaptic.

---

### Post by lazka on 2006-11-02
try the filezilla 3 dev builds: [http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

---

### Post by smithveg on 2006-11-03
Thank for all the replies.

I had try to install gftp. But i found that i do not really know how to use it. Ya, of course i can do the file permission changing. But i do not really know how to upload and download the file. How about if i want to make some changes to a file?

I can see, i left hand side is all about the file in my machine's root. While right hand side is all about the file in FTP server. That's all i know.

---

### Post by FyreBrand on 2006-11-03
You need to know the way the ftp server wants you to connect.  So if it's for work or school ask a coworker or an admin and have them give you the requirements for your ftp server.

For example I need to connect to an ftp server that requires SFTP using SSH. Since gFTP doesn't have a default SFTP setting preconfigured I must use SSH2 and the port along with the other login requirements set by my admin.

If you are using KDE then you have KFTPGrabber at your disposal.  It's a very intuitive and easy to use (as in easy as FileZilla easy) ftp client.  You can still install it in gnome, but I don't like using QT apps in gnome so I bumble with gftp and learn.

---

### Post by smithveg on 2006-11-03
I didn't means i can not connect to somewhere.

I know the way to connect to FTP, i can see all the file in service side. I just do not know how to use it.

---

### Post by FyreBrand on 2006-11-03
Well if you're connecting to the server then you've figured it all out.  I'm not really sure what you're asking here.  If you connect to the ftp server then there is nothing else to do but upload or download files.  There isn't anything else to use.

---

### Post by smithveg on 2006-11-03
Ya, I can connect to a server.

I do not know how to upload.
I do not know how to download.

Just this 2 questions, because then i right click on a file. It never give me an upload or download options.

---

### Post by Vex on 2006-11-03
Doubling clicking on the file in gFTP should do the trick, or you can highlight the files, and then click on one of the arrows in the centre between the two windows.

---

### Post by smithveg on 2006-11-03
Ok, i get it works.

But i see something weird in my machine.

When i open gftp, the left hand windows is showing the file in my system, which is start by /home/veg/

Then i click Desktop because i want to download the file to desktop.
Ok, stop here.

After i had click in Desktop. I see lots of file that i should not see.
Not the ghost file. But is my previous file. For example, i see a file AAA.odt.

But, i'm sure that i have this file in Desktop before, but i had already delete it into trash, and also delete from trash a long time ago.
Why it still in my maachine?

So weird :-k Someone know what's happeing? Is this linux style?

---

### Post by FyreBrand on 2006-11-03
If you are using gFTP (graphical and not command line) there are two orange arrows between the file panes.  They move the files between panes.

Let's say your local directory is in the left pane and your remote ftp directory is in the right pane.  Click to the directory you want to be in (for both panes).  Select and highlight the file you want to transfer then click the arrow pointing toward the other pane.

Right-clicking allows you to create directories, change permissions (this can be important if you have Windows files with funky permissions) and do a bunch of other stuff.

You can also accomplish these same tasks in the menus.  The local and remote menu bars are the same as right-clicking.  The transfer menu bar gives you the option to put (upload) or retrieve (download) files along with a few other options.

gFTP is pretty powerful but not intuitively obvious to use.  I think if they looked at FileZilla or kFTPGrabber and got some UI ideas there it would be a killer app.  It's super stable and hasn't ever crashed on me.

---

### Post by smithveg on 2006-11-03
What kind of FTP you are using?
Filezilla or KFTPGrabber or gFTP. I'm not sure which is the best.

But my second question is as below

> But i see something weird in my machine.

When i open gftp, the left hand windows is showing the file in my system, which is start by /home/veg/

Then i click Desktop because i want to download the file to desktop.
Ok, stop here.

After i had click in Desktop. I see lots of file that i should not see.
Not the ghost file. But is my previous file. For example, i see a file AAA.odt.

But, i'm sure that i have this file in Desktop before, but i had already delete it into trash, and also delete from trash a long time ago.
Why it still in my maachine?

So weird Someone know what's happeing? Is this linux style?

---

### Post by FyreBrand on 2006-11-03
That I'm not sure about.  Try using the refresh command from the Local menu.  It's at the bottom of the menu.

What you describe isn't something that sounds familiar to me.


I use gFTP.  I used kFTPGrabber when I tried out KDE and liked it a lot.  I use portable FileZilla when I'm at school and need to do FTP there.  I'm pretty happy with gFTP but I just wish is was more intuitive to use.

---

### Post by Jose Catre-Vandis on 2007-10-01
My favourite is "Firefly" an extension to Firefox. Easy to use ftp client within your browser. To transfer files just select the file you want to transfer and click one of the green arrows in the middle.

---

