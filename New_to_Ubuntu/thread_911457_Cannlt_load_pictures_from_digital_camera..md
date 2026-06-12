---
title: "Cannlt load pictures from digital camera."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by richie42 on 2008-09-05
Hi, I have Ubuntu and when i connect my digital camera (an HP Photosmart E217).

When I plug in the camera, F-Spot tries to load th pictures. It loads a preview for them, but when it gets to 36, it displays an error message.

```
An unhandled exception was thrown: Number overflow.

  at (wrapper managed-to-native) System.Object:__icall_wrapper_mono_array_new_specific (intptr,int)
  at LibGPhoto2.CameraFile.GetDataAndSize () [0x00000] 
  at GPhotoCamera.GetPreviewPixbuf (.GPhotoCameraFile camfile) [0x00000] 
  at FSpot.CameraFileSelectionDialog.GetPreviews () [0x00000] 
  at FSpot.CameraFileSelectionDialog.CreateInterface () [0x00000] 
  at FSpot.CameraFileSelectionDialog.Run () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
  at FSpot.Core+ImportCommand.Execute () [0x00000] 
  at FSpot.Core.Import (System.String path) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42
```

---

### Post by unutbu on 2008-09-05
What happens if you run```

gphoto2 --port usb: --get-all-files 
```
(run this in the directory where you want the pictures)

---

### Post by richie42 on 2008-09-05
What's a directory
how do I run this?

---

### Post by philinux on 2008-09-05
Try using the app gthumb it's in the graphics menu.

---

### Post by richie42 on 2008-09-05
I don't see gthumb....

---

### Post by halitech on 2008-09-05
> **richie42 said:**
> What's a directory
how do I run this?

open a terminal (Applications - Accessories - Terminal)

type in cd Photos and press Enter

then type in ```
gphoto2 --port usb: --get-all-files
```

if you want to try gthumb, in the terminal type in```
sudo apt-get install gthumb
```

---

### Post by richie42 on 2008-09-05
This happened

```
richard@theSelbys:~$ cd Photos
richard@theSelbys:~/Photos$ gphoto2 --port usb: --get-all-files
The program 'gphoto2' is currently not installed.  You can install it by typing:
sudo apt-get install gphoto2
bash: gphoto2: command not found
richard@theSelbys:~/Photos$ 


```

---

### Post by philinux on 2008-09-05
> **richie42 said:**
> I don't see gthumb....

Sorry I forgot it's not installed by default. It is better than f-spot.

Use the Add/Remove to install it. It's in the graphics section just scroll down the list.

---

### Post by halitech on 2008-09-05
> **richie42 said:**
> This happened

```
richard@theSelbys:~$ cd Photos
richard@theSelbys:~/Photos$ gphoto2 --port usb: --get-all-files
The program 'gphoto2' is currently not installed.  You can install it by typing:
sudo apt-get install gphoto2
bash: gphoto2: command not found
richard@theSelbys:~/Photos$ 


```

type in```
sudo apt-get install gphoto2

``` in the terminal

---

