---
title: "Modifying files via FTP?"
date: 2009-04-04
forum: Programming Talk
---

### Post by Crath on 2009-04-04
So made a connection to my websites ftp account, and i can go into it and see all my files.  I can create directorys fine, and upload / delete files pretty well (sometimes it says it doesnt exist, but thats not a problem) but here is where i run into issues.

[connected to ftp]
[http://crath.com/pics/connect_to_ftp.png](http://crath.com/pics/connect_to_ftp.png)

I open one of the files such as a file called index.html using bluefish, and it opens fine, and shows the ftp's directory in the tree to the left and opens the file, and when i go to hit save, i get errors such as this

[save error]
[http://crath.com/pics/save_error.png](http://crath.com/pics/save_error.png)

Should I not use this method to connect to ftp?  is there something else i can do that is similar to this? I would rather not have to download files each time, edit, and re-upload, if you know what i mean.

I'm a real noobie at linux, so any tips / help would be greatly appreciated!  thanks!

---

### Post by simeon87 on 2009-04-04
What about keeping a local copy of the files? You keep a local copy of all code/html files of the website and you upload only the files that you've modified. This way, all you need to do is to make sure they're both in sync (i.e., the server contain the same files as your local copy).

---

### Post by Crath on 2009-04-04
> **simeon87 said:**
> What about keeping a local copy of the files? You keep a local copy of all code/html files of the website and you upload only the files that you've modified. This way, all you need to do is to make sure they're both in sync (i.e., the server contain the same files as your local copy).

the way i code is, i make a small tweak, and check it, make another small tweak, check it, etc. If i have to leave my text browser, sync the files, then check the web browser every time, that'd kinda suck.

for example, before I switched over I used Notepad++, which had FTP built in, and would upload every time you saved the file

any popular ftp clients that watch for when a file is modified and auto-uploads it like, filezilla does that I think

thanks again guys!

---

### Post by simeon87 on 2009-04-04
> **Crath said:**
> the way i code is, i make a small tweak, and check it, make another small tweak, check it, etc. If i have to leave my text browser, sync the files, then check the web browser every time, that'd kinda suck.

for example, before I switched over I used Notepad++, which had FTP built in, and would upload every time you saved the file

any popular ftp clients that watch for when a file is modified and auto-uploads it like, filezilla does that I think

thanks again guys!

How about installing a local webserver so you don't need to upload every time? This is quite common and more efficient than uploading the files after every tweak.

---

### Post by Crath on 2009-04-04
I found jEdit which has an FTP plugin, thanks for the help!

---

### Post by myrtle1908 on 2009-04-04
Sounds like you need an editor/IDE with FTP support so that you can do "live edits".  There aren't many for linux.  [Eclipse]("http://www.eclipse.org/") probably has it but I've never tried FTP with it.  [Komodo Edit]("http://www.activestate.com/store/download.aspx?prdGUID=20f4ed15-6684-4118-a78b-d37ff4058c5f") I'm told also has this type of integrated FTP support.

---

### Post by myrtle1908 on 2009-04-04
Further to my previous post.  To install Komodo Edit:-

1. Download linux package to temporary location from link I mentioned above.
2. Explode package and then type:- chmod +x install.sh
3. Run the installer by typing:- ./install.sh
4. Follow the prompts in the installer
5. From the install 'bin' folder', run Komodo by typing:- ./komodo
6. From the 'Toolbox' menu, select 'Add Existing Remote File...' and configure your FTP server

---

### Post by Crath on 2009-04-04
> **myrtle1908 said:**
> Further to my previous post.  To install Komodo Edit:-

1. Download linux package to temporary location from link I mentioned above.
2. Explode package and then type:- chmod +x install.sh
3. Run the installer by typing:- ./install.sh
4. Follow the prompts in the installer
5. From the install 'bin' folder', run Komodo by typing:- ./komodo
6. From the 'Toolbox' menu, select 'Add Existing Remote File...' and configure your FTP server

thanks for the tips, jEdit is working out quiet nicely, but I ran into one thing.  Both jEdit and ubuntu's built in "connect to server" feature do not include a way for me to modify permissions of files (CHMOD) on the webserver.  any tips? thanks!

---

