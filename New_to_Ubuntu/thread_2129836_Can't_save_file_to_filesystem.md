---
title: "Can't save file to filesystem"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by ctbuzzy on 2013-03-27
Sorry if I'm repeating a question, but I searched & didn't find a thread that was directly on point.

I'm trying to save a .odt file to a virtual-machine shared folder in the /File_System/media directory on ubuntu, but I keep getting messages that the File System is read-only & won't allow me to save anything there. This defeats the purpose of the shared folder, as I can only save documents to that folder from the direction of my Windows 7 host. I would like to be able to save files there from both the host (Win7) & the guest (the ubuntu virtual machine). Hence the "shared" aspect of a shared folder.

So my real question is, how do I make it so I can save files in a folder on the File System? Do I need to change to a root user? How can I do this & still use GUI?

Thanks much!

---

### Post by ibjsb4 on 2013-03-27
Root is the owner

```
gksudo nautilus
```

---

### Post by Kazi Waseef on 2013-03-27
Some directories are made read-only for users to ensure security. This is one of the reasons why there is no risk of virus destroying your system files. But dont worry there is a solution...

Are you using the save feature of open office, or are you copying an .odt file to the desired folder?

Create an .odt file (lets say myfile.odt) 
copy it to the desired directory (/home/your_username/your_directory/) from (/home/another_directory/)

To do this open the terminal (ctrl+alt+t) and type:
```

  cd /home/another_directory/
  sudo mv myfile.odt /home/your_username/your_directory/

```
Then open "open office" or "Libre Office" (whichever you use) and edit files that exist in locked directories then type:
```

  gksudo openoffice /home/your_username/your_directory/myfile.odt

```
or
 ```

  gksudo libreoffice /home/your_username/your_directory/myfile.odt

```
This will open "Open Office" or "Libre Office" and you can save and edit in locked directories.

---

### Post by ctbuzzy on 2013-03-27
Thanks! It took me a while, but that's just par for the course. It worked like a charm.

---

