---
title: "file uploading application"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by vivekpandey1991 on 2012-03-23
hi all.. is there any file uploading application in ubuntu that can  upload a zip file to my ftp server and extract it on the server without having physical access to the server

---

### Post by Pand5461 on 2012-03-23
In Nautilus File -> Connect to Server. 
Or (also in Nautilus): Ctrl+L and enter your [ftp://user@ftp.server.com](ftp://user@ftp.server.com) as the "Location".

---

### Post by vivekpandey1991 on 2012-03-23
> **Pand5461 said:**
> In Nautilus File -> Connect to Server. 
Or (also in Nautilus): Ctrl+L and enter your [ftp://user@ftp.server.com](ftp://user@ftp.server.com) as the "Location".

sorrry i am a noob and hence i dont know what is nautilus file :(

---

### Post by Pand5461 on 2012-03-23
Oh, sorry. Didn't account for that.

"Nautilus" is the default file manager. You can launch it either by clicking "Home Folder" icon in the Unity launcher or by typing "Nautilus" in Dash (Dash is launched by clicking on Ubuntu logo in the Launcher).

"File" is a menu. The menu bar is revealed when you move mouse pointer at the top of your screen (maybe top-left corner, I'm not sure). Trick: you can have access to Nautilus menu without launching the application explicitly. When you haven't launched anything yet, move your mouse pointer to the top-left corner, and you'll see the menu bar.

I hope this explanation is a bit more clear.

---

### Post by codemaniac on 2012-03-23
try out Filezilla , it is a very cool GUI FTP client .
Do the below on your terminal to install filezilla
```

sudo add-apt-repository ppa:n-muench/programs-ppa
sudo apt-get update
sudo apt-get install filezilla

```

---

### Post by vivekpandey1991 on 2012-03-23
> **codemaniac said:**
> try out Filezilla , it is a very cool GUI FTP client .
Do the below on your terminal to install filezilla
```

sudo add-apt-repository ppa:n-muench/programs-ppa
sudo apt-get update
sudo apt-get install filezilla

```

filezilla uploads one file at a time .. i have around 100 folders with some files in each folder .the files are in a form of a dense tree structure.... to upload using filezilla will take centuries in my case :)

---

### Post by codemaniac on 2012-03-23
You can download by drag and dropping parent directories in filezilla .
To upload a directory from your client box to server , all you need is just right click to the directory and hit upload option .
Does it still take a century for you ?????

---

