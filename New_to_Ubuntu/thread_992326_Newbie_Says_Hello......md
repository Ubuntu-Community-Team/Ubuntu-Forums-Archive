---
title: "Newbie Says Hello....."
date: 2008-11-24
forum: New to Ubuntu
---

### Post by dawiba on 2008-11-24
.....and asks a few questions!

I've downloaded and burnt the live cd and I'm running it in this old laptop (Dell Latitude). So far, so good!

I've plugged in my camera and it was recognised, photos were all there and I was able to select some for editing if I wanted, which was great.

I plugged in my ipod and it was recognised. Rhythmbox was launched but wouldn't play any tracks from the ipod because it needed codecs. Fair enough, this isn't Ubuntu's fault. I have to assume that these will work if I pay for the download from Canonical. Can anyone confirm? I downloaded Helixplayer (Realplayer) and was able to play ipod tracks through this. This will be fine while I'm just trying out Ubuntu. It also allowed me to play media from the BBC website iplayer.

I'm enjoying finding my way round in Ubuntu and everything seems reasonably straight forward up until now.

So far so good then.

The next bit............

Ultimately, I'd like to install Ubuntu Studio (making music is my hobby) and this laptop doesn't have enough space. To that end, I'll be buying an external hard drive and would like to install Ubuntu Studio on there and run it from there. Would that be possible while still maintaining Windows on the laptop hard drive?

Ideally, I'd like to have the laptop running dual boot with Windows and Ubuntu and to have the external drive running Ubuntu Studio. This way, the kids could use the laptop in Ubuntu, without the risk of them exploring and losing some of my music stuff. Is this possible?

---

### Post by theApokalypsis on 2008-11-24
Greetings, 

New myself. Just thought I would let you know you dont need to BUY anything for the codecs. This is open source. everything is free. Im sure others would help you getting that setup (im not so sure myself) :). I have running a fairly new model ipod though.

your idea about Windows/Ubuntu dual boot with Ubuntu Studio on external HD should work (is it eSATA or USB?). All you would do is edit the grub boot menu to have an entry for Ubuntu Studio which will look for grub respectively on the external drive to boot from.

---

### Post by LowSky on 2008-11-24
sure is, 

Ipods are a bit of an issue, espeacially the newer models, but if its an Ipod Gen 5.5 or older you'll be ok those work pretty well. MP3 playback is very simple to get, if you need dvd playback only a little work is required but still very easy. Studio is a great distro, and ubuntu can be upgraded to it very easily from the vanilla installer you have now. Also installing to a usb is possible, as long as the computer will allow that (check BIOS to see if "boot form USB is possible)

back to mp3 support, its a simple command from a terminal window, 

sudo apt-get install ubuntu-restricted-extras

if you need dvd support, google "medibuntu" it will show you exactly what to do
Good luck and enjoy

---

### Post by ad_267 on 2008-11-24
Hello!

Give this a read: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
Then install the ubuntu-restricted-extras package. There's more information at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You should be able to install on a separate hard drive. See the guides at [https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

---

### Post by dawiba on 2008-11-24
Many thanks for the quick and helpful responses.

I decided that I couldn't install the various bits and pieces that had been recommended while still running the live cd, so I went ahead and installed Ubuntu on the laptop and now have a dual boot machine.

I'm happy to report that everything is fine so far, so many thanks once again :)

After looking at the idea of installing and being able to boot Ubuntu Studio from an external drive, I've decided that I'll leave that for a while. I now think I might be better to install the OS on the laptop but have all the music files etc stored on the hard drive. I think I should probably get comfortable with Ubuntu before I get too carried away!

Thanks again.

---

### Post by ad_267 on 2008-11-24
Glad to hear it. Storing the data on the external drive sounds like a simpler and better idea if you have enough space on the inbuilt hard drive to dual boot :)

---

