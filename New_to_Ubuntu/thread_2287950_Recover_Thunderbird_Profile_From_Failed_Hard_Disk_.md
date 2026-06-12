---
title: "Recover Thunderbird Profile From Failed Hard Disk Running Lubuntu 14.4"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by serafini-c on 2015-07-23
I got a hard disk that has randomly stopped booting into Lubuntu today. 

I have tried to solve this issue but have decided just to reload Lubuntu.

There is no important data on the hard drive as most files are stored on a server. The only file that I would like to recover is the Thunderbird profile stored on the failed Lubuntu hard drive. It is not too important for me to recover the file. As I do have a backup of the profile that is five days old but be would be still nice for me to recover this profile. So I know for the future. 

I can boot into a Lubuntu Disk and review the failed hard disk files but I do not know how to access the folder with the Thunderbird profiles from a bootable disk. I cant find the correct directory. 

Reviewing online resources I should be able to type [COLOR=#0000ff]"~/.mozilla-thunderbird/profiles/<NameOfProfileFile>" [/COLOR]but I think this does not work because I am booting from a disk. 

Could someone help me recover this Thunderbird Profile.

Kind Regards, 
Paul Serafini[COLOR=#0000ff]
[/COLOR]

---

### Post by howefield on 2015-07-23
Try 

```
home/*user*/.thunderbird
```

Note the dot indicating a hidden file/folder. Ctrl + H to view hidden files/holders.

---

### Post by serafini-c on 2015-07-27
Thanks for all your help. 

Yes this did solve my issue. I have done this before using another method but complete forgot about it. 

**Additional Information (To people with similar Issue)**

 _Second Method_

1. Open File Manager PCManFM
2. Press View 
3. Press Show Hidden Files

---

