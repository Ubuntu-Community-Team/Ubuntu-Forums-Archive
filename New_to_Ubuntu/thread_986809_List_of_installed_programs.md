---
title: "List of installed programs"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-11-18
I recently installed Ubuntu 8.10 intrepid ibex. There seems to be three places that show me the programs that are installed on my computer.
(1) Add-Remove Applications (this list is not comprehensive)
(2) In Synaptic Package Manager, in the far left column, you can click on the word "Installed". This appears to be a comprehensive list of all installed programs.
(3) In Synaptic Package Manager under File>History, you get a list of all the programs that have been installed, after your initial installation, arranged by date.

None of these lists can be copied to a text document or a spreadsheet. You cannot select the items and and copy to another document.

I would like to make a copy of all the installed applications on a spreadsheet,or at least into an openoffice text document. Is there any way to do this? 

JBA2337

---

### Post by cosmoshell on 2008-11-18
dpkg --get-selections | awk '{if ($2 == "install") print $1}'> \

 /home/whatever your acount name is/Desktop/list.txt

---

### Post by expatCM on 2008-11-19
The above command works nicely.

```
dpkg --get-selections | awk '{if ($2 == "install") print $1}'> \/home/username/Desktop/list.txt
```


If you do dpkg -l you get a huge list which includes drivers and all sorts of things ...  but you get the version numbers.  How do you edit the above command to show the version installed?

---

### Post by JBA2337 on 2008-11-19
Thanks very much for the command that you sent that generates a list of all installed packages. It works perfectly.

I would like my list to be similar to the list that you get with Synaptic Package Manager's list of installed packages. It lists each installed package, plus the following:  Installed Version, Latest Version, Size, Download and Description. 

What do I need to add to get a list like the one above?

Thanks!

JBA2337

---

