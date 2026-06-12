---
title: "unexpected problems trying to install uTorrent. Please help."
date: 2012-06-22
forum: New to Ubuntu
---

### Post by Franknj229 on 2012-06-22
First off, I'm running Ubuntu 10.04 as a guest virtual machine in Vista64.

I would like to install uTorrent on Ubuntu and, since I have no idea how to do that on my own, I have read through every "step by step" tutorial and watched every youtube video on the topic.  They are all a little different in their approach, but the results are always the same:  I end up running into a problem that is not mentioned in the guide.

I'm hoping that someone on this forum can get me started with a step-by-step and as I run into a problem hopefully they can get me through it.

I literally need to start at "step 1".  I would assume that is to go to utorrent .com and download utorrent, but some of the online guides started in the terminal or in the software manager.

Please be overly detailed even if you think it's an obvious step.

Thank you,
Frank

---

### Post by SlugSlug on 2012-06-22
am not a torrent fan, so I don't really know the differences but ubuntu has a torrent program installed by default, look for a program called transmission

---

### Post by Enigmapond on 2012-06-22
This is a windows programme and only installs runs through wine but why bother when transmission works just fine? If you need a larger GUI, install deluge but running utorrent on Ubuntu is not the greatest of ideas...

---

### Post by NikTh on 2012-06-22
I must agree with above opinions. Transmission is far better torrent client from utorrent , 
BUT.. 
if you want to use the torrent client that you like or know to use there is a method for linux..

> 1) Download utorrent from here --> [http://www.utorrent.com/](http://www.utorrent.com/)

2) Extract the archive to your /home folder. 

3) Find the file with name  ***utserver ***[I]and make it executable (right click and permissions) 

4) Execute the file and utorrent is already open , but to see it 

5) open your browser and go to [/I][B][http://localhost:8080/gui/](http://localhost:8080/gui/)

[/B]it will promt you for a username and password . **Username : admin Password : (leave it blank).  **
[B]
Tip1 : [/B]utorrent will continue to work in background even if you close the browser page. You must kill the program (from top command) to close it.

**Tip2:** Download torrent file and then click add (+) from utorrent to add the torrent and begin download. 

**Tip3:** When you download torrent files they go to the folder of utorrent by default , you can change destination if you want. 

Thanks

---

### Post by Franknj229 on 2012-06-22
Ok, thank you for the replies.

I will try transmission, but that leads to my next question:  How?

The software center shows that it is installed, but how do I access it?  If I do a file search for "transmission" it says "file not found".

---

### Post by blueshead on 2012-06-22
Try qBittorrent from the software center. It's very nice. It's replaced Transmission for me as it seems a lot of people have had problems with it lately..

---

### Post by NikTh on 2012-06-22
> **Franknj229 said:**
> First off, I'm running Ubuntu 10.04 as a guest virtual machine in Vista64.
Hi , 
why you don't try Ubuntu 12.04 LTS ? Newer , better kernel , newest packages , programs ... etc

> **Franknj229 said:**
>  but how do I access it?  If I do a file search for "transmission" it says "file not found".

If i remebmer correctly , go to Applications > Internet > Transmission Bitorrent Client.

---

