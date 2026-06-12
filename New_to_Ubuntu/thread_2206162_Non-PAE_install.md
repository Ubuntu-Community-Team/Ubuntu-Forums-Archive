---
title: "Non-PAE install"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by Conan_Troutman on 2014-02-17
@Wild Man
Thanks, worked liked a charm!

> **mörgæs said:**
> Besides: Lubuntu 12.04 is out of support and should not be used. 
If you installed this one because of the PAE problem there are some options here: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Yeah, I tried 13.10 first, but it didn't work because of PAE. I heard I could install 12.04 and do an OTA upgrade, so I just went that way. Anyway, I'm stuck at step 3. When I type in 
sudo cp release-upgrades release-upgrades.backup
[FONT=georgia][/FONT][SIZE=3][FONT=georgia]
it says:  "cannot stat 'release-upgrades': no such file or directory. "

Skipped the backup and typed:
sudo sed -i s/Prompt=lts/Prompt=normal/ release-upgrades

Only to be told: "sed: -e expression #1, char 26: unterminated 's' command"

However, the directory is there, under etc./update-manager/release-upgrades.d

Do I have to adjust the lines and if so, how?[/FONT][/SIZE]

---

### Post by mörgæs on 2014-02-17
Moving your question to a new thread, because this is a new question. Please mark the old thread solved.

In which directory are you when you execute the command
```
sudo cp release-upgrades release-upgrades.backup
```
?

Please confirm using the command ```
pwd
```

---

### Post by Conan_Troutman on 2014-02-17
It says:
/home/daniel

edit:
I found the introduction to the terminal and how to change directories. Seems to be working now!

---

