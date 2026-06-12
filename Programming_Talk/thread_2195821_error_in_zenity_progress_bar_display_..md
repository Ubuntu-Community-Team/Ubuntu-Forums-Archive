---
title: "error in zenity progress bar display ."
date: 2013-12-26
forum: Programming Talk
---

### Post by killer 007 on 2013-12-26
I used zenity and ffmpeg to build a gui frontend for conversion but the progress bar doesn't seem to work correctly , copy and paste and run it , you will know what i mean

```

#!/bin/bash
percent=0
zenity --question --title  "Welcome,Killer-Converter" --text "Welcome to killer-Converter,\n\n\n       choose file to convert"  --ok-label "Continue" --cancel-label "Cancel"
if [ $? == 1 ] ; then exit ; fi
x=$(zenity --file-selection --title "Please select a media file to convert")
#In the following line we are getting the size of the song to be converted
duration=$(ffmpeg -i "$x" 2>&1 | grep "Duration" | cut -d ":" -f 2-4 | cut -d "," -f 1)
#Now converting this time into seconds
hours=$(cut -d: -f1 <<< "$duration")
min=$(cut -d: -f2 <<< "$duration") 
sec=$(cut -d: -f3 <<< "$duration") 
duration_in_s=$(echo " ($hours*3600)+($min*60)+($sec) " | bc) #It is the duration in seconds.
if [ $? == 1 ] ; then exit ; fi
y=$(zenity --height=300 --title "Convert to following format" --list  --text "Convert $x to following format?" --radiolist  --column "Pick" --column "Opinion" TRUE mp3 FALSE ogg FALSE "flv" FALSE "avi"  FALSE "mp4")
if [ $? == 1 ] ; then exit ; fi
final_name="${x%.*}.$y"
zenity --question --title "Proceed" --text "You will be notified on completion. Proceed?" --ok-label "Continue" --cancel-label "Cancel"
if [ $? == 1 ] ; then exit ; fi
# here double quotes around $x is important try removing n see results
ffmpeg -i "$x" -y "$final_name" &     # here & will make the process run in the background
duration_product=00:00:00
#duration_product=$(ffmpeg -i "$final_name" 2>&1 | grep "Duration" | cut -d ":" -f 2-4 | cut -d "," -f 1) #duration of converted
#converting duration of converted song in seconds 
hours_product=$(cut -d: -f1 <<< "$duration_product")
min_product=$(cut -d: -f2 <<< "$duration_product") 
sec_product=$(cut -d: -f3 <<< "$duration_product") 
duration_in_s_product=$(echo " ($hours_product*3600)+($min_product*60)+($sec_product) " | bc) #It is the duration product  in seconds.
(
    while [ "$duration_in_s_product" != "$duration_in_s" ]
    do 
        percent=0;
        duration_product=$(ffmpeg -i "$final_name" 2>&1 | grep "Duration" | cut -d ":" -f 2-4 | cut -d "," -f 1);
        hours_product=$(cut -d: -f1 <<< "$duration_product");
        min_product=$(cut -d: -f2 <<< "$duration_product");
        sec_product=$(cut -d: -f3 <<< "$duration_product");
        duration_in_s_product=$(echo "(($hours_product*3600)+($min_product*60)+($sec_product))" | bc);

        percent=$(echo " ((($duration_in_s_product)*100)/($duration_in_s)) " | bc);
        echo "$percent";
        done
        ) |
              zenity --progress \
        --title="Converting" \
        --text="Converting" \
        --percentage=0
          if [ "$?" = -1 ] ; then
                  zenity --error \
                            --text="Conversion cancelled."
                            fi
zenity --info --text "Successful conversion,Converted file is in same directory as source file"
```

---

