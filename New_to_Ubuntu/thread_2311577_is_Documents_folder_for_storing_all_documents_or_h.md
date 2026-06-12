---
title: "is Documents folder for storing all documents or has another purpose?"
date: 2016-01-28
forum: New to Ubuntu
---

### Post by anotherChris on 2016-01-28
I installed Lubuntu 15.10 then a program called Anki.  I notice it created **/home/anotherChris/Documents/Anki/**.

This might seem like a dumb question, but...

Is the Documents directory designed for users to store their documents, or does it have another purpose and documents (like a letter I write) are meant to be stored in **/home/anotherChris/ **instead of **/home/anotherChris/Documents/**?

I know that any documents I create* can* be stored in either directory.  I'm wondering what the intention was when the directory architecture was designed.

---

### Post by grahammechanical on 2016-01-28
What other purpose could it have? 

/home/anotherChris/ is the Desktop. Which in Linux is treated as if it was another folder/directory. 

I do believe that there are operating systems that stick everything, folder & files, on the desktop. Personally, I like an empty wallpaper image as my desktop background.

I keep all my data on a separate partition. So, I have had to create my own folder structure. And I use the default folders under /home/username/ as a quick but temporary storage space. If I keep any documents in /home/graham/Documents then they would be documents that I do not mind losing if I have to re-install.

A lot depends on the default storage settings of the application we are using. Web browsers will default to storing downloads into /home/username/Downloads. A Music player will default to looking for audio files in /home/username/Music.

It is a useful scheme to help developers have consistency. It should make things easier for the user. And if an application creates its own folder inside the Documents folder, then that keeps things neat for the benefit of the user.

I see this as better than an application storing a newly created file inside its own program directory. Such as /programs/programname/documents. I seem to remember that being standard practice in an OS that I used many, many years ago.

 Regards.

---

### Post by bab1 on 2016-01-28
> **grahammechanical said:**
> What other purpose could it have? 

/home/anotherChris/ is the Desktop. Which in Linux is treated as if it was another folder/directory. 

I think you misspoke here.  The Desktop has its own folder and is at /home/anotherChris/Desktop
> 
...
[There] is a useful scheme to help developers have consistency. It should make things easier for the user. 
This would be the Linux File System Hierarchy the common usage of the directories is shown [**here**]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

### Post by vasa1 on 2016-01-28
And as for subdirectories in the home directory, take a look at [https://wiki.archlinux.org/index.php/Xdg_user_directories](https://wiki.archlinux.org/index.php/Xdg_user_directories)

---

### Post by Dennis N on 2016-01-28
I think with the home folder subfolders like Documents the intention is to suggest that you organize your files rather than dump everything in the same place. Some people are disorganized and need some coaxing. Documents would exclude Pictures, Videos and Music which have their own subfolders. 

Downloads is probably for temporary storage until moved elsewhere.
Public? Who knows?
Templates - used by LibreOffice, for example, for: templates.

You can add more subfolders to your home folder and its subfolders to fit your needs. I have one named Work - used for: projects I am working on.

---

### Post by Habitual on 2016-01-28
> **Dennis N said:**
> Some people are disorganized and need some coaxing.
Most people.

> **Habitual said:**
> The ~/Documents directory is for organization.
How you organize it is up to you. There is no standard.
Anki may or may not have a place to edit/configure where it saves.

---

### Post by anotherChris on 2016-01-29
> **grahammechanical said:**
> What other purpose could it have? 

Well, because Anki stuck a folder in there, I thought maybe it was intended as a repository for documents created by programs, say, automatically... as opposed to user-generated documents.

To a new user, it's not clear that these are simple cookie-cutter directories.  For example, maybe VLC-player can handle things placed in the Music directory differently from things placed in Documents.  I don't know!

Anyhow, if I, personally, were creating a file architecture, I'm not sure I would organize it the way the Lubuntu defaults are.  However, if there are no specialized functions to default directories, I am happy re-arranging things to my pleasure.

---

### Post by bab1 on 2016-01-29
> **anotherChris said:**
> Well, because Anki stuck a folder in there, I thought maybe it was intended as a repository for documents created by programs, say, automatically... as opposed to user-generated documents.

The program is most likely running with your user rights.  The only directory that your user has permission to write to is your home directory of subdirectories below that.  Everything else in the file system hierarchy is owned by root or other users in their home directories.  What happened may not be optimal but it is understandable.
> 
To a new user, it's not clear that these are simple cookie-cutter directories.  For example, maybe VLC-player can handle things placed in the Music directory differently from things placed in Documents.  I don't know!
Not really.  All directories are created the same except for ownership and access permissions> 

Anyhow, if I, personally, were creating a file architecture, I'm not sure I would organize it the way the Lubuntu defaults are.  However, if there are no specialized functions to default directories, I am happy re-arranging things to my pleasure.
Knock yourself out.  Be careful that you don't change anything outside of your home directory or you will be reinstalling the whole thing later on down the road.

---

