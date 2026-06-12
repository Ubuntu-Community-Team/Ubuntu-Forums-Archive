---
title: "HOWTO: Download youtube videos with only this script - no requirements!"
date: 2008-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by alberto ferreira on 2008-10-17
[COLOR=Navy][U][B][SIZE=4][COLOR=Black]
[/COLOR][/SIZE][/B][/U][/COLOR][CENTER][SIZE=6][COLOR=DarkOrange]_**SMART FLASH-VIDEOS SAVE/DOWNLOAD SCRIPT**_[/COLOR][/SIZE] 2.2
[/CENTER]
[COLOR=Navy][U][B][SIZE=4][COLOR=Black] 
[/COLOR][/SIZE][/B][/U][/COLOR][COLOR=Navy][COLOR=Blue]This script is for educational purposes only I don't want to infringe any copyright[/COLOR][/COLOR]
[COLOR=Navy][U][B][SIZE=4][COLOR=Black]
[/COLOR][/SIZE][/B][/U][/COLOR][B][U][SIZE=4]What does it do:
[/SIZE][/U][/B][SIZE=4][SIZE=2]
[COLOR=DarkOrange]**_It Downloads AND saves flash videos from sites like youtube_**[COLOR=Black] (and has some more bonus) :)[/COLOR][/COLOR]


You[COLOR=DarkOrange] just[/COLOR] have to [COLOR=DarkOrange]"say" the name of the video OR it's URL[/COLOR] to save the video you want. 
[U]
**What happens then automatically:**[/U]
The script does not waste bandwidth if the video is already downloaded/being watched.
If no video is being watched it downloads the video (this behaviour can easily be modified, to NEVER download anything, to ALWAYS download or to ask BEFORE downloading, read ahead).[/SIZE][/SIZE]
[COLOR=Navy][U][B][SIZE=4][COLOR=Black]
README:[/COLOR][/SIZE][/B][/U]
[/COLOR][COLOR=DimGray][B]
[COLOR=Red]The guide looks big but believe me it's very easy/fast to read[/COLOR]

Gray[/B][/COLOR] areas of the HOWTO are "optional reading and are meant to be read by noobs"

Don't think I'm satisfied, although this script does everything I want more RIDICULOUS stuff :D I'm thinking about adding new features like:

[LIST]
[*]wait for video loading to reach 100% to save the file instead of the user having to call the script only when the loading is complete
[*]download the video given a URL if it isn't already in Cache or /tmp **[COLOR=Red]-ADDED in v 2.0[/COLOR]**
[/LIST]
 [COLOR=Red]Copy the script or download it (at the end of post)[/COLOR]
[U][B][SIZE=4][COLOR=DarkRed][SIZE=2]
[/SIZE][/COLOR][/SIZE][/B][/U][SIZE=4]**_Why is this script so special:_**[/SIZE]


[LIST]
[*]It requires **no software**
[*]It is **fully customizable** through a USER CUSTOMIZATION SECTION at the beggining of the script (understandable by everyone) this ensures it is a tool that works FOR YOU as YOU want without requiring thinkering with the script
[/LIST]

[LIST]
[*]_**wastes no bandwith**_* (it only uses the video you are watching and that is saved in /tmp) **unless you want to download the video, **read more...
[/LIST]

[LIST]
[*] Automates the saving file process by copying the file automatically
[*]**Unlike many other scripts you don't need to use quotes AND you can use spaces in the names**
[*][SIZE=3]**[SIZE=2]It has "smart naming" - this means that you can provide a custom name for the video _OR_ if you don't want to type the name of the video just give the URL and the script will name the video for you[/SIZE]**[/SIZE]
[*][SIZE=3][B][SIZE=2]The script knows if the video exists in memory or if it has to be downloaded and it does it's job accordingly wasting _no_ unnecessary resources 
[/SIZE][/B][/SIZE]
[/LIST]

[SIZE=4]**_How to use it:_**[/SIZE]

[LIST]
[*] make sure you only have one video open at the time of running the script
[/LIST]

[LIST]
[*] only execute the script when the flash video has the progress bar complete (in the next version the script will wait for the loading bar)
[/LIST]

[LIST]
[*] Don't close the video until the word Done appears on the console
[/LIST]
 [SIZE=4][B]
_Calling the script:_[/B][/SIZE]
**You have 2 options:**

1. /path/to/script [COLOR=Blue][COLOR=Red]http://....[/COLOR]
[/COLOR]**This option finds automatically the name of the video through the URL source**

2.       /path/to/script [COLOR=Red]name of the video[/COLOR]  
**If you use this option don't use the word "http" **

**[COLOR=Purple]Please read the USER CUSTOMIZATION SECTION at the beginning of the script to customize it to your will [/COLOR][COLOR=Purple]!!!!!!![/COLOR]**
  [php]#! /bin/bash
#Flash Downloader 2.2 - by Alberto Ferreira
#############################      USER CUSTOMIZATION SECTION      ################################
#Settings with numeric values and no further instructions assume: 1 (enabled) and 0 (disabled)
folder=$HOME # This is the default folder where videos are saved. Change it if you want
create_folder_if_it_doesnt_exist=1 #If the folder specified in the previous line does not exist it gets created
enable_video_preview=0 #you guessed it, after video saving is complete it is automatically played
script_wait_for_video_loading=0 #If set to 0 make sure you only run the script when video is loaded at 100% - currently under development
download=0 #If the file isn't in cache: -1(never download) 0(ask if user wants to download) 1(download without asking)
##########################   [END] USER CUSTOMIZATION SECTION [END]   #############################

if [ -z "$1" ];then
cat<<EOF
No arguments specified, script QUITTED

USAGE:

/script/path http://..... #Video URL(video name will be automatically found)
                                  OR
/script/path name of the video #Video name(video will be saved with this name)
EOF
exit 1
fi

#Script Initialization:
html_source=`mktemp`
temp=`mktemp`
arg=`echo "$@" | grep http`
page_source_downloaded=0
cached=/tmp/Flash*
[ "$create_folder_if_it_doesnt_exist" -eq 1 ] && [  -e "$folder" ] || mkdir $folder
[ ! -d "$folder" ] && echo "Invalid folder! Check folder in USER CUSTOMIZATION SECTION !!!" && exit 2

#Script functions:
get_video_download_URL(){
baseurl="http://youtube.com/get_video.php?"
[ "$page_source_downloaded" -eq 0 ] && wget ${arg} -O $html_source
videourl=`grep "watch_fullscreen" $html_source | sed "s;.*\(video_id.\+\)&title.*;\1;"`
downloadURL=${baseurl}${videourl}
}

download(){
download_permission="n"
[ "$download" -eq 0 ] && read -p "Download video(y)?" download_permission    
if [ "$download" -eq 1 ] || [ "$download_permission" = "y" ];then
get_video_download_URL
wget $downloadURL -O $folder/"$name".flv
fi
}

character_filter(){
name=`echo $name | sed 's/\// /g'`
}

#######################SCRIPT begins here##################################
if [ -z "$arg" ];then # arguments were custom name or URL
#copies the video with your custom name
name=`echo $@ | sed 's/ /\\ /g'`
character_filter
if [ -f $cached ];then
cp -i $cached $folder/"$name".flv
else
echo "There is more than one video open or no video at all!"
echo "Need URL of video to download it. If no URL is specified download is cancelled!"
read -p "URL:" arg
[ -z "$arg" ] || download 
fi
else
#Uses the URL to find the name
wget "$1" --output-document="$html_source" && page_source_downloaded=1
#Find the name of the video (it will look for the first line with the tag title and selects it's contents)
name=`cat $html_source | grep title | head -1 | awk -F'<title>' '{print $2}' | awk -F'</title>' '{print $1}' | sed 's/ /\\ /g'`
character_filter
[ -f $cached ] && cp -i $cached $folder/"$name".flv || download
fi
[ "$enable_video_preview" -eq 1 ] && 2>/dev/null totem --enqueue $folder/"$name".flv &
echo "Done"
exit 0
[/php][COLOR=#000000][COLOR=#ff8000]
[/COLOR][COLOR=#007700]
[/COLOR][/COLOR][COLOR=DarkSlateBlue][B][COLOR=Black][U][SIZE=4]For noobs: Script "install" instructions:

[/SIZE][/U][/COLOR][/B][COLOR=Black][SIZE=4][SIZE=2]1- Copy the script
2- Open a terminal (Go to Applications>Accessories>Console)
3- Open the editor:
[/SIZE][/SIZE][/COLOR][/COLOR]> nano the_name_you_wish_to_give_to_the_script.sh4- Press F11 to maximize the console then paste the script (Ctrl+Shift+V)
5- Save (Ctrl+O) and quit (Ctrl+X)
6- make the script executable:
> chmod +x the_name_you_gave_to_the_script_**Recommended:**_

This script is most useful if you can call it quickly. This is done in two parts: Create an alias and a console shortcut

Alias HOWTO:
[COLOR=DimGray]An alias works like this:
alias name_of_the_alias='command_that_you_wish_to_execute'
The name of the alias cannot be a system command or program name otherwise it will override that command (this can be useful but not in our case).
In our case, we're going to choose a small name for the alias (we want to write it quicly) and then we put the path of the script in the command section of the alias, thus our alias will be for instance:
alias fd='~/flashdownloaderscript.sh'
fd (flash download) :D[/COLOR]


Now that you know how an alias works:
**PART I**
1 - Open a terminal
2 - write: "nano .bashrc"
3 - add your alias, i will give an example once again:
alias fd='~/flashdownloaderscript.sh'
4-save and quit
**PART II**
Create a shortcut in the keyboard to the console:
System>Preferences>Keyboard Shortcuts>Desktop Section>Execute a console>Choose your shortcut


Now you can just use the console shortcut, type the alias name and then the parameters you wish to pass to the script (URL or the custom name).
[COLOR=DarkSlateBlue] 

[/COLOR][U][B][SIZE=4][COLOR=DarkRed][SIZE=2]BUG FIXED:
[/SIZE][/COLOR][/SIZE][/B][/U]**[COLOR=DarkRed][COLOR=black]Because "/" characters are not supported in linux files's names if a video from youtube contained these characters in the name the script wouldn't work. Now, if a video contains these characters, they are automatically replaced.[/COLOR][/COLOR]**[COLOR=DarkSlateBlue] Bug found by [/COLOR]_**[COLOR=DarkRed][whitethorn]("http://ubuntuforums.org/member.php?u=424805")[/COLOR]**_
[COLOR=DarkSlateBlue] [SIZE=5][U][B][COLOR=Purple]Feel free to make questions, suggestions and requests
I count in YOUR feedback to add more features to the script!
[/COLOR][/B][/U][/SIZE][/COLOR]

---

### Post by alberto ferreira on 2008-11-13
bump BUMP - sorry, but the post is completely new and I believe that this is seriously worth it. Check it out and tell me what you think.
Once again, opinion sharing , requests and constructive criticism welcomed ;)

---

### Post by whitethorn on 2008-11-13
Hi, I gave your script a shot.  Didn't work for me, maybe I didn't read something correctly, anyway I decided you'd probably want to see what error I get.  

[quotevid [http://www.youtube.com/watch?v=ZxyQr7MB7c0](http://www.youtube.com/watch?v=ZxyQr7MB7c0)
--2008-11-14 01:29:30--  [http://www.youtube.com/watch?v=ZxyQr7MB7c0](http://www.youtube.com/watch?v=ZxyQr7MB7c0)
Resolving [www.youtube.com](www.youtube.com)... 208.65.153.253
Connecting to [www.youtube.com|208.65.153.253|:80](www.youtube.com|208.65.153.253|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 136898 (134K) [text/html]
Saving to: `/tmp/tmp.PtizN15410'

100%[======================================================================================================================>] 136,898      172K/s   in 0.8s    

2008-11-14 01:29:32 (172 KB/s) - `/tmp/tmp.PtizN15410' saved [136898/136898]

cp: cannot create regular file `/home/*******/Desktop/YouTube - Porchisode #2 - Looking Down On The Sky (Free song at mollymarlette.com/discovernewmusic).flv': No such file or directory
Download video(y)?y
/home/*********/Desktop/YouTube - Porchisode #2 - Looking Down On The Sky (Free song at mollymarlette.com/discovernewmusic).flv: No such file or directory
Done
][/quote]

I'll look into a bit more when I have more time, but at a glance it looks good.

---

### Post by alberto ferreira on 2008-11-14
Ok, the problem is that you cannot create files in linux that contain some special characters, like "/" in the name. 
That's why the program gave an error. I will work on this, this night, to filter these invalid characters.

Thanks

---------------------------------------------------------------------

EDIT: Bug has already been fixed, the script is now, bullet-proof ;)


Thanks

---

### Post by raghuramos1987 on 2010-08-02
hey... thanks a lot! looking forward to the next version... works like a charm! :)

---

### Post by raghuramos1987 on 2010-08-02
I just wrapped it in a python script. Maybe you can move this into bash (i like to stay away from bash :) )... 

i arrange my ipod files separately... so... using pacpl here... might need to install that for this script to work... on ubuntu... 

sudo apt-get install pacpl


also, the python script assumes this dir structure

HOME dir
----Music
---------flv_files
---------mp3_files

---

