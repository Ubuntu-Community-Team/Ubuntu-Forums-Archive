---
title: "[SOLVED] nautilus script help please."
date: 2008-10-02
forum: New to Ubuntu
---

### Post by madmak on 2008-10-02
hia guys i was wondering if anyone could help me change a small bash script i put together for creating dvds into a nautilus script.
At the moment iv got my bash script saved into my /home folder and created a launcher to start it then i just type the name and full path of the video i want to make the dvd iso of and my script creates the iso and cleans up the junk files left behind but i wanted to make the script so as i can just right click on the video file and run the script to convert it. This is how my bash script looks at the moment,

```
#!/bin/bash
echo " "
echo " type the videos full name and path"
echo " "

read i;
mencoder $i -ovc xvid -xvidencopts pass=1 -oac mp3lame -lameopts vbr=3 -o /dev/null;
mencoder $i -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o output101.avi;
ffmpeg -i output101.avi -target pal-dvd final101.mpg;
dvdauthor -o DVD101/ -t final101.mpg;
dvdauthor -o DVD101/ -T;
mkisofs -dvd-video -v -o $i.iso DVD101;
rm -r /home/*/DVD101;
rm /home/*/final101.mpg;
rm /home/*/output101.avi;
rm /home/*/divx2pass.log;
xmessage "Dvd Complete" -nearmouse;
exit;;

esac
esac 
```

my main problem is how to make the script understand that its the file iv highlighted that i want to convert as im new to writing scrips and decieded to give this a shot so it saves me time when im converting my videos.
Can anyone show me how to do this or point me to any good beginners tutorials thanks. :D

---

### Post by aeiah on 2008-10-02
im not sure as i use a python script to do what you do, but i found that its nice to use nautilus-actions instead of a nautilus script. its easier to set up too and you can set it to only appear in the right-click menu when selecting a video file (and you could make another for when you're selecting two video files, so it joins them up first or something for 2 part .avi movies)

---

### Post by madmak on 2008-10-02
Thanks mate ill have a look at that.
I managed to get my script to work now so im happy for the moment lol
heres the working script if anyone wants to use it for converting.
If your not converting to pal format youll have to change the 

```
 ffmpeg -i output101.avi -target pal-dvd final101.mpg; 
```

part of the script to

```
 ffmpeg -i output101.avi -target pal-dvd -aspect 16:9 final101.mpg; 
```

Heres the working script.

```
 #!/bin/bash
for i 
do

 mencoder $i -ovc xvid -xvidencopts pass=1 -oac mp3lame -lameopts vbr=3 -o /dev/null;
 mencoder $i -ovc xvid -xvidencopts pass=2:bitrate=1000 -oac mp3lame -lameopts vbr=3 -o output101.avi;
 ffmpeg -i output101.avi -target pal-dvd final101.mpg;
 dvdauthor -o DVD101/ -t final101.mpg;
 dvdauthor -o DVD101/ -T;
 mkisofs -dvd-video -v -o $i.iso DVD101;
 rm -r DVD101;
 rm final101.mpg;
 rm output101.avi;
 rm divx2pass.log;
 xmessage "Dvd Complete" -nearmouse;
 
done

esac
esac 
```

---

