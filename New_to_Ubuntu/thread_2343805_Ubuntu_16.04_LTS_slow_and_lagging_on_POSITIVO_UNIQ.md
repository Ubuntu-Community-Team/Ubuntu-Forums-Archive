---
title: "Ubuntu 16.04 LTS slow and lagging on POSITIVO UNIQUE S2050"
date: 2016-11-19
forum: New to Ubuntu
---

### Post by jediashertz on 2016-11-19
I installed the Ubuntu 16.04 LTS on my laptop  POSITIVO UNIQUE S2050. The lag happens all the time and it seem to be asociated to video driver... 

Specs:

RAM 8GB DDR3
Chipset Intel HM70
Processor Intel Dual core B800 1.5Ghz
 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller


I tried to install Intel graphics from Intel Graphics Update tool for Linux but it won't work, cause everytime i try to update those drivers it give me an error: 

W:The repository 'http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://ppa.launchpad.net/skunk/pepper-flash/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://ppa.launchpad.net/upubuntu-com/office/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:[https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:](https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:) Signature by key 09D6EF97BFB38E916EF060E756A3DEF863961D39 uses weak digest algorithm (SHA1), E:Failed to fetch [http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/skunk/pepper-flash/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, E:Failed to fetch [http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

I need some solutions, please. 

Thanks.

---

### Post by Autodave on 2016-11-19
I usually just use the "Software & Updates" -> "Additional drivers" and let Ubuntu search for them. If it doesn't find anything, you are probably using the best driver.

Is there a specific problem you are having that you want to install a different driver?

---

