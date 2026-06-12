---
title: "Terminal Error! &quot;bash: location: No such file or directory&quot;"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by penguinprogrammer on 2013-01-05
Hey, I'm trying to root into a downloaded folder from my downloads in the terminal but no matter how many times I try, I keep getting the same error. "bash: location: No such file or directory". 
Any Help would be appreciated.

---

### Post by TOMBSTONEV2 on 2013-01-05
Make sure there is a space between cd and /
Example

cd /home/justin/Downloads

It is also case sensitive.

---

### Post by Abhinav Kumar on 2013-01-06
> **penguinprogrammer said:**
> Hey, I'm trying to root into a downloaded folder from my downloads in the terminal but no matter how many times I try, I keep getting the same error. "bash: location: No such file or directory". 
Any Help would be appreciated.
Hi penguinprogrammer
Try locating your folder first
```

find YOUR_DIRECTORY_NAME -xtype d

```
YOUR_DIRECTORY_NAME should be replaced with your directory name.
Also then cd to the directory using autocompletion feature. (You just need to use tab and list of possible folders in that folder will be displayed). Make sure if there is a folder with space in it, you need to type escape sequence for space
eg: If you have a folder named **untitled folder** in your home directory, you need to type in a terminal with a slash in between
```

untitled**\ **folder

```

Regards
Abhinav

---

### Post by iMac71 on 2013-01-06
> **Abhinav Kumar said:**
> Make sure if there is a folder with space in it, you need to type escape sequence for space
eg: If you have a folder named **untitled folder** in your home directory, you need to type in a terminal with a slash in between
```

untitled**\ **folder

```Regards
Abhinavan alternative to use of escape sequences is to enclose the directory name between quotes.

---

### Post by penguinprogrammer on 2013-01-06
RE: TOMBSTONEV2 Thanks, I tried it and it still gave me the error. I also capitalized the 'd' in downloads, but it didn't work. Is it different for .zip folders?

---

### Post by JiuJitsu500 on 2013-01-06
You have to extract .zip folders first...

but to get into downloads it's typically "cd ~/Downloads"

Once extracted, then if there is a directory in Downloads, you can ~/Doanloads/yournewfolder or such. Note if you are already in downloads too, only "cd /yournewfolder" is necessary.

---

### Post by penguinprogrammer on 2013-01-06
> **JiuJitsu500 said:**
> You have to extract .zip folders first...

but to get into downloads it's typically "cd ~/Downloads"

Once extracted, then if there is a directory in Downloads, you can ~/Doanloads/yournewfolder or such. Note if you are already in downloads too, only "cd /yournewfolder" is necessary.

Thanks, JiuJitsu500, it worked! :)

---

