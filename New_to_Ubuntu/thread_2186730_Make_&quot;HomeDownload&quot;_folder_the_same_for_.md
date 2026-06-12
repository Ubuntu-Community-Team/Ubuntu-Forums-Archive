---
title: "Make &quot;Home/Download&quot; folder the same for all users"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by shabuboy on 2013-11-08
Hello,

Is it possible to set the "home/download" folder to be the same for all users? If so, how? Did a few internet searches and no luck. At least nothing in plain English I could understand    :D

Would like to make it a default for any future users.

---

### Post by BBQdave on 2013-11-08
> **shabuboy said:**
> Is it possible to set the "home/download" folder to be the same for all users?

If you have Ubuntu Unity, might be better to use the **Public** folder across accounts. Usually, Linux distros are set with individual accounts, with the users deciding what to share.

I would think the Home directory would become cluttered and confusing, if shared by multiply users.

---

### Post by shabuboy on 2013-11-08
hmmm... let me rephrase the question...  How can I make a folder, be the same for all users? It could be downloads, or music, or videos. I do not want home to be the same. Only one of the folders in home.

---

### Post by BBQdave on 2013-11-08
Use [**Ubuntu's Public Folder**]("http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/") might be of interest to you :)

---

### Post by shabuboy on 2013-11-08
I did check it already. However, what I found for it is only "sharing". Users will have to browse network/computername to select the share dir. That is not what I am looking for.

I want the following:
- User X logs in
- Creates a video in his /home/video folder
- Logouts

- User Y logs in
- Goes to his /home/video folder and can also see (RW) video from User X

---

### Post by heir4c on 2013-11-08
You can create a separate partition for all kind of data and than change the settings to put the downloaded files in that DATA partition instead of /home/*username*/Downloads. (Like in FireFox the default is)
Even if you have other versions of Ubuntu on or a different Linux distro on that disk, I think you can use that partition to set the downloaded files on. 
I will try it here out at my computer.

Edit: It will work if the partition mount automatic when you boot up.
Otherwise you can create a folder and give rights to a new group and make the users member of that group, so than they can access the partition.
(If you install gnome-system-tools you can make groups and also make all users member of that group in a graphical environment.)

---

### Post by shabuboy on 2013-11-08
So lets see if I get this straight...
- Create a group and add users to it. So far so good.
- Create a folder somewhere and make the owners the new group. Any recommendations? I was thinking perhaps "/media/share/downloads" or "/home/public/downloads". So far ok.

And now, how do I make current and future users be able to log into Ubuntu, go to Home folder, click on downloads and open one of the locations mentioned above? I guess there is got to be a default config somewhere to point to another location besides $HOME.

---

### Post by pqwoerituytrueiwoq on 2013-11-08
the guest user will not have have access to this folder, no idea i have tried to give it write access to shared content before never figured it out
this should get you close to what you want to do
```
sudo mkdir /usr/local/Downloads
sudo chmod 777 /usr/local/Downloads
sudo mv /home/*/Downloads/* /usr/local/Downloads
sudo chown -R root:root /usr/local/Downloads/*
sudo chmod -R 777 /usr/local/Downloads/*
sudo rmdir /home/*/Downloads
sudo ln -s /usr/local/Downloads /home/*/Downloads
```
only issues that you will have is new files being own by different users
you could add a script to lightdm's session start/exit
edit [FONT=courier new]/etc/lightdm/lightdm.conf[/FONT] and add this line
```
session-cleanup-script=sh -c 'chown -R root:root /usr/local/Downloads/* & chmod 777 /usr/local/Downloads/* &'
```

if you created a fat32 partition for the downloads yu would not hve any need for th chmod/chown stuff

---

### Post by heir4c on 2013-11-08
You can rightclick on the folder/directory and make a link and place it in the home folder of the user. 

 (For creating accounts/groups in graphical way you can install gnome-system-tools)

---

### Post by shabuboy on 2013-11-08
hmmm, those only apply to existing users, what about future users who do not have a home folder yet?

Found something, exactly what I want, However, cannot find the setting for the umask 022.
[http://askubuntu.com/questions/18103/how-can-i-change-the-default-location-of-content-directories-eg-pictures-templ](http://askubuntu.com/questions/18103/how-can-i-change-the-default-location-of-content-directories-eg-pictures-templ)

---

### Post by shabuboy on 2013-11-08
Well, cannot believe it took me soooooo long, but got it.
Followed the instructions on the link from earlier. Found the umask 022 in /etc/logins.defs file.

Also, if you follow the exact scenario, do not create the "Music" folder until the umask, chmod and chown have been executed. Took me a while to figure this one out.

After doing it as in the link, created a new user, added to group,  logged in and whala!!! New users do have the shared dir.

---

