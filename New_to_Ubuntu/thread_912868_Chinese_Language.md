---
title: "Chinese Language"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by 3dmatrix on 2008-09-07
I am using Mint :

I recently tried to enable Chinese Language support on my system.
Nearly 70 mb of packages were downloaded and installed but ultimately nothing happened and I received the following error messages :

[B]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_8.04+20080527_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_8.04+20080527_all.deb)
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch [http://packages.linuxmint.com/pool/upstream/l/language-pack-zh-base/language-pack-zh-base_8.04+20080527_all.deb](http://packages.linuxmint.com/pool/upstream/l/language-pack-zh-base/language-pack-zh-base_8.04+20080527_all.deb)
  404 Not Found


W: Failed to fetch [http://packages.linuxmint.com/pool/upstream/l/language-pack-zh/language-pack-zh_8.04+20080527_all.deb](http://packages.linuxmint.com/pool/upstream/l/language-pack-zh/language-pack-zh_8.04+20080527_all.deb)
  404 Not Found[/B]

What can be done ?

---

### Post by drs305 on 2008-09-07
Try another server. The packages do not appear to exist on the server you cited. To change servers, open Synaptic, Settings, Repositories, Ubuntu Software. Click on the 'Download from' window, and then either chose one of the servers presented or Other. (There is a China server, and it appears my US server - [http://www.gtlib.gatech.edu/pub/ubuntu](http://www.gtlib.gatech.edu/pub/ubuntu), also has the Chinese language support).

---

### Post by 3dmatrix on 2008-09-07
Thanx !
Will try that.

Dont see anything like that here. Remember I am using Mint !

---

### Post by bumanie on 2008-09-07
I downloaded them from an Australian server a few months back - might be worth a try. I think I used the iinet server.

---

### Post by drs305 on 2008-09-07
> **3dmatrix said:**
> Thanx !
Will try that.

Dont see anything like that here. Remember I am using Mint !

Do you have a System, Admin, Software Sources? It would open the same dialog.

---

### Post by 3dmatrix on 2008-09-07
Can see an option for NEW in synaptic but have doubt about which server has Ubuntu authenticated packages. Recently while using Mepis I installed some Chinese fonts and my system became too slow and started giving strange trouble. So can you kindly suggest something to alleviate my fear.

---

### Post by 3dmatrix on 2008-09-07
Apart from looks there is not much of a difference bet Mint and Ubuntu. The core is the same. Attaching a snapshot of my Repo.

---

### Post by drs305 on 2008-09-07
> **3dmatrix said:**
> Can see an option for NEW in synaptic but have doubt about which server has Ubuntu authenticated packages. Recently while using Mepis I installed some Chinese fonts and my system became too slow and started giving strange trouble. So can you kindly suggest something to alleviate my fear.
...
Apart from looks there is not much of a difference bet Mint and Ubuntu. The core is the same. Attaching a snapshot of my Repo. 

The snapshot is of the existing enabled repositories. The 'official' repositories are the 'ubuntu' ones, but medibuntu, canonical, and I would assume mint, are also fine.

The 'failed to fetch' error messages are normally caused by your currently selected server not having a specified package, there is a password key issue, or the server isn't working. The server you tried to get the package from is working but cannot access the package.

The answer is to try another server. The snapshot you provided shows your enabled repositories but that page doesn't appear to be the one to change servers.


[B]
Added:[/B] I've searched around and if you can't do the above try installing *software-properties-gtk*. It appears this will run in Mint and can select the fastest server for you. It might also allow you to pick a different server as well.
```
sudo apt-get install software-properties-gtk
```
Run it with:
```

gksu software-properties-gtk
```

If that app,the synaptic references I gave you don't take you to a page where you can change servers, or the System, Admin, Software Sources menu is not available in Mint, you will have to wait for someone who uses Mint to tell you how to change servers so you can access the packages you want to download.  Best wishes for success.

---

### Post by 3dmatrix on 2008-09-07
I can change server but how do i come to know if a server has authorized packages or not ? The link you provided has no ubuntu.com.

---

### Post by drs305 on 2008-09-07
> **3dmatrix said:**
> I can change server but how do i come to know if a server has authorized packages or not ? The link you provided has no ubuntu.com.

The names you see are the 'authorized' mirrors for ubuntu packages. The main ubuntu server would not be able to handle all the downloads, so there are 'mirror' servers throughout the world which maintain the ubuntu software and make it available through their systems. These servers maintain some or all of the packages on the main ubuntu server. 

In your case, the server you have currently selected may not have the space, bandwidth or desire to maintain every ubuntu package (such as the Chinese language support).

Repositories you may want to avoid if you are concerned about their integrity would be the ones in the 'Third Party' tab. Since those are generally repositories you have selected, you are taking the responsibility for downloading anything from them. If you have any questions about those repositories you could post a thread asking if they are reputable.

---

### Post by 3dmatrix on 2008-09-07
That file is not on that server also :

[http://www.gtlib.gatech.edu/pub/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_8.04+20080527_all.deb](http://www.gtlib.gatech.edu/pub/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_8.04+20080527_all.deb)

---

### Post by drs305 on 2008-09-07
Edited:

I downloaded the files in your first post successfully with synaptic and the GT repository.

You can probably download it by going to this site in your browser:
[http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/]("http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/")

The file you listed first in the first post is near the bottom of the page. **Note you download the 8.04 and not the 8.10 versions.**
language-pack-gnome-zh_8.04+20080527_all.deb

Click it and it will downoad to your desktop. Click on the downloaded file and it should install. Note this is a language-pack-gnome package. 

Repeat for these two:
[http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh-base/]("http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh-base/")
language-pack-zh-base_8.04+20080527_all.deb

[http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh/]("http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-zh/")
language-pack-zh/language-pack-zh_8.04+20080527_all.deb

I will reread the thread and see if I can tell why your synaptic won't download these.

---

### Post by 3dmatrix on 2008-09-07
Installed all the files (according to synaptic) but am not sure how to start input of Chinese characters. Tried keyboard switches like Ctrl+Space or Alt+Shift but nothing happens.

---

### Post by drs305 on 2008-09-07
Again, not a Mint user, but in ubuntu it's System, Admin, Language Support. Default Language. Of course, I think that will change everything over to another language.

To add a keyboard layout (ubuntu): System, Preferences, Keyboard. Layouts. Add to select a new keyboard/language layout.

---

### Post by 3dmatrix on 2008-09-07
My default language will always remain English. Its only when I need to type in Chinese (through Pinyin) I will use some keyboard shortcut to activate that input and then again revert back to English. For this Linux uses SCIM - it is installed on my system but some how it does not works. I am able to work with ease in Xp but I dont wish to use Xp. Any help ?

---

