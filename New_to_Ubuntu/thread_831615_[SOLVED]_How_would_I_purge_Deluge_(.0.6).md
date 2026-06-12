---
title: "[SOLVED] How would I purge Deluge? (.0.6)"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by 449 on 2008-06-17
How would I going about completely purging deluge from my system. Because when I try to start it up I get this screen: 

[http://img501.imageshack.us/img501/1167/screenshotbb5.png](http://img501.imageshack.us/img501/1167/screenshotbb5.png)

And terminal spits out this long mess of stuff. I'll attach it in a text file because it's too long to post. Thanks.


I tried sudo apt-get remove --purge deluge-torrent, then reinstalling, but still no changes.

---

### Post by iaculallad on 2008-06-17
Use the Terminal command:

```
sudo dpkg --purge deluge-torrent
```

and make an uninstall (To completely remove deluge remnants) inside the source and then try installing deluge-torrent again.

---

### Post by 449 on 2008-06-17
> **iaculallad said:**
> 
and make an uninstall (To completely remove deluge remnants) inside the source and then try installing deluge-torrent again.

Could you explain this part please?

---

### Post by iaculallad on 2008-06-17
> **449 said:**
> Could you explain this part please?

That process can only be applicable if you installed deluge-torrent via tarball.

Assuming that you did install using tarball: Try to change directory to where you extracted your deluge-torrent tar file, on on your terminal, issue the command:

```
sudo make uninstall
```

Try reading the Readme file w/c comes with the tarball. Install/Uninstall procedures is listed in there.

---

### Post by 449 on 2008-06-17
> **iaculallad said:**
> That process can only be applicable if you installed deluge-torrent via tarball.

Assuming that you did install using tarball: Try to change directory to where you extracted your deluge-torrent tar file, on on your terminal, issue the command:

```
sudo make uninstall
```

Try reading the Readme file w/c comes with the tarball. Install/Uninstall procedures is listed in there.

I installed it from a .deb package.

---

### Post by bumanie on 2008-06-17
You can go to synaptic and type deluge into search and mark for complete removal.

---

### Post by iaculallad on 2008-06-17
> **449 said:**
> I installed it from a .deb package.

Open up your terminal:

```
sudo dpkg --purge remove deluge-torrent
```

---

### Post by RomeReactor on 2008-06-17
Hi. Try switching back to the Human theme and see if Deluge starts correctly; the problem might be related to the theme.

Go to Synaptic (System->Administration->Synaptic), search for Deluge there, and if it shows up mark it for 'Complete Removal'. Otherwise, run this from the terminal:
```
sudo dpkg -P deluge
```

EDIT: Before you uninstall Deluge you might want to remove the hidden **.deluge** configuration folder from your home directory and run Deluge again to see if that helps; press CTRL+H in Nautilus to see the hidden files. Or form the terminal:
```
rm -R ~/.deluge
```

---

### Post by kpkeerthi on 2008-06-17
> **449 said:**
> How would I going about completely purging deluge from my system. Because when I try to start it up I get this screen: 

[http://img501.imageshack.us/img501/1167/screenshotbb5.png](http://img501.imageshack.us/img501/1167/screenshotbb5.png)

And terminal spits out this long mess of stuff. I'll attach it in a text file because it's too long to post. Thanks.


I tried sudo apt-get remove --purge deluge-torrent, then reinstalling, but still no changes.

Before you uninstall it, close deluge and try deleting the folder **deluge **under **.config** in your $HOME directory. Restart deluge.

---

### Post by 449 on 2008-06-17
Yep, deleting the deluge folder did it. Thanks ! :)

---

