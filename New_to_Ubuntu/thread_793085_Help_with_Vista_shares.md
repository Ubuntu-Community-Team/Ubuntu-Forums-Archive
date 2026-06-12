---
title: "Help with Vista shares"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by tmcelveen on 2008-05-13
Hey guys! This is my first post and first wanted to say how happy I am since trying out Linux for tht first time. I have had almost no problems since installing Heron (only due to my newbie ignorance) and I don't understand all the fearmongering about Linux. Anyway on to the question...

Here's my setup...

1 Server w/ Windows Home Server (basically Server 2003)

1 Laptop w/ Vista

Both joined to a Windows Domain

1 Ubuntu (Heron) PC

Here's the situation...

I've installed Samba and set up a share on my Ubuntu box. 
I can open up Nautilus and see all the pc's on my Windows Domain.
I can read/write all of the shares on my Home Server from Ubuntu.
I can see the Ubuntu box and access the shares from Vista.
I CANNOT see any Vista shares from Ubuntu.
When I double-click on the Laptop icon in Nautilus all I get is a blank screen.

I've googled the problem and there are a ton of "fixes" but there are too many for me to figure out what might be the problem. Any help is greatly appreciated!

Travis

---

### Post by bluefrog on 2008-05-13
eventhough this post should go to a vista forum, haven't I heard that shares must be"enabled" in vista?

---

### Post by aloyr on 2008-05-13
apparently file/folder sharing is disabled in vista by default.

this [link]("http://technet.microsoft.com/en-us/library/bb727037.aspx") on MS website outlines the steps you need to follow to get enable file sharing in vista.

From that page:

> To enable file sharing, do the following:

   1. In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to File sharing.

   2. Within the File sharing settings, click Turn on file sharing, and then click Apply.

To enable public folder sharing, do the following:

   1. In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to Public folder sharing.

   2.  Within the Public folder sharing settings, click one of the following:
          * If you want to share the public folder so that other computers on the network can access the Public share to open files, but not create or change files, click Turn on sharing so anyone with network access can open files. This is the default setting.
          * If you want to share the public folder so that other computers on the network can access the Public share to open files and also create or change files, click Turn on sharing so anyone with network access can open, change, and create files.

   3. Click Apply.


---

### Post by tmcelveen on 2008-05-13
I have verified that file sharing is enabled and and Public folder sharing is also enabled.

Following someone's advice I also turned on the "guest" account in Vista.

Still nothing...

---

