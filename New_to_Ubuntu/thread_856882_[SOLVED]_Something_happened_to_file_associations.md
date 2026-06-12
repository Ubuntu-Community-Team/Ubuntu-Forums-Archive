---
title: "[SOLVED] Something happened to file associations"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Tart on 2008-07-11
Hello All,

Something happened to pictures/photos file association, now all my picture/photos are treaded as "plain text document". I can only open them individually by clicking "Open with" -> Open with Other Application and then selecting F-Spot or something similar. 

UPDATE: It happened to pretty much all file associations, same problem with PDFs or music files
How do I re-associate all my graphical files??

I have absolutely no idea of why it happened.
Thank you

---

### Post by MasterXandrex on 2008-07-11
You can manually associate file types by changing the mime.types file:

```

 gksudo gedit /etc/mime.types

```


Xan

---

### Post by Baelus on 2008-07-11
Try right clicking on a jpg and choose "properties" at the bottom. Click the "Open with" tab and choose "Add". Select the image viewer you want and that should associate the viewer with that file type. Then do the same for the other types (gif, png, etc).

That's the only thing I can think of. Hope it works out.

- B

---

### Post by Tart on 2008-07-11
Thank you for your reply.
As far as I can tell they are associated correctly in mime.types as (all jpg's are images).
Then I click on any file and look at the properties and go to "Open With" tab, files have correct file associations. But in Nautilus they are shown as "plain text document", and then I click on them they i'm told that they are executables.

---

### Post by Tart on 2008-07-11
I think I found the problem

```
 /etc/gnome/defaults.list 
```
for all image files it contains the following

image/bmp=eog.desktop
image/gif=eog.desktop
image/jpeg=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/png=eog.desktop

What is eog.desktop?

I replaced those with kde4-gwenview.desktop, restarted machine, but it didn't help :-(

---

### Post by Baelus on 2008-07-12
Mine says the same:

```
image/bmp=eog.desktop
image/gif=eog.desktop
image/jpeg=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/png=eog.desktop
```

Must be something else.

Maybe you'll find something in this:

[http://ubuntuforums.org/showthread.php?t=272152]("http://ubuntuforums.org/showthread.php?t=272152")

- B

---

### Post by Tart on 2008-07-12
I tried to follow recommendation in the link above. Unfortunately it didn't fix my problem :-(.

---

### Post by Tart on 2008-07-12
Additional information

As far as I can tell 

```
/usr/share/applications/mimeinfo.cache 
```
and 
```
/etc/gnome/defaults.list 
```

All have correct information. When I click on any file and check it's preference and "Open With" tab, files always show correct information. 

However, in Nautilus they are always shown as text and then I click on them it doesn't know what to do. :confused:

I'm attaching screen shot, maybe this will clarify something.

Any help is welcomed.

Thank you

---

### Post by Vivaldi Gloria on 2008-07-12
Try right clicking on a photo and make it non-executable from the permissions tab and then try double clicking it.

---

### Post by Baelus on 2008-07-12
Something from the top of my /etc/mime.types file:

"Users can add their own types if they wish by creating a ".mime.types" file in their home directory.  Definitions included there will take precedence over those listed here."

So maybe check for something weird going on in your local mime.types file, if it exists.

Otherwise, all I can offer is to make sure this line is in the /etc/mime.types file:

```
image/jpeg                                      jpeg jpg jpe
```

Best of luck.

- B

---

### Post by Tart on 2008-07-12
Thank you all for your help. But nothing seems to work :-(
/etc/ mime.types are in order :-(

---

### Post by Tart on 2008-07-13
When I try to open files in GNOME Commander,I get the following message
"No default application found for the mime-type application/octet-stream.
Open the "File types and programs" page in the Control Center to add one."

However in 'File types and programs' does not exists in the Control Center. In "File Management" everything seems to be in order.

So it looks like indeed some mime files were corrupted.  
Where is "application/octet-stream" located? .local/share/application doesn't have such file.

Is there any way to track what changes were made on Friday/Saturday, to see what corrupted the file associations and maybe reverse it?

---

### Post by Tart on 2008-07-13
I finally found the solution! So happy! :-). 
For anyone who experience the same problem 


```

sudo update-mime-database /usr/share/mime

```

This fixed it for me

---

### Post by kingcharles1666 on 2009-09-10
Thanks 4 the fix!!!
I had exactly the same issue after a power outage and this command fixed the issue.

---

