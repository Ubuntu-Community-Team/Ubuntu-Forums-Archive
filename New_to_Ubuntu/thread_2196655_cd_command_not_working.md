---
title: "cd command not working?"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by apos124 on 2013-12-30
Hello I'm trying to install utorrent on Ubuntu 13.10. Utorrent is in my downloads folder. I'm trying to navigate to the folder using the cd command so I can extract the tar.gz file, but I am getting this error:

hierophant@hierophant-Satellite-C655D:~$ cd /home/hierophant/downloads/utorrent-server-3.3-ubuntu-13.04-i386-30235.tar.gz
bash: cd: /home/hierophant/downloads/utorrent-server-3.3-ubuntu-13.04-i386-30235.tar.gz: No such file or directory
hierophant@hierophant-Satellite-C655D:~$

What I am doing wrong? Thank you for taking time to help!

---

### Post by zacktu on 2013-12-30
You're trying to cd to the name of the file.  Instead use 

cd /home/hierophant/downloads

so that you'll be in the directory containing the file.

---

### Post by steeldriver on 2013-12-30
Hello and welcome to the forum

utorrent-server-3.3-ubuntu-13.04-i386-30235.tar.gz is a **file** not a folder (directory) - you need to cd to the directory that **contains** it i.e.

```
cd /home/hierophant/downloads
```

Also note that Linux file and directory names are case-sensitive and the default downloads directory is actually called **D**ownloads so unless you've changed it you probably want

```
cd /home/hierophant/Downloads
```

FYI you can use the abbreviation ~ for your home dir

```
cd ~/Downloads
```

---

### Post by apos124 on 2013-12-30
Thank you for the correction I can navigate with cd now, but after I extract the file I try to complete the installation with the commands ./configure, make, and sudo make install. It gives me this error:

hierophant@hierophant-Satellite-C655D:~/Downloads$ tar xvzf utorrent-server-3.3-ubuntu-13.04-i386-30235.tar.gz
utorrent-server-alpha-v3_3/
utorrent-server-alpha-v3_3/utserver
utorrent-server-alpha-v3_3/docs/
utorrent-server-alpha-v3_3/docs/Server_Changes.txt
utorrent-server-alpha-v3_3/docs/Changes.txt
utorrent-server-alpha-v3_3/docs/style.css
utorrent-server-alpha-v3_3/docs/license.txt
utorrent-server-alpha-v3_3/docs/uTorrent_Server.txt
utorrent-server-alpha-v3_3/docs/Server_Changes.html
utorrent-server-alpha-v3_3/docs/Server_Changes.pdf
utorrent-server-alpha-v3_3/docs/uTorrent_Server.pdf
utorrent-server-alpha-v3_3/docs/ut-logo.gif
utorrent-server-alpha-v3_3/docs/uTorrent_Server.html
utorrent-server-alpha-v3_3/docs/footer_ut_address.gif
utorrent-server-alpha-v3_3/webui.zip
hierophant@hierophant-Satellite-C655D:~/Downloads$ ./configure
bash: ./configure: No such file or directory
hierophant@hierophant-Satellite-C655D:~/Downloads$ 

After the ./configure command is used successfully then how do I use the make and sudo make install commands? Thank you for your help guys!

---

### Post by steeldriver on 2013-12-30
Where are you getting the instructions that you should run ./configure and make? Based on the file list from the tar command, it is not a source code package

---

### Post by oldos2er on 2013-12-30
There's nothing to configure, you just run the file utserver. ```
cd ~/Downloads/utorrent-server-alpha-v3_3

./utserver
```

---

### Post by apos124 on 2013-12-30
When I run ./utserver nothing happens? It dosen't give me an error but nothing comes up either.

hierophant@hierophant-Satellite-C655D:~$ cd ~/Downloads/utorrent-server-alpha-v3_3
hierophant@hierophant-Satellite-C655D:~/Downloads/utorrent-server-alpha-v3_3$ ./utserver

---

### Post by steeldriver on 2013-12-30
if it's what I think it is, it runs a little stand-alone web service and you need to connect to it via a browser using the URL [http://localhost:8080/gui/](http://localhost:8080/gui/) 

see here: [http://www.webupd8.org/2010/09/utorrent-is-finally-available-for-linux.html](http://www.webupd8.org/2010/09/utorrent-is-finally-available-for-linux.html)

---

### Post by apos124 on 2013-12-30
You guys are awesome thanks!!!!

---

