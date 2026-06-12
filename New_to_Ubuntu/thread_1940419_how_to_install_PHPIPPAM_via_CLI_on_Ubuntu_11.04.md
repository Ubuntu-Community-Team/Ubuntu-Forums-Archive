---
title: "how to install PHPIPPAM via CLI on Ubuntu 11.04"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by businoss on 2012-03-13
hi everyone, extreme beginner here please forgive the ridiculously basic questions.

Im interested in using a tool I found called PHPIPPAM...

I have an existing ubuntu system that someone else already set up to use a tool called Cacti. This is a CLI only install so I'm told and I was given the root password. I use putty to access Cisco devices on my network so I'm using putty to access the Ubuntu computer with SSH.

I found a guide online to install PHPIPPAM but its not working as it should. This is the guide I tried to use: [http://www.progob.nl/robmaaseu/?p=300]("http://ubuntuforums.org//http://www.progob.nl/robmaaseu/?p=300")

I tried to type the wget command from the guide and it failed so then I just pasted [http://sourceforge.net/projects/phpipam/files/latest/download](http://sourceforge.net/projects/phpipam/files/latest/download) and it downloaded something.

I typed LS at the hash mark and see a file called download and that's as far as I can get. I'm guessing I need to unzip it with tar, however I'm lost at this point.

Not sure how to proceed and exhaustive googling and my inexperience has prompted me to post on this forum. Any links to point me in the right direction or any advice would be greatly appreciated. Thanks in advance.

---

### Post by doctorzeus on 2012-03-13
> **businoss said:**
> hi everyone, extreme beginner here please forgive the ridiculously basic questions.

Im interested in using a tool I found called PHPIPPAM...

I have an existing ubuntu system that someone else already set up to use a tool called Cacti. This is a CLI only install so I'm told and I was given the root password. I use putty to access Cisco devices on my network so I'm using putty to access the Ubuntu computer with SSH.

I found a guide online to install PHPIPPAM but its not working as it should. This is the guide I tried to use: [http://www.progob.nl/robmaaseu/?p=300]("http://ubuntuforums.org//http://www.progob.nl/robmaaseu/?p=300")

I tried to type the wget command from the guide and it failed so then I just pasted [http://sourceforge.net/projects/phpipam/files/latest/download](http://sourceforge.net/projects/phpipam/files/latest/download) and it downloaded something.

I typed LS at the hash mark and see a file called download and that's as far as I can get. I'm guessing I need to unzip it with tar, however I'm lost at this point.

Not sure how to proceed and exhaustive googling and my inexperience has prompted me to post on this forum. Any links to point me in the right direction or any advice would be greatly appreciated. Thanks in advance.

Firstly your downloading the download page and not the download itself, you need to wget the direct link, you just need to go to the download page in your browser and right-click on "direct link" and then click "copy link location" or something like that.. Then type wget and then paste it in:

e.g. ```
wget http:\\www.thisisthelink.com
```

Then ```
tar -xf phpipam-0.6.tar
```

That should do it..

---

