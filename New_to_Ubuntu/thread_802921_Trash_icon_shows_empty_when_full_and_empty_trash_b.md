---
title: "Trash icon shows empty when full and empty trash button grayed"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Ioky on 2008-05-21
As the Title say. any one know how to fix that?

The empty trash button grayed in the trash window, even when there is trash. and I can't lick on it to delete the stuff. however, trash icon is the only way I can really empty my crash. The one on the Desktop doesn't work, I do use gconfgi- editor to set it up.

---

### Post by drs305 on 2008-05-21
If you are using hardy, try just emptying the trash from the terminal and see if the icons change:
```
rm -r /home/USERNAME/.local/share/Trash
```

---

### Post by Ioky on 2008-05-21
> **drs305 said:**
> If you are using hardy, try just emptying the trash from the terminal and see if the icons change:
```
rm -r /home/USERNAME/.local/share/Trash
```

The icon never goes full, what else it can change to?

I am not the only one who has this problem, I see a few post that describe the same thing, However no one really tell how to fix it. 
haha Maybe that is a Bug then

---

### Post by drs305 on 2008-05-21
> **Ioky said:**
>  even when there is trash. and I can't lick on it to delete the stuff. however, trash icon is the only way I can really empty my crash. 

The above command should have emptied you user's trash. It is not as convenient as clicking on the trash icon, although it would be simple enough to make a shortcut on the panel for it. As to why the icons don't change, I don't know.

---

### Post by Ioky on 2008-05-21
I think it is more like the Trash - folder what whatever, it call can't recognize there is Trash in the Trash folder, as I said, not just the icon doesn't change, but also the "Empty Trash" button in side the Trash Windows is grayed which I can't use it to empty my Trash, Just wondering is that can be a bug and some one know how to fix it. 

It is not a very big deal and I do know how to empty my trash from command line, but it kind of bother me a bit. haha 

just wondering any one can fix it. 

Thanks for the help though

---

### Post by drs305 on 2008-05-21
Now I'm curious - is it the same on the panel? Does it do it on both? If you only have the icon on one of the two, maybe tyring the other location would work. 

I am not having that problem (good for me anyway). I hope you can get it solved. :D

---

### Post by Ioky on 2008-05-21
No the one on the panel always works, however, The one on the Desktop sometime work, but sometime doesn't. I don't know has this do with that ubuntu 8.04 have a new location for the trash(I mean the actual location of the trash folder, not the icon). so yeah.

Can you give me more detail on how to change it's location?  I am not so sure what you mean, and how to do it. 

Thanks for the help

---

### Post by drs305 on 2008-05-21
> **Ioky said:**
> Can you give me more detail on how to change it's location?  I am not so sure what you mean, and how to do it. 

I just meant that if you had it on the desktop you could try putting one on the panel, or if it was on the panel, try putting one on the desktop. But you have already done that. For me, all I use is the one on the panel and it works. I don't even have it on my desktop, which may be the reason I wasn't even aware of the bug until you posted your problem. Hope you find an answer someday.

---

### Post by jason6g on 2008-11-26
Anyone figure this out? mine is doing this as well.

i have the trash folder bookmarked and that icon would change on its own just fine - as would the "empty trash" button in the trash window.

within the past week this feature broke and works similar how the op described - possibly an update broke it?

---

### Post by drs305 on 2008-11-27
> **jason6g said:**
> Anyone figure this out? mine is doing this as well.

i have the trash folder bookmarked and that icon would change on its own just fine - as would the "empty trash" button in the trash window.

within the past week this feature broke and works similar how the op described - possibly an update broke it?

One possibility of why the 'empty trash' button is greyed out might be that the system thinks there is no *user* trash to be emptied. If there is nothing in the trash bin, the button is greyed out as you describe. If the trash was owned by *root* but ended up in your local trash, perhaps that would give the same indication since the *user* can't empty it. 

Try opening your file browser with administrative privileges with the following command(s). You will see a 'Trash' folder. Delete individual files inside the 'Files' subfolder using SHIFT-DEL or simply delete the entire Trash folder - it will regenerate. The commands are for Hardy/Intrepid:
```
gksudo nautilus $HOME/.local/share/
```

If that doesn't solve it, also empty the root trash. 
```
gksudo nautilus /root/.local/share/
```

---

### Post by imtheguru on 2009-09-26
> **Ioky said:**
> I think it is more like the Trash - folder what whatever, it call can't recognize there is Trash in the Trash folder, as I said, not just the icon doesn't change, but also the "Empty Trash" button in side the Trash Windows is grayed which I can't use it to empty my Trash, Just wondering is that can be a bug and some one know how to fix it. 

It is not a very big deal and I do know how to empty my trash from command line, but it kind of bother me a bit. haha 

just wondering any one can fix it. 

Thanks for the help though
The reasons for it are not too clear to me, but i believe it occurs when the Trash applet fails to communicate correctly with the Gnome/Bonobo layer.

Solution is to remove the Trash applet from the panel and add a new Trash applet in its place. Alternatively, restart Gnome.

Cheers.

---

### Post by Dennis N on 2009-09-26
Occasionally I had this same problem with the greyed empty trash button in Ubuntu 8.04. What I did is just right-click on the trash icon in the lower panel and select "empty trash" from the context menu which always worked.

As I recall, the icon also may or may not change immediately to show empty, but would be ok on the next startup.

I have not seen this problem in my current version, 8.10.

---

### Post by joereith on 2009-10-02
It works to remove the trash applet from the panel and then re-add it. It will show up empty again.

---

