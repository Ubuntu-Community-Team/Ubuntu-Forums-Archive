---
title: "[SOLVED] Getting DVDs onto my hard drive"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Archie69 on 2008-10-02
Hey everyone,

I'm kinda new to Ubuntu, and was searching this forum to see if there were any tips on how to 'back up' DVDs onto my hard drive.  The posts on here didnt seem to help me.  Maybe I'm doing something wrong.  Is anyone able to give me some advice on how to Copy my DVDs onto my computer?

From the previous forums I've read, I tried this:

Synaptic Package Manager -> Settings -> Repositories -> then i unclicked "software restricted by copyright or legal issues (multiverse)'

then I tried to go to terminal to install K9copy, but it said it couldn't find k9copy package

Thats pretty much it.  Any ideas?

I'm running Hardy Heron 8.04
Thanks

---

### Post by bigdee973 on 2008-10-02
i think this should work it will save the dvd as an iso file so that you could burn it later when you want to

[http://wlmtips.com/2008/03/07/saving-a-dvd-iso-in-ubuntu-linux/](http://wlmtips.com/2008/03/07/saving-a-dvd-iso-in-ubuntu-linux/)

---

### Post by Archie69 on 2008-10-02
I would like the opportunity to have it as an iso file as well as watch it on my computer.  So basically be able to rip it so I can watch it on gxine or movie player or vlc as well as burn it.

---

### Post by Archie69 on 2008-10-02
Can anyone help?  This is something I'd like to be able to do.  I travel a bit so I'd like to be able to have movies on my computer without having to download torrents.  I just want to be able to watch a dvd pn my computer by copying it.  And from there to alleviate space I'd like to be able to burn it on a copy DVD afterwards.   

Please help.

---

### Post by halitech on 2008-10-02
K3B will allow you to copy them, just select the option to make the iso only

---

### Post by SuperSonic4 on 2008-10-02
If I'm right in saying you want to rip it to a video file to watch on the pc? Such as mkv?

VLC will rip dvd for you: [http://lifehacker.com/software/dvds/rip-dvds-with-vlc-230349.php](http://lifehacker.com/software/dvds/rip-dvds-with-vlc-230349.php) but you get a massive file (Wallace and Gromit film was 3.1gb)

dvd::rip will do it with more options and will be a smaller file

```
sudo apt-get install dvdrip
``` 

Be sure to select the transcode tab unless you want vob (which vlc can handle)

---

### Post by bigdee973 on 2008-10-02
> **Archie69 said:**
> I would like the opportunity to have it as an iso file as well as watch it on my computer.  So basically be able to rip it so I can watch it on gxine or movie player or vlc as well as burn it.

archie than that link i gave you wuld do the trick it will save it as an iso and as an iso you can open it with VLC (one of the best video players for linux) on it with no problem

---

### Post by bumanie on 2008-10-02
Using dd commands would be a good method, it works, but the .iso will be at the full size of the original dvd as dd used that way gives a byte for byte copy. I am not much into movies, but think this will work. If you want the dvd and resulting .iso shrunk, I think you could shrink it through k9copy and then put the k9 copy output through something like devede which will give a dvd compatible or avi .iso, either of which can be played by vlc. Just a way to save some hard drive space if that's important. > sudo apt-get install k9copy installs k9copy and > sudo apt-get install devede will install devede.

---

### Post by bigdee973 on 2008-10-02
Have you ever wanted to backup a DVD (without losing quality) onto your hard drive in Ubuntu? There are a few programs that will do it, but the simplest way is by using the terminal.

First, open the terminal. Then type:

    sudo dd if=/dev/dvd of=Name_of_DVD.iso

Where I have &#8216;Name_of_DVD&#8217; you should put the title of the movie you&#8217;re trying to rip.

The iso image will be automatically saved in your home folder. You will need around 5GB of space in your home folder as the iso file will be about 4-5GB. [COLOR="Red"]**_Once you have the file, just right click and open it with VLC_**[/COLOR].

---

### Post by haydnc on 2008-10-02
If you're feeling particularly brave and you don't mind using the command line you could also use dvdbackup.

```
sudo apt-get install dvdbackup
```

Brave because last time I checked / used it, it was a command line only bit of software. 
:)

~~~ 

Edit: I hadn't thought of using dd if you're going to use the terminal. It is at least as much of a good choice as dvdbackup. Also be aware that dvds with copy protection may not copy so well. I've run into that a time or two.

---

### Post by Archie69 on 2008-10-02
I know bigdee, but 5 gigs is a rather large file.  Bt if thats the best method I guess thats what I'll do.  I ran that command in terminal, and it was left blinking.  Does that mean its copying?  There is no progress bar or % rate, so due to my impatience i closed it.  Do I just wait?

---

### Post by haydnc on 2008-10-02
If you're using dd then you just have to wait until the copy is finished... it can take a fair while to copy off 5Gb of data.

That is one advantage to using dvdbackup - you can tell it just to 'rip' the movie file.

I'd give you the commands, but I can't remember them. You can get them by typing dvdbackup -help in the terminal anyway.

---

