---
title: "tar -zxvf fails on a particular archive"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by vmarquez on 2008-10-24
Hi!

I am trying to decompress an archive (tikiwiki-2.2.tar.gz) and every time tar just hangs at some point. Impossible to regain control over the session. Ctrl-C just does nothing.

Every time I try to decompress the file tar hangs. Every time at a different point. Yes I am deleting the resulting directory before retrying.

I have downloaded the file several times. Same results.

I have used tar to decompress other archives today and before with no problems.

tikiwiki-2.2.tar.gz is just 15 MB. I have succesfully downloaded and decompressed archives hundreds of megabytes long.

Using Ubuntu 8.04 Server. apt-get updated and upgraded.

Any hint?

Thanks in advance for your time

Victor Marquez

---

### Post by porchrat on 2008-10-24
try this...see if it can list the contents:

```
tar -t tikiwiki-2.2.tar.gz
```

Also see what ubuntu actually thinks the file is.  Post the ouput of this command:

```
file tikiwiki-2.2.tar.gz
```

You may find the file wasn't compressed properly and ubuntu doesn't recognise it as a .tar.gz and hence can't extract it properly.

---

### Post by vmarquez on 2008-10-24
Hi porchrat, thanks.

tar -t tikiwiki-2.2.tar.gz

Does nothing. Command hangs but I am able to stop it with Ctrl-C. Absolutelly nothing happens. Nothing listed. Just hangs. Waited 2 minutes before stopping it.

----
Result from: 

file tikiwiki-2.2.tar.gz

tikiwiki-2.2.tar.gz: gzip compressed data, from Unix, last modified: Fri Oct 17 14:
05:57 2008

---

### Post by porchrat on 2008-10-24
> **vmarquez said:**
> Hi porchrat, thanks.

tar -t tikiwiki-2.2.tar.gz

Does nothing. Command hangs but I am able to stop it with Ctrl-C. Absolutelly nothing happens. Nothing listed. Just hangs. Waited 2 minutes before stopping it.


OK not a good sign.

There is an old unix command you could try that might be able to open the file, but I don't think it works on .tar.gz though.  So you may have to run it through gzip to remove the .gz first.

The command is cpio.

syntax would be something like this:

```
cpio -i tikiwiki-2.2.tar
```

If the indexes are missing from that tikiwiki-2.2.tar.gz then cpio might still be able to extract it.  Give it a go.

---

### Post by Baelus on 2008-10-24
I just got it from freshmeat.

[http://freshmeat.net/projects/tiki/?branch_id=58248&release_id=286833]("http://freshmeat.net/projects/tiki/?branch_id=58248&release_id=286833")

It untars fine.

I'm looking at tikiwiki for the first time and it seems great. I'll check it out some more.

---

### Post by vmarquez on 2008-10-24
Tried that. First gunziped, then cpio did nothing. Just hangs. Waited several minutes, then cancelled with Ctrl-C.

A side note: I have been able to download the corresponding .zip file to a Windows PC and unziped there. The I FTP-d the files to my Ubuntu host and were able to install and configure TikiWiki. I may stop here as my main requirement is solved but. I am able to continue with this thread if it can be of help for somebody in the future. What do you think porchrat?

Thanks again for your time.

---

### Post by vmarquez on 2008-10-24
> **Baelus said:**
> I just got it from freshmeat.

[http://freshmeat.net/projects/tiki/?branch_id=58248&release_id=286833]("http://freshmeat.net/projects/tiki/?branch_id=58248&release_id=286833")

It untars fine.

I'm looking at tikiwiki for the first time and it seems great. I'll check it out some more.
Hi Baelus, 

wget [http://freshmeat.net/projects/tiki/?branch_id=58248&release_id=286833](http://freshmeat.net/projects/tiki/?branch_id=58248&release_id=286833)

gives me "ERROR 403: Forbidden."

---

### Post by Baelus on 2008-10-24
That's the project page. You can choose the file to download from there.

Here's a direct link to tikiwiki2.2.tar.gz from the internode mirror:

[http://internode.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.gz]("http://internode.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.gz")

---

### Post by jerome1232 on 2008-10-24
[http://internap.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.bz2](http://internap.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.bz2)

 That's the direct link to the download or if you want the gzipped one

[http://internap.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.gz](http://internap.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.gz)

---

### Post by vmarquez on 2008-10-24
> **Baelus said:**
> That's the project page. You can choose the file to download from there.

Here's a direct link to tikiwiki2.2.tar.gz from the internode mirror:

[http://internode.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.gz]("http://internode.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.tar.gz")
Baelus, Dumb of me!

trying...

same results.

---

### Post by Baelus on 2008-10-24
How about taking tar out of the equation and just use a zip file:

[http://puzzle.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.zip]("http://puzzle.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.zip")

or

[http://internode.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.zip]("http://internode.dl.sourceforge.net/sourceforge/tikiwiki/tikiwiki-2.2.zip")

---

