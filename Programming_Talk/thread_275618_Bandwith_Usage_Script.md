---
title: "Bandwith Usage Script"
date: 2006-10-11
forum: Programming Talk
---

### Post by dyol on 2006-10-11
as a newbie Linux  may u help with a script that monitor bandwith usage when downloading/copying a file from an ftp server i have already set up.thanx

---

### Post by JonahRowley on 2006-10-11
I'm not sure I understand your question.  Do you want a tally of all bandwidth used, or do you want a progress bar for downloading and uploading files with FTP?

---

### Post by dyol on 2006-10-13
> **JonahRowley said:**
> I'm not sure I understand your question.  Do you want a tally of all bandwidth used, or do you want a progress bar for downloading and uploading files with FTP?


OK thank you for replying. let me try explaining my problem as simple as possible.

What i want to do is to monitor how a specific files is downloaded. ie the throughput at any given point in time during its download. for example lets say we have a 100MB file we want to download. Basically that files will not be downloaded at constant throughput. so i want something which will show me the variations in throughput. and if possible also do it graphically.

Ideally i wld lyke to run the same download during different times then be able to compare the performance, fluctuations etc.

---

### Post by amo-ej1 on 2006-10-13
The easiest way would be to use a single interface (NIC/vlan/etc..) and keep that dedicated to tests. Then there are a lot of tools which can assist you, things like mrtg or some simple things like nload.

---

### Post by JonahRowley on 2006-10-13
Yes, there are a bunch of network monitor programs and applets and such.  If you stop using other network apps, you can use that to monitor your download.  However, it's not really automated, so that doesn't sound like what you want.

You can use wget for this.  Use **wget --progress=dot [http://some.large/file](http://some.large/file)** and log this to a file.  I think it does just what you want, give it a try.

---

