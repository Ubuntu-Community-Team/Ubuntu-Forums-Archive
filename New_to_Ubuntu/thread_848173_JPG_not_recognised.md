---
title: "JPG not recognised"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by RobHK on 2008-07-03
When JPG files are displayed no image appears in the icon. When I doubleclick on the icon the image appears in the icon but the file does not open. Instead I get this error message:

"Cannot open xxxx.jpg
The filename xxxx.jpg indicates that this file is of type "jpg document". The contents of the file indicate that the file is of type "JPEG image". If you open this file, the file may present a security risk to your system.
Do not open the file unless you created the file yourself, or you received the file from a trusted source. To open the file rename the file to the correct extension for "JPEG image", then open the file normally. Alternatively use the Open With menu to choose a specific application for the file."


I can open the file by right clicking and selecting the application to use. If I rename the file to .jpeg extension, it displays the icon normally and opens normally with a double click.

How can I reset the association correctly for files with .jpg extension?

TIA.

---

### Post by 4-Ever-Euphemistic on 2008-07-03
> **RobHK said:**
> When JPG files are displayed no image appears in the icon. When I doubleclick on the icon the image appears in the icon but the file does not open. Instead I get this error message:

"Cannot open xxxx.jpg
The filename xxxx.jpg indicates that this file is of type "jpg document". The contents of the file indicate that the file is of type "JPEG image". If you open this file, the file may present a security risk to your system.
Do not open the file unless you created the file yourself, or you received the file from a trusted source. To open the file rename the file to the correct extension for "JPEG image", then open the file normally. Alternatively use the Open With menu to choose a specific application for the file."


I can open the file by right clicking and selecting the application to use. If I rename the file to .jpeg extension, it displays the icon normally and opens normally with a double click.

How can I reset the association correctly for files with .jpg extension?

TIA.


Right,JPG files that you have saved off the internet etc?

Chances are that the file hasnt been saved correctly.

Also,do other gifs get displayed in your browser?

---

### Post by unutbu on 2008-07-03
> **RobHK said:**
> 
I can open the file by right clicking and selecting the application to use. 

How can I reset the association correctly for files with .jpg extension?

TIA.

Have you already tried this:
[http://ubuntuforums.org/showthread.php?t=48516](http://ubuntuforums.org/showthread.php?t=48516) ?

What you said sounds like you've already tried right clicking on the file -> Open with other application. That is the standard method of setting the default application based on file extension.

---

### Post by RobHK on 2008-07-03
> **4-Ever-Euphemistic said:**
> Right,JPG files that you have saved off the internet etc?

Chances are that the file hasnt been saved correctly.

Also,do other gifs get displayed in your browser?

All JPGs. Mainly from my camera. On my other Ubuntu installation they work OK.

PNG work fine. JPG too, if renamed to JPEG. Haven't tried GIF.

---

### Post by RobHK on 2008-07-03
> **unutbu said:**
> Have you already tried this:
[http://ubuntuforums.org/showthread.php?t=48516](http://ubuntuforums.org/showthread.php?t=48516) ?

What you said sounds like you've already tried right clicking on the file -> Open with other application. That is the standard method of setting the default application based on file extension.
Yes, I have. With several applications.

---

### Post by unutbu on 2008-07-03
Right-click on the image, go to Properties, Click on the "Open With" tab, and select or add the image viewer you wish to use... or have you tried that too?

---

### Post by RobHK on 2008-07-04
> **unutbu said:**
> Right-click on the image, go to Properties, Click on the "Open With" tab, and select or add the image viewer you wish to use... or have you tried that too?

Yes,I have.

But I have found other problems with the setup so I think I am going to re-install.

Thanks for the help, guys.

---

### Post by iaculallad on 2008-07-04
Another way to determine the real file type of a file is using the **file** terminal command.

```
file file_name.jpg
```

---

### Post by ramjet_1953 on 2008-07-04
I have found that some applications are case sensitive to file extensions.

I can't remember which one it was recently but it involved .jpg files and wouldn't recognise them if the suffix was .JPG but was happy with .jpg or jpeg.

Regards,
Roger :cool:

---

### Post by jepong on 2008-07-04
This is also a problem on some of my JPG especially one coming from my Sony Ericsson P990i. But JPG from my Canon PowerShot 540 was recognize by Ubuntu.

---

