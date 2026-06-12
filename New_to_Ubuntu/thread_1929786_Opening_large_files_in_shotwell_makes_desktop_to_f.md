---
title: "Opening large files in shotwell makes desktop to freeze !"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by sbnwl on 2012-02-22
This my first post.
I am using ubuntu 11.10 64 bit on asus k53sv netbook.
Whenever I double click some large sized (>16 mb and some upto 450 mb) jpeg and png files, it makes my desktop to freeze completely.

I have tried to produce the bug (if can call it so) several times and here is what I noted just before it goes to freeze:

1. The physical memory usage suddenly increases from 500 mb to 5.2 GB just after opening in shotwell photo manager.
    (I have 8 GB RAM in my machine.)
2. CPU usage shown in 'System Monitor' is about 100% in two of the eight CPUs shown there. (Its an Intel core i7 2670QM, 2.2 GHz)
3. When try to zoom the image with mouse (or whether by hitting ctrl+1 key combination, doesn't matter), the RAM usage suddenly increases to 7.3 GB and then simultaneously see 4 of the CPUs loaded to 100%.
4. It just freezes within a second or two after that. Nothing works on keyboard, nor the mouse. All freezes. Try ctrl+alt+F1, not working. Power consumption just booms from 13 W to 47 W just after trying for zoom. 
5. I left the machine for around 5-15 minutes in the frozen state, waited for it to respond, and each time I had to hard reset finally.
6. The machine goes to cool state (fan noise calms down, heating of machine lowers to usual level) after 3-4 minutes of commence of freezing.
7. I did dmesg on reboot to find a thing:
```
[   31.281228] init: plymouth-stop pre-start process (1848) terminated with status 1

```The same files open so smoothly in EyeOfGnome (eog). Even eog takes much less of cpu (loads only 1 core to 100% for a short time) and less RAM (3.5GB) while it is open and remains constant at 3.5GB while zooming.
What can be wrong, I have produced the same bug in both "gnome 3" and "unity" sessions in the same machine (USUALLY I USE GNOME 3). Unity is used rarely. I have home folder encrypted.

---

### Post by eric-yorba on 2012-02-22
When you say you're opening the files in Shotwell, are you using Shotwell in library mode, or are you opening them in photo viewer mode?

Also, what version of Shotwell are you running?

---

### Post by eric-yorba on 2012-02-22
FYI, I opened a ticket on this here:
[http://redmine.yorba.org/issues/4777](http://redmine.yorba.org/issues/4777)

---

### Post by sbnwl on 2012-02-23
Sorry, I could not reply earlier.
It is here what you asked:
```
mu@mu-lap750:~$ shotwell --version
Shotwell 0.11.6
mu@mu-lap750:~$
```I have tried opening the files by right clicking => open with => shotwell photo viewer.
I downloaded the stuff from [here]("http://eoimages.gsfc.nasa.gov/images/imagerecords/73000/73938/world.200401.3x21600x21600.panels.png.tar")
And then extracted the *.tar file, opened the files one by one in shotwell.
It froze each time for all of the eight images. eog did the job so fine!
But eog was not able to give me that clarity in detection of ground features  that I had expected from the high resolution images.

---

### Post by yorba-jim on 2012-02-23
How many files are in the directory with the photo you were trying to view?  Was it only the photos in the tarball you linked to, or were there more?

I ask because there's two likely culprits here: the size of each photo file, and the number of files in the directory.  It could be either or both.

-- Jim

---

### Post by sbnwl on 2012-02-23
I have extracted the tarball, then I see a new folder created, which contains eight files only. I enter the folder in nautilus, and open one of the files in shotwell by right clicking it. Only after that problem starts.

---

### Post by sbnwl on 2012-02-25
I know for most of us, this issue is not so problematic, for such filesizes are too uncommon. Is there any software (image viewer) , be it paid or Free for linux platform, for precise large file viewing. I don't mean to compare to any other platform.

---

### Post by sbnwl on 2012-02-26
```
FYI, I opened a ticket on this here:
[http://redmine.yorba.org/issues/4777](http://redmine.yorba.org/issues/4777)
```

Thank you eric-yorba. I've seen the ticket. Perhaps it will be fixed in next release.

---

