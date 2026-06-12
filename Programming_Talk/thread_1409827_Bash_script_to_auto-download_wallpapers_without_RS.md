---
title: "Bash script to auto-download wallpapers without RSS"
date: 2010-02-18
forum: Programming Talk
---

### Post by blacksunseven on 2010-02-18
So abduzeedo.com posts a sick new wallpaper every week and I thought it'd be neat to have a script that goes and gets it and sets it as the current wallpaper for a week's time. I don't really know what the best way to do this would be. Here's some info that might help out:
[LIST]
[*][http://abduzeedo.com/tags/wallpaper](http://abduzeedo.com/tags/wallpaper) <- main wallpaper page
[*][http://www.abductit.com/files/wallpapers/wpw87/wp_1440.jpg](http://www.abductit.com/files/wallpapers/wpw87/wp_1440.jpg) <- standardized URL syntax abduzeedo follows. wpw## (and probably soon ###) increases by one every week beginning on Sunday. wp_$$$$ represents the resolution width (1440x900 in this case).
[/LIST]

Thanks for any code!

---

### Post by geirha on 2010-02-18
I liked those images, and the idea, so I made a script to do it. 

I noticed that [http://www.abductit.com/files/wallpapers](http://www.abductit.com/files/wallpapers) gave a standard directory listing. So the script reads that listing, sorted by last modified, and grabs the last one, which will most likely be the latest weekly. Then it downloads the image of wanted size to /usr/local/share/backgrounds/Weekly abduzeedo.jpg.

Obviously, you'll have to set /usr/local/share/backgrounds/Weekly abduzeedo.jpg as your wallpaper. When a new one gets downloaded, it should be detected automatically.

```

#!/bin/bash

size=1280R
dest="/usr/local/share/backgrounds/Weekly abduzeedo.jpg"

mkdir -p "${dest%/*}" || exit

read -r _ baseurl < <(lynx -listonly -dump 'http://www.abductit.com/files/wallpapers/?C=M;O=A' | tail -1) &&
wget -q "$baseurl/wp_$size.jpg" -O "$dest"

```

Copy it to /etc/cron.weekly/weeklywall (or some other name you prefer, but do NOT add an extension) and make it executable. It will then be run by anacron once a week, and during boot (if it was more than a week since last it was run).

Oh and the script uses lynx to parse the html, but lynx is not installed by default, so you'll need to install it [apt://lynx-cur](apt://lynx-cur).

---

### Post by diesch on 2010-02-18
lynx has a greate keystroke recording feature that comes handy with thinks like that:

Save the following as e.g.* abduzeedo.lynx* 
```
set INFOSECSr=:0
set MESSAGESECS=0
set ALERTSECS=3
set REPLAYSECS=0

key /
key W
key a
key l
key l
key p
key a
key p
key e
key r
key <space>
key o
key f
key <space>
key t
key h
key e
key <space>
key w
key e
key e
key k
key ^J
key ^J
key Down Arrow
key /
key R
key e
key s
key o
key l
key u
key t
key i
key o
key n
key s
key ^J
key Down Arrow
key d
key ^J
key ^U
key ~
key /
key w
key a
key l
key l
key p
key a
key p
key e
key r
key .
key j
key p
key g
key ^J
key q
key ^J

```

Then
 ```

lynx -cmd_script abduzeedo.lynx   http://abduzeedo.com/tags/wallpaper

```
saves the current *Wallpaper of the Week* in the highest resolution available as *~/wallpaper.jpg*

---

### Post by itismike on 2013-02-11
> **geirha said:**
> ...
```
read -r _ baseurl < <(lynx -listonly -dump 'http://www.abductit.com/files/wallpapers/?C=M;O=A' | tail -1) &&
wget -q "$baseurl/wp_$size.jpg" -O "$dest"

```...

I understand this is attempting to put the results of the lynx and tail commands into the variable baseurl, but I'm not experienced with the context of read -r _ 
And how does the < < separated by whitespace redirect?

---

### Post by sisco311 on 2013-02-11
> **itismike said:**
> I understand this is attempting to put the results of the lynx and tail commands into the variable baseurl, but I'm not experienced with the context of read -r _ 
And how does the < < separated by whitespace redirect?

_ is a variable name, just like baseurl. Some people use it as a "junk variable" to ignore fields (See BashFAQ 001 for an example).

The first < is a redirection and

<(list) is a process substitution: [http://mywiki.wooledge.org/ProcessSubstitution](http://mywiki.wooledge.org/ProcessSubstitution)

---

### Post by itismike on 2013-02-12
Thanks for the clarification, sisco311. That explains why I was getting null values after adding -nonumbers to the lynx command. Here's what I'm using to set my background to the Experimental Aircraft Association's monthly wallpaper:```
#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
size=1680
dest="/usr/local/share/backgrounds/wallpaperEAA.jpg"
read -r baseurl < <(lynx -nonumbers -listonly -dump 'http://www.eaa.org/wallpaper/' | grep -i `date +%B%g` | grep $size) &&
wget -q "$baseurl" -O "$dest"
```Each wallpaper is uniquely-named, but follows a **monthyr** format: [http://www.eaa.org/wallpaper/images/](http://www.eaa.org/wallpaper/images/)**february13**/skiplane_wallpaper1440w.jpg so I'm parsing it with grep to find the correct month and resolution for my screen.

Save it without an extension to: /etc/cron.monthly to launch monthly.

I dual-boot, so here's the same solution for Mac OS X:
[http://stackoverflow.com/questions/431205/how-can-i-programatically-change-the-background-in-mac-os-x/14861053#14861053](http://stackoverflow.com/questions/431205/how-can-i-programatically-change-the-background-in-mac-os-x/14861053#14861053)

---

