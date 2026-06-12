---
title: "Themes in 11.10"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by JamesParnell on 2011-12-05
Is there any themes (other than stock) for 11.10? and if so how do i get/install them. Thanks :)

---

### Post by JRV on 2011-12-05
You can find themes in Software Center.
Or try Google, search "Ubuntu Themes"

To change themes open a terminal and install gnome-tweak-tool:

```

sudo apt-get update
sudo apt-get install gnome-tweak-tool 

```

Then run the program:

```
gnome-tweak-tool
```

---

### Post by Frogs Hair on 2011-12-05
You need GTK 3 themes for 11.10 . [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=164776999bd3425bd261fe5e1104f627](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=164776999bd3425bd261fe5e1104f627)

(Installing Downloaded Themes / Icons)

Install the Gnome Tweak Tool / Advanced Settings from the software center for making theme selections.  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Ctrl + H to open the hidden folder option in Nautilus .

(All Users) Use gksudo nautilus > File System / usr / share / themes or icons .

Download , extract the packages , and place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .

---

### Post by BRUCEY8D on 2011-12-05
where do i find the advance settings folder??

---

### Post by kensum on 2011-12-05
There is no advance themes folder. What the above post was saying is to download a theme, use gksu natilus to run nautilus in root and then you just click the file you downloaded, extract it and then put the folder in usr/share/themes. gnome-tweak-tool, is called advanced settings in your menu. You will use this to select the theme you want to use. You can also use the gnome-tweak-tool to install your themes...just extract the file in whatever folder your use for your downloads and then open advanced settings(gnome-tweak-tool) and under themes, click the folder button and select your extracted theme. I hope this helps make it clearer.  ps, you can just open nautilus, file manager, and browse your usr/share/ themes to see what is in there and kinda get an idea of what is going on.:P

---

### Post by BRUCEY8D on 2011-12-05
thanks! but i get this "permission denied" error... 
and can you explain "...gksu natilus to run nautilus in root..." are those codes? i JUST started exploring ubuntu 11.10 on a old crappy laptop, so i wldnt mess up my netbook which i plan to transfer what i learn in to. :)

---

### Post by Frogs Hair on 2011-12-05
> where do i find the advance settings folder??It is not to a folder it is an application .

In order to add , remove , or make changes to the file system you must open nautilus with elevated permissions using  the following command in the terminal and entering a password . In order to make themes available for all users you would want to use this location  ```
gksudo nautilus 
```What I do is place my extracted  theme folders on the desktop an drag them into the themes or icons folder and delete the folders on the desk when done .

If  only want themes for yourself see the link .  [http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml)

---

