---
title: "Cross platform torrenting"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by talsemgeest on 2008-04-27
I've been looking for a way to be downloading a torrent under ubuntu, then booting into windows and resume where I left off under Ubuntu. Can anyone help me out?

---

### Post by ad_267 on 2008-04-27
Azureus is available for windows so you could try using that in both Linux and Windows.

---

### Post by quinnten83 on 2008-04-27
this is theoretical and the assumption is that we are talking about one computer with an NTFS and linux partition.
create a folder on a windows partition in Ubuntu where you will place your downloads and torrents.

Download the torrent (and start your torrent program and stop it when you feel like it).

Boot up in windows.
Start your torrent program and save in the folder you created while in Ubuntu. Your torrent program should tell you that there is a file being downloaded and if you want to merge them.

At least, deluge does that..
Remember this is theoretical, so I have no idea if it will actually work.

---

### Post by talsemgeest on 2008-04-27
> **ad_267 said:**
> Azureus is available for windows so you could try using that in both Linux and Windows.
Yeah, I've been trying that, but Azureus wouldn't let me do that. I will try again though...

---

### Post by talsemgeest on 2008-04-27
> **quinnten83 said:**
> this is theoretical and the assumption is that we are talking about one computer with an NTFS and linux partition.
create a folder on a windows partition in Ubuntu where you will place your downloads and torrents.

Download the torrent (and start your torrent program and stop it when you feel like it).

Boot up in windows.
Start your torrent program and save in the folder you created while in Ubuntu. Your torrent program should tell you that there is a file being downloaded and if you want to merge them.

At least, deluge does that..
Remember this is theoretical, so I have no idea if it will actually work.
Ok, I'm trying that now...

---

### Post by ad_267 on 2008-04-27
Yeah assuming that both OSs can access the partially downloaded file, then there is no reason this shouldn't work. I would have thought that using the same client would do this easily. You should just need to make sure that both clients are set to download torrents to the same directory by default or tell them to download to the directory where the partially downloaded file is.

---

### Post by talsemgeest on 2008-04-27
Awesome, everything seems to be working great. I've been getting quite a few crashes in windows though, but I'm not sure if its connected.

Thanks for your help!

---

