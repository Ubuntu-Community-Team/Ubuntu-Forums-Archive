---
title: "Bash script that download, unzip archive and create text info file"
date: 2020-11-08
forum: New to Ubuntu
---

### Post by delq4kata on 2020-11-08
[COLOR=#242729][FONT=Arial]I need a bash script that downloads (from URL) an archive in the /tmp directory, unzip it and create a text file with information - date of unzipping, time of unzipping, file size and file name. All scripts and comments are welcome. Thanks in advance guys![/FONT][/COLOR]

---

### Post by ActionParsnip on 2020-11-08
wget can download the file for you. You can then use unp to extract it easily.
du will be good to show file and folder sizes. 
Date and time can be added to text files. For the full date / time use this sort of thing 
[https://tecadmin.net/get-current-date-and-time-in-bash/](https://tecadmin.net/get-current-date-and-time-in-bash/)

---

