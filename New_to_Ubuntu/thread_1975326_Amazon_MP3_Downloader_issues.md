---
title: "Amazon MP3 Downloader issues"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by Bigjack08 on 2012-05-07
Hi all, I know that there has been posts with regard to Amazon before, but not this problem?
I updated to Ubunto 04/12 from Ubuntu 10/11 on my Samsung R530 and since the upgrade cannot download MP3 music from Amazon.
I used a fix that I found on here to get the Amazon Downloader installed on my laptop.
When I open a downloaded file instead of loading the music into Rythmbox it opens Gedit and presents me with a long list of data.
Rythmbox plays all of my previous downloads without a problem.
Hope someone out there can help......soon please.

Just tried using Banshee and music downloads ok....clearly a problem with Rythmbox then?

---

### Post by oklokl on 2012-05-07
First of all, I
[COLOR=Red]audacious[/COLOR]. I use ...

The second
[COLOR=Red]ubuntu-tweak[/COLOR] . This used ...

All the above problems, the program does not install.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) 
(Change the entire connection properties)

[ATTACH]217461[/ATTACH]

[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")
(What song is playing any better. Most Recommended)
(Jokes lie n,.n)May or may not ..



```
sudo add-apt-repository ppa:tualatrix/ppa 
sudo add-apt-repository ppa:nilarimogard/webupd8

sudo apt-get update
sudo apt-get install [COLOR=Red]ubuntu-tweak[/COLOR] [COLOR=RoyalBlue]audacious[/COLOR]
```

---

### Post by Trent T on 2012-05-22
Hi All,

I got the Amazon MP3 Downloader to install, thanks to an excellent tutorial, here, from Eric Fleming at helpdeskgeek.com;

[http://helpdeskgeek.com/linux-tips/get-the-amazon-mp3-downloader-working-in-ubuntu-11-10/]("http://helpdeskgeek.com/linux-tips/get-the-amazon-mp3-downloader-working-in-ubuntu-11-10/")

Apparently, the Amazon MP3 Downloader has dependencies to obsolete libraries that were used last in Ubuntu 8.04.  SO....

1) Install the Amazon MP3 Downloader from CLI

2) Manually install the 7 obsolete libraries from Ubuntu 8.04

3) Use sudo apt-get to install 3 more missing libraries from current repositories.

**DETAILED INSTRUCTIONS FOR STEPS 1 TO 3 ARE AT THE HELPDESKGEEK WEBSITE**

I'm not too familiar with downloading MP3's from Amazon, so I included the following additional instructions and comments (mostly to remind myself what to do next time!) ;

4) I had to restart Ubuntu to find the AmazonMP3Downloader icon in Dash. In CairoDock, its under the 'Internet' subdirectory.

2) Amazon seems to tell me to OPEN the *.AMZ file rather than save it;
This did not work for me.  Instead,

   I saved the *.AMZ file to my Downloads directory, then right-clicked on it, and opened the .AMZ file with AmazonMP3Downloader.
   The *.AMZ file vanishes from Downloads, and my album appears as a folder in /home/Music/Amazon MP3

3) NOTE: If you're a fan of the 'Cloud,' it's possible to play album(s) from the Amazon Cloud Player, located on the [www.amazon.com](www.amazon.com) website.

Hope that helps!

--Trent T, with MAJOR THANKS to Eric Fleming for figuring this out!!

---

