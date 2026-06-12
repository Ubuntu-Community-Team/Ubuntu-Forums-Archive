---
title: "How to copy long file path"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-07-22
Is there an easy method of copying the filepath; for instance using Nautilus;  to a particular file once it is found ? A long file path scrolls along the top of a window above a tab, I can make a note, and copy  by writing down the information.

Presumably this may be done easily from the CLI.

I know I may click on the file and check the file properties, but these sometimes truncate. 

Also are there any particular constraints on length of filepath ?

I am using 64 bit Ubuntu 12.04 LTS on ext4 filesytem

---

### Post by Bucky Ball on 2012-07-22
Not sure I follow, but ... From memory, you have a choice of whether to see an address bar in Nautilus /like/this/to/your/file or as 'blobs' with  directory names. In the former you can just select the path in the address bar and paste it into a terminal as the path rather than writing it down. Remember: You can copy from all sorts of places in Linux. ;)

I use PCmanFM myself and the address bar is /just/like/that. Makes life easier, at least for me.

PS: If you want to dabble with this in a terminal:

dir = directory; cd = change directory; therefore:

```
dir /home
```... will give you the contents of your home directory.

```
cd /media/music/Beatles
```... will change the current 'working' directory to /media/music/Beatles. Now, issuing just:

```
dir
```... will give you a listing of what's in the directory /media/music/Beatles as you are 'in' that directory. 

Have fun ...

[PS: Google 'maximum filepath length linux'.]

---

### Post by NTL2009 on 2012-07-22
When I right-click a file in Nautilus, and select 'copy', I can paste into a text editor (I used gedit), and it pastes the full path. It is in my copy buffer in ClipIt also.

Example:

```
/boot/grub/locale/en_GB.mo
```

Is that what you want? edit/add - there is no apparent limit on the path length, I was able to do very deeply nested files also

-NTL2009

---

### Post by dcsoldschool53 on 2012-07-22
In nautilus, press the keys```
Ctrl + L
``` or click go in nautilus > location, this will change the information in the address bar to something you can copy then paste in the terminal.

In a terminal to find something, you will need to use the find or locate command if you know the name of the file you want.

---

### Post by sudodus on 2012-07-22
You can just drag-and-drop from a file icon in Nautilus to a terminal window, and the /path/and/filename is written. You can do the same with the 'blobs' describing the working directory ('blobs' as defined in post #2 by Bucky Ball).

---

### Post by Bucky Ball on 2012-07-23
> **dcsoldschool53 said:**
> In nautilus, press the keys```
Ctrl + L
``` or click go in nautilus > location, this will change the information in the address bar to something you can copy then paste in the terminal.



> **sudodus said:**
> You can just drag-and-drop from a file icon in Nautilus to a terminal window, and the /path/and/filename is written. You can do the same with the 'blobs' describing the working directory ('blobs' as defined in post #2 by Bucky Ball).

Both great tips, cheers! The latter; guess you could drag and drop the icon from any file manager ...

---

### Post by NikTh on 2012-07-23
Hi , 
also Ubuntu has pre-installed the bash-completion package. This package help user to auto-fill the path (or command) with Tab key. So if you know the first and/or second path , then you can search (kinda) the next path (until the last file) by pressing Tab key. But this method requires to know where the file is , it just help you to fill the path (kinda automatically)
Thanks

---

### Post by aka-John99 on 2012-07-24
Thanks to everyone for the replies. This is not a subject I have had time to get back to yet. I was noticing some truncation, but have not had time to study and try the answers yet.

---

### Post by aka-John99 on 2012-08-02
Thanks again for all the information.

I had not noticed the tiny scroll tiny arrows at the end of the blobs|breadcrumbs, so although the displayed info was truncated it was in fact all still available.

I also was not aware of the ***Ctrl + L*** option to  display the Location path as text (and ***Esc ***to reverse the option).   

I have now been trying the advice and putting it to use; so have now marked the thread as solved. As often the case there is more than a single method of achieving the objective.

---

### Post by monkeybrain2012 on 2012-12-17
> **aka-John99 said:**
> Is there an easy method of copying the filepath; for instance using Nautilus;  to a particular file once it is found ? A long file path scrolls along the top of a window above a tab, I can make a note, and copy  by writing down the information.

Presumably this may be done easily from the CLI.

I know I may click on the file and check the file properties, but these sometimes truncate. 

Also are there any particular constraints on length of filepath ?

I am using 64 bit Ubuntu 12.04 LTS on ext4 filesytem

I like to be able to cut and paste the file path from Nautilus. The fancy way Nautilus displays  path by default  is not useful for my purpose. 

To fix this install dconf-tools, then open the dconf-editor from the dash, choose on the left panel org > gnome >  nautilus > preference and check the box "always use location entry" on the right panel.

---

