---
title: "adding wallpapers to system 12.10"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by cabz on 2012-11-24
I have just installed 12.10 on my dell mini so far it is working very well, i have done all the tweaks i know how to do and now i'd like to try some more tweaking. since I am still new to ubuntu i wanted to ask before jumping in.
I want to add some more wallpapers to my pc but what i would like to know is how can i put my new wallpapers in the same folder as the current system ones ? i would like them to change like the current system ones do. also will ,jpgs work? and is there a size limit on the pics i can use?.
sorry if this seems like a newb question , but i am a newb at this :)

---

### Post by LuisGMarine on 2012-11-24
The default location for Ubuntu 12.10 wallpapers is currently 

```
/usr/share/backgrounds
```

As far as I know the only way I have been able to have the wallpapers change based on a custom folder is using this application called wallch.

You can install it through the Ubuntu Software Center by searching for "Wallch", or alternatively you can do it through the command line:

```
sudo apt-get install wallch
```

And yes .jpeg format should work, and there is no size limit.

---

### Post by cabz on 2012-11-24
> **LuisGMarine said:**
> The default location for Ubuntu 12.10 wallpapers is currently 

```
/usr/share/backgrounds
```As far as I know the only way I have been able to have the wallpapers change based on a custom folder is using this application called wallch.

You can install it through the Ubuntu Software Center by searching for "Wallch", or alternatively you can do it through the command line:

```
sudo apt-get install wallch
```And yes .jpeg format should work, and there is no size limit.
thanks for the reply, I was hopeing that by putting the new wallpapers in the same folder so they show up in the standard ubuntu wallpaper folder list would allow them to show up and change with  the system setting of "changes througout the day" .if not at least they will all show up in the same folder .

---

### Post by cabz on 2012-12-20
Well I got the pics I wanted into the backgrounds folder and they still dont show up . even after a reboot. any other ideas?

---

### Post by rnerwein on 2012-12-20
> **cabz said:**
> Well I got the pics I wanted into the backgrounds folder and they still dont show up . even after a reboot. any other ideas?
hi
i am running 12.04 LTS
just right klick on your screen and select "change the background" (hope you anderstand what i'll will tell you - my box is in my mothertoung (german).
the window with the available backgrounds will apear. now select the "+". this will open nautilus i think and you parse the filesystem for a background wich will fit to your behavior ( i think it is in your home). select it and just follow the instruction. the background will change imediatly if you select a new one.
cheers

---

### Post by zikalify on 2012-12-20
To add wallpapers to usr/share/wallpapers open up terminal then ```
sudo nautilus
``` with the window that just opened navigate to wallpapers folder and drop the thing what you want in there.

---

### Post by zombifier25 on 2012-12-20
> **zikalify said:**
> To add wallpapers to usr/share/wallpapers open up terminal then ```
sudo nautilus
``` with the window that just opened navigate to wallpapers folder and drop the thing what you want in there.

The correct code is 
```
gksu nautilus
```
or any graphical applications you want to launch as root. You should not use "sudo" to launch graphical applications.

---

### Post by grahammechanical on 2012-12-20
There are a couple of scripts that need to be edited if you want another image to be part of the selection of images that change the desktop image over time.

I worked out how to do this in 12.04 or was it 11.10? I was even able to have more than one background slideshow to select from. But things have changed. Stuff is put into different folders. I need to review my research.

I am back. This is for 12.10.

Go to computer /usr/share/backgrounds

That is where you will see all the background (wallpaper) images. Put the image you want into there.

You will also see a folder called contest. In that folder is a script called quantal.xml. It can be opened in a text editor but you will need administrator privileges. So

```
gksudo gedit /usr/share/backgrounds/contest/quantal.xml
```

will open the file with administrator access. Examine the style of the file and add a reference to your image following the same pattern. Example.

>   <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/A_Little_Quetzal_by_vgerasimov.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/A_Little_Quetzal_by_vgerasimov.jpg</from>
    <to>/usr/share/backgrounds/Vanishing_by_James_Wilson.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/MyNewImage.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/MyNewImage.jpg</from>
    <to>/usr/share/backgrounds/Below_Clouds_by_kobinho.jpg</to>
  </transition>

Assuming that your image is called MyNewIMage.jpg. Save the file and see if that works. If duplicate images appear it is because Gedit has created a backup of quantal.xml called quantal.xml~. That tilde character ( ~ ) makes it also a hidden file so the normal Nautilus will not see it. But that backup needs to be deleted.

I experimented with this stuff months ago but I have not tried it again. So, this suggestion should be viewed as experimental.

I am back yet again. If you only want to add another image as a static background image then go to /usr/share/gnome-background-properties and edit the script called quantal-wallpapers.xml. It has a style like this:

>   <wallpaper>
    <name>Below Clouds</name>
    <filename>/usr/share/backgrounds/Below_Clouds_by_kobinho.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>Cairn</name>
    <filename>/usr/share/backgrounds/MyNewImage.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

Again assuming the the extra background image is called MyNewImage.jpg.

Regards.

---

### Post by cabz on 2012-12-20
I had to create the wallpaper folder and put the pic in itand it still did not work. but what I am trying to do is put the pic in the usr/share/backgrounds folder with all the other standard ubuntu wallpapers and have my pics show up in the list with all the other wallpapers so when i chose the "changes throughout the day " option my wallpaper will be one of the ones it changes to. but when I put my pics in the folder usr/share/backgrounds it doesnt show up in the list even though it is in the folder and it is the same type of pic as the rest.

---

### Post by cabz on 2012-12-20
> **grahammechanical said:**
> There are a couple of scripts that need to be edited if you want another image to be part of the selection of images that change the desktop image over time.

I worked out how to do this in 12.04 or was it 11.10? I was even able to have more than one background slideshow to select from. But things have changed. Stuff is put into different folders. I need to review my research.

Regards.cool this is what i need , please let me know when you remember what it is you did. thanks

---

### Post by grahammechanical on 2012-12-20
> **cabz said:**
> cool this is what i need , please let me know when you remember what it is you did. thanks

I have added to my original post. I like to test suggestions before I offer them. But I have not been able to do that this time. Have fun. Let us know if it works and how to fix any issues you come up with.

To create our own slide shows we need to create a folder in /usr/share/backgrounds and in that new folder we put a modified xml script following the pattern of quantal.xml. We can put our images in /usr/share/backgrounds or, for neatness in /usr/share/backgrounds/newslidshowfolder. We need to make sure that the links are pointing to the right place. Has the right path.

either

> <from>/usr/share/backgrounds/NewImage.jpg</from>
<to>/usr/share/backgrounds/NextNewImage.jpg</to>

or

> <from>/usr/share/backgrounds/newslideshowfolder/NewImage.jpg</from>
<to>/usr/share/backgrounds/newslideshowfolder/NextNewImage.jpg</to>

depending upon the exact place that we put our collection of new slideshow images.

Regards.

---

### Post by Frogs Hair on 2012-12-20
If adding items to usr/share/backgrounds see this thread.  [http://ubuntuforums.org/showthread.php?t=2033019](http://ubuntuforums.org/showthread.php?t=2033019)

---

