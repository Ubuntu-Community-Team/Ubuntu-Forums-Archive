---
title: "Howto:  Video Thumbnails for .BIN &amp; .RM Files."
date: 2006-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by hikaricore on 2006-10-15
Ok before I begin this is kind of a nasty hack, and by that I mean I associate thumbnailing for the application/octet-stream mimetype to pull this off.  Meaning this will use mplayer to general *attempt* to make thumbnails from any file with that mimetype.  Which can have interesting side effects to say the least...  Examples below.

Unfinished rar files for a movie from a torrent:
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/more/zomg.png[/IMG]

Random SMC snes roms:
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/more/zomg2.png[/IMG]


If you're ok with this and don't care, go ahead and read on. (or just remove this section and only install thumbnailing for RM videos)

First I have to thank minio for his HowTo on OpenOffice thumbnails [http://ubuntuforums.org/showthread.php?t=76566]("http://ubuntuforums.org/showthread.php?t=76566"), which showed me exactly what I needed to know to get this started.

And [me2030581]("http://me2030581.googlepages.com/") for his mplayer thumbnailing script.  Since gnome uses totem i believe (or xine depending on your setup) to create video thumbnails, thumbnailing bin files (and possibly RM files but i'm not sure on this one) isn't supported since it can't play these file types.

**Dependencies**
> mplayer
mogrify
gconf-editor 


make sure you have these installed (you probably should, but just incase) or this will fail worse than a flying sheep.

Here goes:

```

cd ~
wget http://me2030581.googlepages.com/mplayer-video-thumb-0.1beta.tar.bz2
tar -xvjf mplayer-video-thumb-0.1beta.tar.bz2
cd mplayer-video-thumb-0.1beta/
chmod 755 mplayer-video-thum.sh
sudo mv mplayer-video-thum.sh /usr/bin
sudo mkdir /usr/share/apps/videothumbnail/
sudo mv *.png /usr/share/apps/videothumbnail/

```

now that the mplayer thumbnailer script is installed we start with the gconf-editor side of things :)

```

sudo gedit /usr/share/gconf/schemas/bin-rm_thumb.schemas

```

once gedit is opened you will need to paste the following:

```

<gconfschemafile>
    <schemalist>

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@octet-stream/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@octet-stream/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@octet-stream/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@octet-stream/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/mplayer-video-thum.sh -s %s %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.rn-realmedia/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.rn-realmedia/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.rn-realmedia/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.rn-realmedia/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/mplayer-video-thum.sh -s %s %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>

    </schemalist>
</gconfschemafile>

```

I havn't as you can see changed the owner string from the template I made out of minio's information from ooo2-thumb, but I don't believe this causes any horrible conflict.

Save the file and get your happy butt back to that terminal.

```

gconftool-2 --install-schema-file /usr/share/gconf/schemas/bin-rm_thumb.schemas
killall -9 nautilus

```

With that done you should be able after nautilus restarts, goto the folder(s) where you keep you BIN vcds and or RM video files and see them being thumbnailed.  :)  You may need to hit F5 to refresh the window for the change to take effect.  In a couple cases I needed to rename a file to the process started, but I'm guessing that has something to do with the nautilus caches it's thumbnails.

Hopefully this works for anyone interested.  If there are any problems, please let me know so I can update this howto.

        --Aaron

[SIZE="1"]all references to canada, cows, billy corgan, polar bears, ect.; living or dead are purely coincidential. also random fits of confusion, anger, loss of purpose, and/or canada; may be blamed on you...in which case you will be killed in the slowest possible way while watching the sexual organs of any of your close friends be unwillingly fed to large satanic carebears. all comments dealing with the non-existance of god are to be taken as fact unless otherwise proven by written notice/birth certificate. you may be castrated in the state of neveda for molesting small children. throwing lit candles at large bulls may be hazardous to your health, unless of course you are dead....then the proceeding statement is null and void.[/SIZE]

---

### Post by hikaricore on 2006-10-16
**update 10/16**  just fixed a few serious typos lol  **update**

**update 10/17**  Note this can also be used to thumbnail almost any file type mplayer can play, where the gnome thumbnailer drops dead on some files this can shine.  If you add the appropriate mime types to the schemas file you can thumbnail almost anything.

---

### Post by chocbar31 on 2006-10-20
> **hikaricore said:**
> **update 10/16**  just fixed a few serious typos lol  **update**

**update 10/17**  Note this can also be used to thumbnail almost any file type mplayer can play, where the gnome thumbnailer drops dead on some files this can shine.  If you add the appropriate mime types to the schemas file you can thumbnail almost anything.


Excellent post! Thanks...

---

### Post by Sukarn on 2006-10-21
Can you please tell me how to get thumbnails of rmvb files using this method? I am kind of confused about that.
The way I have been doing it so far is to open the directory containing the files in Konqueror. Konqueror generates thumbnails for it. Then I have the thumbnails in nautilus as well.

---

### Post by hikaricore on 2006-10-27
> **chocbar31 said:**
> Excellent post! Thanks...

You're quite welcome :)

> **Sukarn said:**
> Can you please tell me how to get thumbnails of rmvb files using this method? I am kind of confused about that.
The way I have been doing it so far is to open the directory containing the files in Konqueror. Konqueror generates thumbnails for it. Then I have the thumbnails in nautilus as well.

I would need to know the mimetype so I could write a modified .schemas file, but if you can get me that info I wouldn't mind trying.  :)

---

### Post by Efros on 2006-12-10
Just tried this and I get RMVB thumbnails just as is!

---

### Post by zigzed on 2007-02-28
Thanks for your information...I found a bug which did not support chinese path/file very well. and i modify the scripts as follow:

```

#!/bin/bash 
file="$3"
file=`uri-unescape.pl $file`
cd /tmp
LENGTH=$(mplayer -nocache  -identify -vo null -ao null -frames 0 "$file"  | awk -F= '/ID_LENGTH/ {print $2}'| awk -F. '{print $1}')
START=$((($LENGTH*15)/100))
END=$((($LENGTH*70)/100))
start=$(($START+($RANDOM%($END-$START+1))))
/usr/bin/mplayer -nocache -vf scale -vo jpeg -ao null -ss "$start" -frames 4 "$file"
rm -f 00000001.jpg 00000002.jpg 00000003.jpg
/usr/bin/mogrify -resize "$2" -draw 'image Over 0,0 10,100  "/usr/share/apps/videothumbnail/filmholes-big-left.png"' -draw 'image Over 118,0 10,100 "/usr/share/apps/videothumbnail/filmholes-big-right.png"' 00000004.jpg  
cd -
mv  /tmp/00000004.jpg "$4"


```

please note line 3 (I modify this line only), i use URI::Escape module of perl to unescape the filename. and following is script uri-unescape.pl

```

#!/usr/bin/perl
use URI::Escape;
$text = $ARGV[0];
print uri_unescape($text);

```

I know little about perl, and didn't how to combine the uri-unescape.pl with the mplayer-video-thum.sh..........I hope someone can help me out.

p.s. if you want re-generate the thumbnails, you should delete the files under ~/.thumbnails/fail/gnome-thumbnail-factory

---

### Post by fxtrem on 2008-07-27
I've made a little patch to support some accented characters (Most of them used by PT_BR language)

Type this on the terminal:
```
sudo gedit /usr/bin/mplayer-video-thum.sh
```

Then change this line

```
(...)
file="$3"
[COLOR="Red"]file=$(echo "$file" | sed -e 's/%20/ /g' | sed -e 's/%26/\&/g' | sed -e 's/%5B/\[/g' | sed -e 's/%5D/\]/g' | sed -e 's/%40/\@/g' )[/COLOR]
cd /tmp
(...)
```

With this:
```
file=$(echo "$file" | sed -e 's/%20/ /g' | sed -e 's/%26/\&/g' | sed -e 's/%5B/\[/g' | sed -e 's/%5D/\]/g' | sed -e 's/%40/\@/g' | sed -e 's/%C2%AA/ª/g' | sed -e 's/%C3%BA/º/g' | sed -e 's/%C2%B0/°/g' | sed -e 's/%C3%A1/á/g' |sed -e 's/%C3%A9/é/g' | sed -e 's/%C3%AD/í/g' | sed -e 's/%C3%B3/ó/g' | sed -e 's/%C3%BA/ú/g' | sed -e 's/%C3%81/Á/g' | sed -e 's/%C3%89/É/g' | sed -e 's/%C3%8D/Í/g' | sed -e 's/%C3%93/Ó/g' | sed -e 's/%C3%9A/Ú/g' | sed -e 's/%C3%A3/ã/g' | sed -e 's/%C3%83/Ã/g' | sed -e 's/%3F/?/g' | sed -e 's/%C3%A2/â/g' | sed -e 's/%C3%AA/ê/g' | sed -e 's/%C3%B4/ô/g' | sed -e 's/%C3%82/Â/g' | sed -e 's/%C3%8A/Ê/g' | sed -e 's/%C3%94/Ô/g')
```

---

### Post by zyfnab on 2008-10-11
Someone can post how to apply this to .rmvb movies? I have tried it but it has been a failure :(

I'm using intrepid ibex.

---

### Post by Efros on 2008-11-04
I haven't tried this on an intrepid installation yet but I intend to today, I will let you know how I get on with rmvb.

---

### Post by hmartoliveira on 2008-11-17
> **zyfnab said:**
> Someone can post how to apply this to .rmvb movies? I have tried it but it has been a failure :(

I'm using intrepid ibex.

Hi there!

Great tip! Thank you!

One note for Intrepid users:

Delete the directory *.thumbnails* in your *home* folder and the thumbnails will work.

(sorry about my English)

---

