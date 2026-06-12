---
title: "Canadian Update Mirror URL Change?"
date: 2006-01-11
forum: Repositories &amp; Backports
---

### Post by Hygelac on 2006-01-11
Has the URL of the Ubuntu updates Canadian mirror changed?  It used to be at [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu), but this no longer seems to exist when I check it.

If it has indeed changed, where is it now?

---

### Post by az on 2006-01-11
I have just experienced the same thing.  I am in a hurry to update a computer for a friend, so I had to use the main mirror (I removed the "ca." from the sources in my list, using synaptic.)

I guess it is just a problem with the server   I doubt they are changing the name.  Maybe it is a dns propagation thing, too, if they changed the location of the server?

---

### Post by pieboy314 on 2006-01-11
same here,

I just used this post to correct the situation,
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Hygelac on 2006-01-11
Alright; so it's not just me. :???:

The reason I think the URL may have changed is because I can still interact with the server in a web browser (even downloading from it this way); which I would think means that the server is still running ([http://ca.archive.ubuntu.com)](http://ca.archive.ubuntu.com)).  There seems to have once been a folder in it called «Ubuntu», but it is no longer there (unlike the regular [http://archive.ubuntu.com](http://archive.ubuntu.com), which still has its «Ubuntu» folder), hence the repository trouble.

[http://archive.ubuntu.com?](http://archive.ubuntu.com?)  Thanks; I'll use that for now.

---

### Post by Quake on 2006-01-12
I changed my sources.list for apt to work with ca.archive.ubuntu.com/ and guess what... The files are corrupted. Something is happening with the canadian mirror.

So I guess I'll use archive.ubuntu.com for the time being

---

### Post by Quake on 2006-01-13
It's working fine now...

---

### Post by pieboy314 on 2006-01-13
[QUOTE=Quake]It's working fine now...[/QUOTE]

guess I should have made a backup of my original. :oops:

---

### Post by marcthenarc on 2008-05-02
It seems the Canadian mirrors are acting up again at ca.archive.ubuntu.com (129.97.134.71).  My gutsy distro can't connect to it while it can still reach the security repository @ security.ubuntu.com.

Any others to confirm this?

---

