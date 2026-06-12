---
title: "unmet dependencies"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-05-15
Error: Opening the cache (E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed of opened.)

what does this mean? how to deal with this? please help.

---

### Post by Daveth on 2012-05-15
it would help us if you told us which program you were trying to install. The unmet dependencies mean that the program you want relies on a set of files and that 1 or more of them on your system are either missing or of the wrong version. You would typically download the missing files, then try again.

---

### Post by tojonukokhadush on 2012-05-15
okay. i don't remember i was doing anything like installing any program. i was rather downloading from deluge. and interestingly, though i was reluctant to mess up with that and actually did nothing; it again started working after few hours! lucky meh ;-) 
thankyou very much for your concern.

---

### Post by debussyfields on 2012-05-17
Although I like to find easy solutions to my ubuntu-related dilemmas, I have found out in the past, that sometimes there is no single answer to an issue like unmet dependencies. 

I chose to use the apt-cache tool, with a request of most significant issues first. The first which came up was Nvidia. I removed the drivers and app. Then I used Ubuntu Software Centre to remove several library codestrings which were also quite noticeable. I then reinstalled the recommended Nvidia drivers and apps.

After that was done, I rebooted. 

Problem now gone!

---

