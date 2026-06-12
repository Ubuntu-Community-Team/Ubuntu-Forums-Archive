---
title: "Bookmarked network folder not showing in Browse for files"
date: 2013-08-06
forum: New to Ubuntu
---

### Post by Elizabeth_Gossett on 2013-08-06
Hi,

I'm new here, so I apologize if this isn't the appropriate forum. 

I'm trying to attach a file I have saved on a Windows network folder in my Outlook Web Application. I am connected successfully to the Windows network folder ([See this picture]("https://dl.dropboxusercontent.com/u/53879046/Connected%20Windows%20Network%20Folder.png")) and I have the folder bookmarked in Nautilus. However, when I click "Browse" to attach the file, the network folder does not show up in the available folders list ([see this picture]("https://dl.dropboxusercontent.com/u/53879046/Bookmark%20Not%20Showing.png")). 

I would like to either A) find a way to add the network folder so it shows up in **_all_** Browse for files locations or B) verify if what I'm trying to do is just not possible. The network folder also does not show up when [Browsing for files using Scribus]("https://dl.dropboxusercontent.com/u/53879046/Not%20in%20Scribus%20Either.png"). 

Thanks!

---

### Post by bab1 on 2013-08-06
> **Elizabeth_Gossett said:**
> Hi,

I'm new here, so I apologize if this isn't the appropriate forum. 

I'm trying to attach a file I have saved on a Windows network folder in my Outlook Web Application. I am connected successfully to the Windows network folder ([See this picture]("https://dl.dropboxusercontent.com/u/53879046/Connected%20Windows%20Network%20Folder.png")) and I have the folder bookmarked in Nautilus. However, when I click "Browse" to attach the file, the network folder does not show up in the available folders list ([see this picture]("https://dl.dropboxusercontent.com/u/53879046/Bookmark%20Not%20Showing.png")). 

I would like to either A) find a way to add the network folder so it shows up in **_all_** Browse for files locations or B) verify if what I'm trying to do is just not possible. The network folder also does not show up when [Browsing for files using Scribus]("https://dl.dropboxusercontent.com/u/53879046/Not%20in%20Scribus%20Either.png"). 

Thanks!
Is the "Outlook Web Application" accessed via Firefox?  The displayed "shared directory" you see in Nautilus is not the actual directory that is mounted.  If you expose the 'hidden" directories (alt+h) and browse to this location in your home directory: *[COLOR="#0000FF"]**~/.gvfs**[/COLOR]* (*aka = **/home/<you>/.gvfs***) you should see the actual mounted share.  If this is successful and works for your needs, you can make this easier with either a sym-link (shortcut) or you can mount the share explicitly to a point that is visible in your home directory.

---

### Post by Elizabeth_Gossett on 2013-08-06
Thank you for your quick response. I'll try your suggestions! :)

---

