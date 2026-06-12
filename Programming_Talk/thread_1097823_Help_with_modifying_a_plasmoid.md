---
title: "Help with modifying a plasmoid"
date: 2009-03-16
forum: Programming Talk
---

### Post by skeebo on 2009-03-16
I am currently trying to modify the oxygen system monitor [http://kde-look.org/content/show.php/Oxygen+System+Monitor?content=86664 ]("http://kde-look.org/content/show.php/Oxygen+System+Monitor?content=86664") 

My goal is to have the HDD monitor show me the disk usage of my external drive. Here's what I've got so far.

```
# [ HDD " My Book " ]
    text x=3 y=52 value="My Book" fontsize=11 font="Blue Highway"
    text x=190 y=52 sensor=disk format="Used: %up% (%ug GB / %tg GB)" mountpoint="/media/My\ Book/" fontsize=11 #font="Blue Highway" align=right
    image x=3  y=65 path="images/bar_back.png"
    bar x=3  y=65 path="images/bar_front.png" sensor=disk mountpoint="/media/My\ Book/" interval=60000
```The problem is that my mountpoint (to me) seems correct, but for some reason it doesn't appear to see my external drive "/media/My\ Book" It simply shows 0% usage with 0 GB / 0GB. What is it I may be doing wrong, or what could I try instead? Any help or links to point me in the right direction would be fantastic. 

I'm not sure whether it matters or not, but my external drive is shown in my mtab file as follows:
```
/dev/sdf1 /media/My\040Book vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed 0 0
```Also if possible, rather than a straight forward "type this here instead" answer, more of a "this works because ..." would be nice. I like to know exactly what I'm doing and why I'm doing it. I'm sure most of you can agree with me there.

Anyways, thanks for taking the time to read this, I made sure to take the time to read the FAQS myself. If anything I'm saying isn't clear just ask, I'll try and explain my situation a little better for you.

---

### Post by skeebo on 2009-03-17
I never realized how dumb my question was, but i found my solution. I thought I would post it in case somebody as inexperienced as me needs to know.

First off, if you take a look in your mtab file located in /etc/mtab you will see the device you want your plasmoid to read. As i posted above mine is as follows:

```
/dev/sdf1 /media/My\040Book vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed 0 0
```As you can see it's at "/dev/sdf1" and mounted to "/media/My\040Book" or "/media/My\ Book/".. Your's may say something different, it doesn't matter. I think my plasmoid couldn't read the drive possibly because of the spacing in "My Book?" Correct me if I'm wrong.

So all I did was mounted /dev/sdf1 to the /mnt directory as follows:
```
sudo mkdir /mnt/whatever_you_want    ## creates a directory to mount your drive
sudo mount /dev/sdf1 /mnt/whatever_you_want    ## mounts your drive to your newly made directory
```Now that you have your drive mounted to your directory, in my case "/mnt/extern". Open up your .theme file and go to the line where your telling your plasmoid to read the external drive. In my case it looks like this:

```
# [ HDD " My Book " ]
    text x=3 y=52 value="My Book" fontsize=11 font="Blue Highway"
    text x=190 y=52 sensor=disk format="Used: %up% (%ug GB / %tg GB)" [COLOR=Red]mountpoint="/mnt/extern"[/COLOR] fontsize=11 #font="Blue Highway" align=right
    image x=3  y=65 path="images/bar_back.png"
    bar x=3  y=65 path="images/bar_front.png" sensor=disk [COLOR=Red]mountpoint="/mnt/extern"[/COLOR] interval=60000
```Just a little bit more googleing is all I needed, I apologize for not looking further into this before posting, at least my mistake may help someone else.

By the way you guys (the linux community) are doing a huge service to the world in general. I'm not sure if you all realize it, but besides opening people up to the vast world of open source software you are directly and indirectly passing on knowledge to thousands, if not millions of newcomers.

I may not know too much as of yet, but everything I'm learning comes from this community, and I know I'm not the only one. I simply one of the MANY to come. You guys are shaping the future of this world on a larger scale than some may realize. This is just a short thank you from "the newbs" to "the community" as I'm sure I can speak for all of us. 

I'd tell you all to keep up the good work, but obviously you all will anyways. 

On a side note, can anyone explain to me why I couldn't use /media/My\ Book/ as a mountpoint in my plasmoid, and rather I had to mount /dev/sdf1 to /mnt/extern in order for this to work? I'm kind of curious, and though I fixed my problem I really am clueless as to why it worked. My guess was the spacing in My Book, and maybe something with superkaramba not knowing what I was telling it to do?

---

### Post by slavik on 2009-03-17
did you try "/media/My Book" by any chance? the space escaping is usually needed for the shell.

---

