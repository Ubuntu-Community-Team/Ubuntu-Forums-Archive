---
title: "Quick Grub Bootsplash Howto"
date: 2006-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by towsonu2003 on 2006-08-25
Disclaimer: If something goes wrong and you cannot boot, it is most probable that I will **not** be able to help you. 

The bootsplash is the background you see when the grub menu is displayed right after you boot your computer. By default, the background is black in Ubuntu. These steps will enable you to change it to any image you want. There are many guides like this around, but I don't think too much is bad :) You will need the terminal, gimp, and an image of your choice. I use pictures that I take with my camera. Here it goes... 

1. Choose an image / picture of your liking. Maybe that of your kid, your spouse, your favorite place etc...

2. Open the picture with gimp

3. Go to Image -> Scale Image -> Width = 640 & Height = 480 and click on Scale

4. Go to Image-> Mode -> Indexed and choose 'generate optimum palette' with the **maximum number of colors** of 14

5. Go to File -> Save As and change the name of the file from whatever it was to **splash.xpm** and save it to your Desktop (extension have to be xpm). Close Gimp

6. Open a terminal (alt+f3) and type
```

cd Desktop
gzip splash.xpm
sudo cp splash.xpm.gz /boot/grub/

```
As you see, we "converted" (sic) the xpm file to a gz file. 

7. Now let's change your grub menu.lst:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst

```
And add the following line to the beginning of the text file:
```

splashimage=(hd0,5)/boot/grub/splash.xpm.gz

```
Now, be careful, because you may have to change your hd(0,5) part... This tells grub where your boot partition is. You can check what your ubuntu entry tells you. Example: 
This is my ubuntu entry in my menu.lst:
```

title           Ubuntu, kernel 2.6.15-26-686
root            **(hd0,5)**
kernel          **/boot/**vmlinuz-2.6.15-26-686 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

```
so for me, the partition where /boot is is called by grub as **hd(0,5)**... Your line might as well looked like this: 
```
splashimage=**(hd0,1)**/boot/grub/splash.xpm.gz
```

8. Save the file and close it. You can also delete the splash.xpm.gz on your desktop if you'd like to. 

9. Show your friends how your linux is beautiful.

PS. I attached my splash image. Use and/or change it to your liking. The picture is taken at Ada Camping, [Cunda Island]("http://en.wikipedia.org/wiki/Cunda_Island"), near Ayvalik, Turkey. 

Don't forget: the picture has to be 14 colors, in xpm format, and 640 x 480 pixels...

---

