---
title: "Size mismatch - error while update"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by chekoo on 2008-08-06
I am facing this error for last 2 months.

Every time I run update manager, first file gets downloaded and installed correctly. 

But for all other files it gives error - Size mismatch. So If there are 200 updates I have to run update manager for 200 times to get all the files downloaded correctly. 

I have done following things to get away with this error 

* reinstalled ubuntu 8.04 for at least 4 times
* tried - sudo update clean
* tried - sudo update --fix-missing
* tried - sudo upgrade
* tried to change the software sources
* tried to change localization

But still no success.

Please Help !!!

---

### Post by ibuclaw on 2008-08-06
That seems very strange indeed.

Only reasons I can think of is that it either has something to do with your ISP or your connection is rather faulty and upon downloading the packages the checksum fails.

You could try
```

sudo apt-get update 
sudo apt-get upgrade -o Acquire::Retries=4

```

If that might help...

Regards
Iain

---

### Post by chekoo on 2008-08-06
Thanks for the help.

But still the problem is not resolved.

When I run this command, I see that first file size and download size are correct but from second file onwards file size is different and download size is different.

May be it is an issue with my ISP.

Thanks again for the suggestion.

---

### Post by bpowell2005 on 2008-08-06
Do you have enough free hard drive space? I've seen aptitude get very troublesome when the hard drive fills up. Please verify you have space available on your root partition to support downloading, unpacking, and installing of packages.

---

### Post by chekoo on 2008-08-07
Yes I have 80 GB harddisk with more than 35% free.

---

### Post by bpowell2005 on 2008-08-07
how about running apt-get clean? This will clean out the cache for apt, and maybe something has been corrupted in your cache? Apt-get clean may remove the corrupted file. Then run apt-get update, apt-get upgrade.

---

### Post by ibuclaw on 2008-08-07
Have you checked your sources list app?
**System->Administration->Software Sources**
And made sure that you are getting it from a nearby server?

Regards
Iain

---

### Post by chekoo on 2008-08-07
Thanks. I tried that but still the issue remains.

---

### Post by chekoo on 2008-08-07
Yes. I changed the sources - main / US but it is same for all.

---

### Post by bpowell2005 on 2008-08-07
This is a strange problem. The only things I can think of that cause this are:

1: Disk full: (please post the result of "df -h" here.
2: Corrupted File from Apt-get: apt-get clean should correct this.
3: Outdated program information in aptitude...apt-get update should correct this.
4: Problem with repos: other uses would be noticing this same failure then, and I haven't noticed others commenting on this issue.

Other than the above, I'm stumped. I'm curious what it is though!

---

### Post by canvasman on 2009-03-16
Hi All ! I am getting the same errors on update. Just started today. Never had any issue with updates in the past.

---

### Post by canvasman on 2009-03-17
H i Again ! I did as the previous poster said to do.. changed the mirror and the error was gone as fast as it came. All updates continued without issue. Thanks for this thread.

---

