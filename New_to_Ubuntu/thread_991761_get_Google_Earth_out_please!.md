---
title: "get Google Earth out please!"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Nu music project on 2008-11-24
(ubuntu studio)

I installed google earth from the .bin file.  It doesn't work and crashes the Laptop (inspiron 1525).  No big deal.  I didn't need it anyway.  However it does not appear in add/remove or synaptic so I guess I need to do it in terminal.
Would someone give me a guide please.

---

### Post by ad_267 on 2008-11-24
If you installed as root you should be able to do:

```
sudo /opt/google-earth/uninstall
```

There's also an uninstallation section at [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by Nu music project on 2008-11-24
nope.
The instructions I followed installed it in the home directory.
Change directory to "Home" and repeat?

---

### Post by Sealbhach on 2008-11-24
> **ad_267 said:**
> 
There's also an uninstallation section at [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I often wondered about undoing that type of install. The guide here recommends using rm -rf which just means basically to delete any folders or files that the installation created. 

That's the way I have been doing it so glad to see that it's OK.

There's a Google Earth in the repos, I think, which might be more stable.


.

---

### Post by hyper_ch on 2008-11-24
and I recommend to install it from the medibuntu repos...

---

### Post by Nu music project on 2008-11-24
yep, but I don't want a better wayto in stall it.  I want a better way to get rid of it.

---

### Post by Michael.Godawski on 2008-11-24
There should be an uninstall script in the directory you have install Google Earth.
Try 
```
sudo sh /path/to/directory/uninstall
```

and here I've found another how-to how to :) remove GE. 
[http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html](http://www.ehow.com/how_2279483_uninstall-google-earth-ubuntu.html)

---

### Post by Tom--d on 2008-11-24
If its in your home directory, just delete it.

---

### Post by Nu music project on 2008-11-24
> **Tom--d said:**
> If its in your home directory, just delete it.

really? Thats it? no leftover bits?

---

### Post by Sealbhach on 2008-11-24
> **Nu music project said:**
> really? Thats it? no leftover bits?

No. Look a this command from the how-to


```
"sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth" 
```

There's bits of it in /usr/share and /opt


.

---

### Post by philinux on 2008-11-24
When you need to install it click the medibuntu link below.

Then version 4.3 will be in the repo's to install.

---

### Post by ad_267 on 2008-11-24
> **Sealbhach said:**
> No. Look a this command from the how-to


```
"sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth" 
```

There's bits of it in /usr/share and /opt


.

Not if it's in the home directory. And yes there will be left over bits like launchers. There should be an uninstall script in your home directory.
```
cd ~/google-earth
./uninstall
```
Just modify the first line to where your google earth is installed.

---

### Post by Kellemora on 2008-11-25
Hi NMP

Every file you install LEAVES TONS of stuff behind when you uninstall it!

I have a program that I ran the uninstall program for and it reinstalls it instead of uninstalls it.

I deleted EVERY FILE I could find regarding that program.
Tried uninstall again, since it still appears on the drop down list.
It reinstalled it again.
I removed all the folders, pulled the LAN cable, just in case it was fetching it, and it still installed itself again.
So it's HIDING on the hard drive somewhere INTACT!

But I'm looking for it and some day, enchimed in some remote hidden folder, 40 levels deep under a secret code name, I'm going to find it, hi hi..........

TTUL
Gary

---

### Post by Tony Flury on 2008-11-25
so Kellemora - just because you had one very bad experience with one application, you think that _all_ applications will be exactly the same ?

Unusual logic to say the least.

to give the flip side - I have installed a large number of applications, and then de-installed them with no files all over the place. I know some windows applications do that, but i have never seen any linux apps do it.

---

### Post by Ripfox on 2008-11-25
> **Kellemora said:**
> Hi NMP

Every file you install LEAVES TONS of stuff behind when you uninstall it!

I have a program that I ran the uninstall program for and it reinstalls it instead of uninstalls it.

I deleted EVERY FILE I could find regarding that program.
Tried uninstall again, since it still appears on the drop down list.
It reinstalled it again.
I removed all the folders, pulled the LAN cable, just in case it was fetching it, and it still installed itself again.
So it's HIDING on the hard drive somewhere INTACT!

But I'm looking for it and some day, enchimed in some remote hidden folder, 40 levels deep under a secret code name, I'm going to find it, hi hi..........

TTUL
Gary

Not so much. Most Linux apps uninstall very cleanly compared to Windows.

---

### Post by Trafferth on 2008-11-25
Hi Kellemora,

You can manually delete anything with a few judicious searches.  I installed GoogleEarth myself and uninstalled it in the following way.

1. Update the file database:

```
sudo updatedb
```

2. Go searching using the locate command:

```
locate google
```

3. Remove any directories that look like they should go e.g. ~/some/path/google-earth using the appropriate command:

```
rm -rf ~/some/path/google-earth
```

(You may need sudo if it is not in your home (~) directory):

```
sudo rm -rf /some/other/path/google-earth
```

4. Go back to step 2 and type in some other search names.  Remember that since Linux cares about case, you might want to search for google, Google, earth, and Earth as a starting point.

You should get most of the files you want to remove this way.  Of course, this is just one way of doing it.

Good luck!

- T :)

---

### Post by philinux on 2008-11-25
Also dont forget 

sudo apt-get autoremove

This removes any redundant dependencies.

---

