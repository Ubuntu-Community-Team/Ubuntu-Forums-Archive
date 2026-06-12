---
title: "how to access a folder in terminal"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by Seadevil on 2012-11-04
hello, I unzipped an archive in ubuntu 12.10 and it created a folder in the downloads folder. I can navigate to it and go into it
in Natulis?  However, I cannot get to it in the Terminal.  
I believe it's a "hidden" folder ? as it is in blue like the dot folders.  Terminal says:  no such folder.

How do i fix this ?  thanks

---

### Post by jonathandawdy on 2012-11-04
In Ubuntu if you are in a file browser you can veiw the hidden files by pressing Ctrl-H are clicking on view and toggle veiw hidden files.

Also a little note when you do this the hidden files will start with a . that is how the files are marked hidden.

Example .cache

---

### Post by SeijiSensei on 2012-11-04
Use the -a switch with ls, e.g., "ls -a /home/username" will show all files and folders including hidden ones.  If you want to navigate to a hidden folder, just make sure to include the dot.  For instance, you probably have a .gconf folder in your home directory.  You can enter it from the prompt with "cd /home/username/.gconf".  ("cd" is the "change directory" command.)

---

### Post by Seadevil on 2012-11-04
Thank you all for the response.  fixed it.

---

