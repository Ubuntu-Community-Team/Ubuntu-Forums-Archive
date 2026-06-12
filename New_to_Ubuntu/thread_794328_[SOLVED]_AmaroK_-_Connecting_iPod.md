---
title: "[SOLVED] AmaroK - Connecting iPod?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-14
I need some help with AmaroK. Can someone help me with connecting my iPod with AmaroK? It says I need to mount it with AmaroK or something? Thanks for any help.

---

### Post by ace007 on 2008-05-14
So, your problem is that you iPod isn't mounted?  If it is not automounting then the problem is more than likely it was not properly ejected when using it previously.  You can try using the -force command with mount to override this.

For instance
```

sudo mount -t vfat /dev/sdc1 /media/iPod -o force

```

Assuming the ipod is device sdc1 and you want to mount it at /media/iPod

---

### Post by Bigtime_Scrub on 2008-05-14
Id like to know the answer to this too. I havent gotten anything to work with my IPod.

---

### Post by Goemon4 on 2008-05-14
Don't you need to just manually set it up in the amaroK preferences? If it cant detect it, it probably cant detect the mount point, so thats all you have to do. 

If you dont know the mount point, right click the ipod on your desktop, and go to properties, and it should be in there. (it's usually /media/*IPOD NAME* or something.)

---

### Post by shifty_powers on 2008-05-14
> **Bigtime_Scrub said:**
> Id like to know the answer to this too. I havent gotten anything to work with my IPod.

i'm assuming you've used gtkpod?

and depending on which ipod you've got, check out [http://www.rockbox.org/](http://www.rockbox.org/)

> What is Rockbox? Why should I use it?

Rockbox is an open source firmware replacement for a growing number of digital audio players. It has been in development since 2001 and receives new features, tweaks and fixes every day to provide you with the best possible music listening experience. Rockbox aims to be considerably more functional and efficient than your device's stock firmware while remaining easy to use and customizable. We believe that you should never need to go through a series of menus for an action you perform frequently. We also believe that you should be able to configure almost anything about Rockbox you could want, pertaining to functionality. It is written by users, for users.

Another top priority of Rockbox is audio playback quality. Rockbox, for most models, includes a wider range of sound settings than that device's original firmware. A lot of work has been put into making Rockbox sound the best it can, and improvements are constantly being made. All models have access to a large number of plugins, including many games, applications, and graphical demos.

You can load different configurations quickly for different purposes (e.g. a large font for in your car, different sound settings for at home). You can even customize your While Playing screen to display only and exactly what you want to see when your music is playing. In addition, Rockbox features a wide range of languages, and all supported models also have the ability to talk to you - menus can be voiced and filenames spelled out or spoken.

---

### Post by Bigtime_Scrub on 2008-05-14
> **Goemon4 said:**
> Don't you need to just manually set it up in the amaroK preferences? If it cant detect it, it probably cant detect the mount point, so thats all you have to do. 

If you dont know the mount point, right click the ipod on your desktop, and go to properties, and it should be in there. (it's usually /media/*IPOD NAME* or something.)

Well its supposed to just show up as an Icon on your desktop. Then you open the media transfer program of your choice (gtkpod, amaroK, etc.) You click <add files>, save, and then click <load IPod or synchronize> and it should work, but it never does.

---

### Post by Elementality on 2008-05-14
Do you have an iPod touch?

If so, the process is a fairly different, and maybe even more complex.

Check out: [https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone").

It's a great HOWTO on setting up your iPod touch with Ubuntu and subsequently configuring amaroK to mount and unmount automatically.

Interestingly enough when I tried this my version of "ipod-convenience" didn't work (the version may be different now). I had to rewrite some source code in its installation directory to correct where my actual iPod touch music library was contained in the iPod filesystem, so that the app could correctly mount the music directory.

I used gFTP to SSH into my iPod and find the correct directory.

(I'd list it here, but I'm on a Windows box, and don't have the path memorized :P)

---

### Post by UnknownFear on 2008-05-14
> **Goemon4 said:**
> Don't you need to just manually set it up in the amaroK preferences? If it cant detect it, it probably cant detect the mount point, so thats all you have to do. 

If you dont know the mount point, right click the ipod on your desktop, and go to properties, and it should be in there. (it's usually /media/*IPOD NAME* or something.)

That worked!! Thanks a lot. Now, something weird happens when I go to disconnect my iPod. I'll hit the Disconnect button.. and out pops my CD tray :S and my iPod doesn't even disconnect.. very weird. This is what the post-disconnect command reads:

```
kdeeject -q %d
```

Any suggestions?

---

