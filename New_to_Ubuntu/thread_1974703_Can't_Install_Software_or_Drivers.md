---
title: "Can't Install Software or Drivers"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by alsamman on 2012-05-06
I've been using Ubuntu 10.04 LTS and switched to 12.04 yesterday. Ever since then I am getting a ridiculous amount of errors and problems and i did a fresh install.

When I go to system settings>Additional Drivers all it does is says its downloading packages and indexes and when that's done nothing happens. Doesn't say anything about installing my nvidia driver. 

Then for my mp3s when I try to import my music folder to rhythmbox it says that it requires mpeg encoders so when I try to install them i get an error saying it couldn't find the required plugins?
```
Required plugin could not be found

Python (v2.7) requires to install plugins to play files of the following types:
&#8226; MPEG-1 Layer 3 (MP3) decoder
&#8226; MPEG-1 Layer 3 (MP3) decoder
&#8226; MPEG-4 AAC decoder
```

Flash is crap. When I went to youtube and the message saying I need additional plugins (adobe flash) I click install and it just says "Failed". I managed to install it from the adobe site but my youtube video quality isn't up to par with what I used to have on 10.04.

Management service always says its unable to install and then it crashes.

Anything that needs to 'universe' repository doesn't work because it says for me to check my internet??
```
W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
```

Seriously whats going on here? This is ridiculous.

---

### Post by mastablasta on 2012-05-06
don't know about nvidia drivers. i think there are some bugs and you might need to install them manually. it's nvidia issue.

for the mp3 and flash i find it better to simply install restricted extras package from software center that includes MP3, codecs, various other media codes, flash and i think some fonts.

---

### Post by alsamman on 2012-05-06
alright I figured it out. My settings had it set so that all my downloads come from the Server in Canada. I changed it to Main Server and now I am able to download everything.

---

### Post by kunalchakra on 2012-11-06
I have cganged it to main server  but still it is giving me the same error message!!!

---

### Post by mlentink on 2012-11-06
@kunalchakra: It's not super polite to hijack someone else's thread, so you might take that into account. Are you sure you've got exactly the same problem as OP? What error messages are you getting. Please be as specific as possible to help others help you.

---

### Post by COMECON on 2012-11-10
You should create a new thread, as this one has been marked as Solved.

---

