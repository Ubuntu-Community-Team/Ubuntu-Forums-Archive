---
title: "bash script"
date: 2007-11-10
forum: Programming Talk
---

### Post by prophet73 on 2007-11-10
Hi does anyone know how to get the zenity progress bar to work with mencoder.I'm trying to write a video converter script but haven't got the knowledge to get the progress bar to work as i'm still a newb.

---

### Post by prophet73 on 2007-11-11
I used this line of code after mencoder but the progress bar stops half way through.
2>&1 |  awk -vRS='\r' '$1 ~ /Pos/ {gsub(/f/,"  ");gsub(/%)/," ");gsub(/ \(/," ");if ($4>0)print $4; fflush();}'| zenity --progress --percentage=0 --auto-close --auto-kill --title="Converting" --text="Running..."

---

### Post by prophet73 on 2007-11-13
I've worked it out it was when the output from mencoder was getting to 1000s when it was going wrong,here's the finished script.
Before you tell me its rubbish this is my first script and i'm only learning.
```
  #!/bin/bash


#Choose video file to use
 zenity --info \
          --text="video converter."
                

FILE=`zenity --file-selection --title="Select a File"`

        case $? in
                 0)
                        echo "\"$FILE\" selected.";;
                 1)
                        echo "No file selected.";;
                -1)
                        echo "No file selected.";;
        esac




#Check video type
vid()

{
file -i "$FILE" | echo $1 | grep -i '\.avi$'
}

if ( vid "$FILE")
        then
	avi="1"
fi	

if [ $avi -eq "1" ]; then
	zenity --info \
          --text="You have selected the correct video type."
	else
	zenity --error --title="Error" --text="You have not selected a correct type of file." 
	exit 
fi




#Choose a destination for your project
dir=`zenity --file-selection --directory --title="Select a project destination"`

        case $? in
                 0)
                        echo "\"$dir\" selected.";;
                 1)
                        echo "No file selected.";;
                -1)
                        echo "No file selected.";;
        esac
cd "$dir"




#Choose bitrate
BITRATE=$(zenity --scale --text "Choose video bitrate" --min-value=1000 \
--max-value=5000 --value=1000 --step=10);echo $BITRATE





#Encode using mencoder
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf \
  -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 \
  -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=$BITRATE:\
keyint=15:vstrict=0:acodec=ac3:abitrate=128:aspect=16/9 -ofps 25 \
-o movie.mpg "$FILE" 2>&1 | awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/,"  ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Position :\\t"$1"\\nFrame :\\t"$2"\\nPercentage :\\t"$3"%\\nFrame Rate :\\t"$4"\\nTime Remaining :\\t"$6; fflush();}' | zenity --progress --auto-kill --auto-close



#Create an xml file for dvdauthor 
echo '<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>' > dvdauthor.xml




#Create dvd file structure
dvdauthor -x dvdauthor.xml 2>&1 | awk '{ print $1; fflush() }'| zenity --progress --pulsate --auto-close \
--text "Creating dvd file structure"




#Burn to dvd or create an iso

ans=$(zenity  --list --text "do you want to burn straight to dvd or create an iso?" --radiolist  --column "Pick" --column "Opinion" TRUE 'Create an iso'  FALSE 'Burn straight to dvd (please insert dvd)'); 
 
 if [ "$ans" = "Burn straight to dvd (please insert dvd)" ]

 then 
        dvd+rw-mediainfo /dev/dvd
fi

if [ $? -eq 0 ]
  then dev=/dev/dvd
  
  else dev=/dev/dvd1
fi


if [ "$ans" = "Burn straight to dvd (please insert dvd)" ]

 then

   growisofs -Z "$dev" -dvd-compat \
"$dir"'/DVD'  2>&1 | awk '{ print $1; fflush() }' | zenity --progress --auto-close \
--text "Burning DVD" && eject "$dev"


 else
     mkisofs -dvd-video -v -o dvd.iso "$dir"'/DVD' 2>&1 | awk '{ print $1; fflush() }' | zenity --progress --auto-close \
--text "Creating iso file"

fi




#cleanup 
zenity --question --text "Do you want to delete temporary files?"; 

if [ $? -eq 0 ]
   then 
   rm "$dir"'/dvdauthor.xml' & rm "$dir"'/movie.mpg' & rm -r "$dir"'/DVD'
fi
 zenity --info \
          --text="Enjoy your film."
exit
```

---

### Post by harold4 on 2008-01-11
Nice example.

---

### Post by prophet73 on 2008-01-11
Thank you.

---

### Post by vnevoa on 2008-06-01
Excelent work on the awk arguments!!! :)
Thanks a million!

---

### Post by ezramorris on 2008-09-12
> **prophet73 said:**
> I've worked it out it was when the output from mencoder was getting to 1000s when it was going wrong,here's the finished script.


Hi,
Just a couple of things which could make this a tiny bit better. Perhaps consider these for future scripts.

1) 'if' does something if the result is true (ie. exit 0), so instead of

```
FILE=`zenity --file-selection --title="Select a File"`

        case $? in
                 0)
                        echo "\"$FILE\" selected.";;
                 1)
                        echo "No file selected.";;
                -1)
                        echo "No file selected.";;
        esac
```

you could just do

```
if FILE=$(zenity --file-selection --title="Select a File")
        then echo "\"$FILE\" selected."
        else echo "No file selected."
        fi
```

you could also do the same for the bit further down.

```
#Choose a destination for your project
if dir=$(zenity --file-selection --directory --title="Select a project destination")

        then echo "\"$dir\" selected."
        else echo "No file selected."
fi
cd "$dir"
```

2) Also notice that I changed the backticks `somecommand` to $(somecommand). Backticks are now deprecated, so $(...) is the alternative and should be used.

3) Replace

```
vid()

{
file -i "$FILE" | echo $1 | grep -i '\.avi$'
}

if ( vid "$FILE")
        then
	avi="1"
fi	

if [ $avi -eq "1" ]; then
```

with

```
if [[ $FILE = *.avi ]]; then
```

All you are doing is finding the filename ends in .avi.

4) You can tidy up the #Burn to dvd or create an iso and #cleanup section a bit too.

```
#Burn to dvd or create an iso

ans=$(zenity  --list --text "do you want to burn straight to dvd or create an iso?" --radiolist  --column "Pick" --column "Opinion" TRUE 'Create an iso'  FALSE 'Burn straight to dvd (please insert dvd)')

if [ "$ans" = "Burn straight to dvd (please insert dvd)" ]

 then

  if dvd+rw-mediainfo /dev/dvd
   then dev=/dev/dvd
   else dev=/dev/dvd1
  fi  

  growisofs -Z "$dev" -dvd-compat \
"$dir"'/DVD'  2>&1 | awk '{ print $1; fflush() }' | zenity --progress --auto-close \
--text "Burning DVD" && eject "$dev"

 else
  mkisofs -dvd-video -v -o dvd.iso "$dir"'/DVD' 2>&1 | awk '{ print $1; fflush() }' | zenity --progress --auto-close \
--text "Creating iso file"

fi


#cleanup 
if zenity --question --text "Do you want to delete temporary files?"; 

   then 
   rm "$dir"'/dvdauthor.xml' & rm "$dir"'/movie.mpg' & rm -r "$dir"'/DVD'
fi
 zenity --info \
          --text="Enjoy your film."

```

I hope this is more helpful than critical, and may you continue scripting !

---

### Post by davidryder on 2008-09-20
> **ezramorris said:**
> Hi,
Just a couple of things which could make this a tiny bit better. Perhaps consider these for future scripts.



```

  growisofs -Z "$dev" -dvd-compat \
"$dir"'/DVD'  2>&1 | awk '{ print $1; fflush() }' | zenity --progress --auto-close \
--text "Burning DVD" && eject "$dev"


I am having some trouble making the progress dialog display the actual progress of the process. The code I am using:

[code]growisofs -Z $drive -allow-limited-size $file 2>&1 | awk '{ print $1; fflush() }' |zenity --progress --percentage=0 --auto-close --text="Burning..." --title="BurnBIG Progress"
```

This is all I get:

[img]http://www.phpstory.net/graphics/ss_Sep_20_2008_1802.png[/img]

Any idea what the problem might be?

Thanks

---

### Post by prophet73 on 2008-09-20
This part " |zenity" should be "| zenity" you missed a space out between the pipe and the zenity command mate. It should work now.

---

### Post by mssever on 2008-09-20
> **prophet73 said:**
> This part " |zenity" should be "| zenity" you missed a space out between the pipe and the zenity command mate. It should work now.
That has nothing to do with it. I like to have spaces around my pipes for readability, but spaces aren't required. Try it.
> **davidryder said:**
> ```
growisofs -Z $drive -allow-limited-size $file 2>&1 | awk '{ print $1; fflush() }' |zenity --progress --percentage=0 --auto-close --text="Burning..." --title="BurnBIG Progress"
```
Try omitting zenity from the pipeline and see if the correct values are being printed.

---

### Post by prophet73 on 2008-09-21
Yeah you're right sorry about that.

---

