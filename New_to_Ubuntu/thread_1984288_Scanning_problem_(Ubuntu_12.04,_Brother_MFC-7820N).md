---
title: "Scanning problem (Ubuntu 12.04, Brother MFC-7820N)"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by MagicalGirl on 2012-05-21
Hi everyone! I am pretty new to Ubuntu (>1 month old). I'm running 32-bit Ubuntu 12.04 on a Dell Inspiron 1525. (I don't know how much of this matters.)
I'm trying to scan using a Brother MFC-7820N scanner, so I downloaded the driver provided by Brother, according to their instructions. ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)) Terminal told me I couldn't install it using "rpm" (Brother told me to put "rpm  -ihv  --nodeps  brscan2" into the terminal) because I didn't have rpm installed, so I did "sudo apt-get install rpm". It spat out a bunch of code and informed me that it was done, so I did "rpm  -ihv  --nodeps  brscan2" again. It told me that I should've used Alien instead of rpm to install an rpm package, but it was going to assume I knew what I was doing (always very dangerous) and do it anyway.
So. I tried to scan something, and Simple Scan told me that it "Failed to scan / Unable to connect to scanner", but when I click Change Scanner I get this:
[IMG]http://http://www.flickr.com/photos/79043148@N02/7242774616/in/photostream[/IMG]http://www.flickr.com/photos/79043148@N02/7242774616/in/photostream/
which suggests to me that it's at least latched onto the idea that I have a scanner (before I installed the driver, Simple Scan would tell me that it wasn't connected to any scanner whatsoever.) This is about when I realized that contrary to what I'd been told, this was *not* going to be easy, so I started taking screenshots so I'd be able to ask for help.
Then I figured I'd try Alien (using these instructions [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)), so I installed it and tried installing the rpm package that way, and I got this:
[IMG]http://http://www.flickr.com/photos/79043148@N02/7242775588/in/photostream/[/IMG]http://www.flickr.com/photos/79043148@N02/7242775588/in/photostream/
which I think means it converted it to a Debian package instead of installing it (?) but I'm not sure why it did that.  I then tried to install said Debian package, and got this:
[http://www.flickr.com/photos/79043148@N02/7242776282/in/photostream/](http://www.flickr.com/photos/79043148@N02/7242776282/in/photostream/)
While I was in the middle of writing this post, I realized I'd forgotten an -i when I first tried to install the rpm package with Alien, so I did it over, and got this:
[http://www.flickr.com/photos/79043148@N02/7242877630/in/photostream](http://www.flickr.com/photos/79043148@N02/7242877630/in/photostream)
Still no luck. What do I do? All I want to do is scan one stupid flyer so I can invite my Facebook friends to roller-skating night at the community center.
I realize this is terribly long and I've probably left out something major, but I'd really appreciate any help that anyone can give me. :(
[IMG]http://www.flickr.com/photos/79043148@N02/7242776282/in/photostream/[/IMG]

---

### Post by Cheesemill on 2012-05-21
You have the wrong driver. You've downloaded the .rpm driver which is for Fedora/Red Hat systems. Instead you should download the .deb file and follow the dpkg instructions.

---

