---
title: "bash scripting"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by caxuality on 2013-01-28
Hi, Ubuntu users. 

I'm having a problem in bash scripting. I want to download .gr2 files in ftp server, and place the downloaded files in $DocumentRoot/directories/directories and organize the file system image according to date. can anyone know the script ? ):P

---

### Post by Cheesehead on 2013-01-28
see  [FONT="Courier New"]man wget[/FONT]

---

### Post by caxuality on 2013-01-28
oh thanks.:p wget then URL right ? how about the script on how to organize the file system according to its date ?

---

### Post by Cheesehead on 2013-01-28
By "organize the file system image according to date," I assume you mean "set the last-modified date on the downloaded file." 

wget can do that. See the 'timestamping' section of the wget man page.

You can separately change a file's date anytime using the [FONT="Courier New"]touch[/FONT] command. See [http://askubuntu.com/questions/62492/how-can-i-change-the-date-modified-created-of-a-file](http://askubuntu.com/questions/62492/how-can-i-change-the-date-modified-created-of-a-file)

---

### Post by Impavidus on 2013-01-29
If you mean "create directory base/year/month/day/", you can use **date** to get the date. Read **man date** for precise instructions. You can store year, month and day in bash variables and then use wget with the option```
wget --directory-prefix=$DocumentRoot/$year/$month/$day
```

---

### Post by caxuality on 2013-01-29
thank you, thank you :smile: it helped me a lot. :)

---

