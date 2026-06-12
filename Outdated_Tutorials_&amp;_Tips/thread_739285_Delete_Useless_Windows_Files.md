---
title: "Delete Useless Windows Files"
date: 2008-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by BadPenguin86 on 2008-03-29
If you just directly moved a large group of files from a Windows drive into linux, here is a quick way to delete the useless windows files that hitchhiked onto your beautiful ext3 drive.

1. Open a terminal and type cd ~/Desktop
    (This will put you in your Desktop directory, where we will create the script that will delete the files)

2. In the terminal, type gedit deletewinfiles.sh (Or what-you-want-to-call-it.sh)
   (This will open gedit and give you a blank text document)

3. Type this into gedit:

```


find /home/user -name Thumbs.db -exec rm {} \; &&
find /home/user -name ehthumbs.db -exec rm {} \; &&
find /home/user -name ehthumbs_vista.db -exec rm {} \; 

```

If the files you are seeking to destroy are in your home directory, just  replace "user" with your user name. If those files are somewhere else, then replace "/home/user" with the directory you need. The files this will delete are the thumbs files created by XP, XP's Media Center, and Vista's Media Center, repectively. If you do not need all of these, You can delete the appropriate section of code to shorten the script.

4. Save the file and close gedit.

5. Into the terminal, type chmod +x "whatever-you-named-the-file.sh" (without quotes).

6. Type ./whatever-you-named-the-file.sh to run the script.

Now, whenever you need to run this script, you can just double click on the script and hit "run in terminal".

---

