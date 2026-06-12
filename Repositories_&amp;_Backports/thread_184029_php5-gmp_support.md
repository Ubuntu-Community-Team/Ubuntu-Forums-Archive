---
title: "php5-gmp support"
date: 2006-05-29
forum: Repositories &amp; Backports
---

### Post by jimmystewpot on 2006-05-29
Hello,

I have recently moved away from using Slackware and Redhat throughout my datacentres and started to use Ubuntu. I found that the apt was brilliant. However I have noticed some issues where the apt repositories are not upto spec with what I would see using Redhat Enterprise Linux v4 or Slackware. In particular I am talking about the lack of php 5.1.x support with the libgmp extensions. It appears as though its a part of most distributions except debian and Ubuntu. Having had a look at the following URLs :

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=php5&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=php5&searchon=names&subword=1&version=breezy&release=all)

It is something that I feel would probably be important, Many of my customers use the gmp extensions in PHP for their web applications and not having the functionality makes us seriously think twice about deploying those applications on Ubuntu.  Moving forward I would like to have all of the servers running on a Single distribution for easy management however at this stage it seems unlikely. 

Are ther any chances of getting the php5-gmp support added to dapper/Ubuntu. If this is the wrong place to ask where should I go to get that request? From looking through the apt sources it appears as though its maintained by Debian but I am unsure how to make the requests there?

Any info would be greatly appreciated.

---

### Post by graylion on 2007-03-04
seconded. dexter has ported it to dapper, but it is a pain. any specific reason why it isn't in Ubuntu?

---

### Post by tyrusx on 2007-03-23
I have the same problem.  I think php5-gmp must available in feasty .

---

### Post by Keith_S on 2007-04-20
Just another note from a user who would like to see this added in either edgy or feisty. Thanks!

---

### Post by confuciusquinn on 2007-10-11
I would also really like to see this

---

### Post by Keith_S on 2007-10-11
While it may not be built in, I did find a way to add GMP support:

[http://ubuntuforums.org/showthread.php?t=351873](http://ubuntuforums.org/showthread.php?t=351873)

---

### Post by confuciusquinn on 2007-10-11
cool, thanks. I'll give that a shot and see if I can get it working.

---

