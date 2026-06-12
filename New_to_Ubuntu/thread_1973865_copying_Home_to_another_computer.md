---
title: "copying /Home to another computer"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-05-05
Yesterday I fresh installed 12.04 to a spare desktop and with the same user name as my laptop. Then I copied my /Home to it. Then it was totally screwed up. So I reinstalled and just copied my documents and desktop. My question is what files and folders need to be avoided to not screw up the new install and yet get most of my config settinbg
s from the original machine Home folder.

---

### Post by PaulW2U on 2012-05-05
I've re-used my /home partition files for a new installation many times but have always copied my files from the old partition to the new partition first. 

When installing I use the option that gives me full control over what partitions are used and whether they are formatted or not. Obviously I tell the installer not to format the partition that I have designated as /home. I've never had a problem doing it this way with either Ubuntu or Kubuntu.

If I was copying files after installation I think I would avoid any configuration files that specifically refer to the desktop environment.

---

### Post by cmcanulty on 2012-05-05
what I need to know is what files to avoid copying of ?Home when going to a different computer

---

### Post by oldfred on 2012-05-05
I would first copy all the non-hidden folders like Music, Documents etc.

But you have data in some hidden folders. The one's I copy include the Firefox profile and Thunderbird profile. Back up current one's first. 

Some other applications store settings and data that you may want to copy but have to review application by application.

---

### Post by gordintoronto on 2012-05-05
+1 for Oldfred. Don't copy the hidden folders.

Firefox has a method for exporting the bookmarks and importing them into a new installation via a .json file. If you use Evolution, it also has export/import functions. I also use Miro, which has similar functions.

---

### Post by iMurshaq on 2012-05-09
Just copy the folders INSIDE the home folder instead of the home folder itself, also like tpam said, DO NOT COPY THE HIDDEN FOLDERS. Good luck.

---

### Post by cmcanulty on 2012-05-09
what I don't understand is- aren't the hidden folders where are the configs are?

---

### Post by Derek Karpinski on 2012-05-09
Definately copy the .shotwell folder if you've setup and managed your picture libraries with shotwell.

---

### Post by oldfred on 2012-05-09
I thought you did not want the configs to mess up your system. 

Generally if a new install I suggest reusing /home or copy the entire thing so all configurations are copied over. 

I normally do a clean install and copy data and then only copy some of the hidden configurations I know I want, but you have to decide.

---

### Post by cmcanulty on 2012-05-09
OK that's what I thought but I don't know which ones would mess up my system. Firefox has a lot of special configs I have set up for example.

---

### Post by oldfred on 2012-05-09
I keep all my hidden folders with data like Firefox profile, Thunderbird profile, kmymoney, and others in separate data partitions. Then my /home has very little configuration files.

---

