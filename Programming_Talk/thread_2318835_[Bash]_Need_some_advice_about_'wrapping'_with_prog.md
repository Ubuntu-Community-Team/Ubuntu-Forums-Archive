---
title: "[Bash] Need some advice about 'wrapping' with programs"
date: 2016-03-29
forum: Programming Talk
---

### Post by dev18 on 2016-03-29
Greetings.
    I hope this is the right forum for this. I've been working on a Bash script to play twitch.tv streams on the Raspberry pi. I've hit a bit of a hiccup and was wondering if someone could help?

So here is what I got in short:

#the stream name
in_streamer='streamer tag'

#quality of stream
quality='source'

#volume of playback
vol=0

#Designating screen dimensions. Using livestreamer + omxplayer because of the low Rpi resources and lack of Java support.
omx_x1=0; omx_y1=0; omx_x2=50; omx_y2=50

So I try to insert those variables into a single command like so:
(livestreamer twitch.tv/${in_streamer} ${quality} -np "omxplayer --vol ${vol} --win '${omx_x1} ${omx_y1} ${omx_x2} ${omx_y2}' ") >> 2&1>/dev/null &
The -np is passing the audio and video off to omxplayer. Something like VLC will not work for me.

The issue is livestreamer is throwing an 'unexpected argument' error for the "-- vol --win x1 y1 x2 y2" arguments. Without the --win it will work and won't complain about $vol. There has to be a way to wrap this somehow so everything is happy. The --win is super picky about those single quotes. 

From what I've tried, either it produces the previous error or the variables read out in plain text. Any advice would be appreciated!
          Thank you,

---

### Post by sisco311 on 2016-03-29
Quoting is very important in shell programming, but unfortunately the rules are often hard  for beginners and even for more experienced users. 

Mixing single and double quotes is something that I would try to avoid whenever is possible. 

According to [http://elinux.org/Omxplayer](http://elinux.org/Omxplayer) the --win option has two forms:
```

    --win 'x1 y1 x2 y2'     Set position of video window
    --win x1,y1,x2,y2       Set position of video window

```

So try the comma separated syntax. 

If you want to learn more about `quoting' in the shell, then check out: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by dev18 on 2016-03-29
> **sisco311 said:**
> Quoting is very important in shell programming, but unfortunately the rules are often hard  for beginners and even for more experienced users. 

Mixing single and double quotes is something that I would try to avoid whenever is possible. 

According to [http://elinux.org/Omxplayer](http://elinux.org/Omxplayer) the --win option has two forms:
```

    --win 'x1 y1 x2 y2'     Set position of video window
    --win x1,y1,x2,y2       Set position of video window

```

So try the comma separated syntax. 

If you want to learn more about `quoting' in the shell, then check out: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

Your suggestion worked. Thank you Sisco! That simple huh? [face palm] 

omx="324,317,686,451";
livestreamer twitch.tv/${in_streamer} ${quality} -np "omxplayer --vol ${vol} --win ${omx}" >> 2&1>/dev/null &

This is that by the way. Use it at your own risk :P
```

#!/bin/bash

inputDir="/home/pi/scripts/twitch/input.txt";
dataDir="/home/pi/scripts/twitch/data.txt";


echo "" > /home/pi/scripts/twitch/data.txt;
echo "" > /home/pi/scripts/twitch/input.txt;


declare -a optionsArray=(audio mobile low med high source alert);
declare -A stremmers; declare -A gaems; declare -A views;
declare -a siteArray=(www.twitch.tv www.google.com www.twitch.tv www.wikipedia.org www.twitch.tv www.facebook.com);
sAmnt=${#siteArray[@]};


quality="source";
vol=0;
volC="high";
toWatch="..."; 
idle=0;
freshBit=0;
#omx="24,17,686,451"; $fullscreen
omx="400,400,686,451";


Kill() {
	while [ "$(pgrep livestreamer)" ]; do
		kill $(pgrep livestreamer); sleep 1s;
	done
}


function Parse(){
	Kill
	if [ "$2" == "custom" ];then
		printf "\n Opening Stream based off: ${1}\n"; sleep 2s;
		(livestreamer http://twitch.tv/${2} ${quality} -np "omxplayer --vol ${vol} --win '${omxRes}'") >> 2&1>/dev/null &
	else
		in_streamer="$(echo "${stremmers[$1]}" | sed 's/\.//g')"
		in_game="$(echo "${gaems[$1]}" | sed 's/\.//g')"
		printf "\n Opening Stream: $1) $in_streamer : $in_game\n"; sleep 2s;
		livestreamer twitch.tv/${in_streamer} worst -np "omxplayer --vol ${vol} --win ${omx}" >> 2&1>/dev/null &
		#(livestreamer twitch.tv/${in_Streamer} ${quality} -np "omxplayer --vol ${vol} --win '${omxRes}'") >> 2&1>/dev/null &
		#(livestreamer twitch.tv/${in_Streamer} ${quality} -np "omxplayer --vol 0 --win '24 17 686 451'") >> 2&1>/dev/null &
	fi
}


function Refresh() {
	curl -s -H 'Accept: application/vnd.twitchtv.v3+json' -H 'Authorization: OAuth fb222a222n2ha0kd22220no26n5tkz' \ -X GET https://api.twitch.tv/kraken/streams/followed > $dataDir;
	streamers="$(cat $dataDir | grep -o 'display\_name"\:["^]*[^"]*"' | sed 's/display\_name\"\://g' | tr -d '"')";
	games="$(cat $dataDir | grep -o 'game\"\:["^]*[^"]*"' | sed 's/game\"\://g' | tr -d '"' | uniq)";
	viewers="$(cat $dataDir | grep -o 'viewers\"\:["^]*[^"]*"' | sed 's/viewers:\?//g' | tr -d '["],[,],[:]' | uniq)";
	freshBit=1;
}
Refresh


function PrintStr() {
	clear;
	case "$idle" in
		0 ) echo -e "\e[1;32m . . . Twitch.tv : iFolo\e[0m"
		;;	
		1 ) echo -e "\e[1;32m . . . . . . Twitch.tv : iFolo\e[0m"
		;;	
		2 ) echo -e "\e[1;32m . . . . . . . . . Twitch.tv : iFolo\e[0m"
		;;	
		3 ) echo -e "\e[1;32m . . . . . . . . . . . . Twitch.tv : iFolo\e[0m"
		;;
		4 ) echo -e "\e[1;32m . . . . . . . . . . . . . . . Twitch.tv : iFolo\e[0m"
		;;
	esac


	if [ $freshBit -eq 1 ];then
		stremmers=(); gaems=(); views=();
		stremmerLen=20; gaemsLen=28;
		x=1;
		for s in $streamers; do #list them
			if [ "$s" != "" ];then
				stremmers[$x]="$(echo "$s" | tr '[:upper:]' '[:lower:]')";
				while [ ${#stremmers[$x]} -lt $stremmerLen ]; do
					stremmers[$x]+=".";
				done
				while [ ${#stremmers[$x]} -gt $stremmerLen ]; do
					stremmers[$x]=${stremmers[$x]:0:(-1)};
				done				


				gaems[$x]="$(echo "$games" | sed -n "$x p" | tr '[:upper:]' '[:lower:]')";
				while [ ${#gaems[$x]} -lt $gaemsLen ]; do
					gaems[$x]+=".";
				done
				while [ ${#gaems[$x]} -gt $gaemsLen ]; do
					gaems[$x]=${gaems[$x]:0:(-1)};
				done				


				views[$x]="$(echo "$viewers" | sed -n "$x p")";
	
				if [ $x -ge 10 ]; then
					echo "$x) ${stremmers[$x]}|${gaems[$x]}|viewers:${views[$x]}";				
				else
					echo "$x)) ${stremmers[$x]}|${gaems[$x]}|viewers:${views[$x]}";				
				fi
				((x++));
			fi
		done
		freshBit=0;
	else
		for ((x=0; x<=${#stremmers[@]}; x++)); do #format
			if [ "${stremmers[$x]}" != "" ];then
				if [ $x -ge 10 ]; then
					echo "$x) ${stremmers[$x]}|${gaems[$x]}|viewers:${views[$x]}";				
				else
					echo "$x)) ${stremmers[$x]}|${gaems[$x]}|viewers:${views[$x]}";				
				fi
			fi
		done
	fi
	echo -e "\e[1;32m?) For more options\nEnter the # of the Stream to watch:\e[0m";
	read -t10 res;
	if [ "$res" == "" ];then
		((idle++));
			if [ "$idle" -gt 4 ];then
				Refresh
				idle=0;
			fi
	else
			case "$res" in
					"vaudio" ) idle=0; printf " Stream quality changed to audio only"; quality="audio"; res="";
				;;
					"vmobile" ) idle=0; printf " Stream quality changed to mobile"; quality="mobile"; res="";
				;;
					"vlow" ) idle=0; printf " Stream quality changed to low"; quality="low"; res="";
				;;
					"vmed" ) idle=0; printf " Stream quality changed to medium"; quality="med"; res="";
				;;
					"vhigh" ) idle=0; printf " Stream quality changed to high"; quality="high"; res="";
				;;
					"vsource" ) idle=0; printf " Stream quality changed to source"; quality="source"; res="";
				;;
					"amute" ) idle=0; vol=-4000; volC="mute"; res="";
				;;
					"alow" ) idle=0; vol=-1300; volC="low";  res="";
				;;  
					"amed" ) idle=0; vol=-2600; volC="medium"; res="";
				;;  
					"ahigh" ) idle=0; vol=0; volC="high"; res="";
				;;  
					"exit" ) idle=0; Kill; res="";
				;;  
					"ref" ) idle=0; Refresh; res="";
				;;
					"?" ) idle=0; 			
					printf "\n\n *) Enter a stream not listed.\n ref) Manually refresh the list.\n alert) Enter a streamer to highlight if present. (${toWatch})\n v+>>) Video quality: ${quality} {audio/mobile/low/med/high/source}\n a+>>) Audio volume: ${volC} {mute/low/med/high}\n\n";
					sleep 10s; res="";
				;;  
					"*" )
						idle=0;
						read -p " [?] Enter custom stream name to watch: " cres;
						Parse $cres custom;
						res="";
				;;
			esac
			
			if [ "$res" != "" ];then
				Parse $res;
			fi
fi
}
function Control() {
while true;do
       testPacket="$(ping -c 1 -s 0 -W 2 ${siteArray[$((RANDOM%$sAmnt))]} | grep -c "1[ ]packets[ ]transmitted\,[ ]1[ ]received")";
       if [ "$testPacket" -gt 0 ]; then
	        tempPacket="$(ping -c 1 -s 0 -W 2 ${siteArray[$((RANDOM%$sAmnt))]} | grep -c "1[ ]packets[ ]transmitted\,[ ]1[ ]received")";
		        if [ "$tempPacket" -gt 0 ]; then
					PrintStr
			else
					clear;
					printf " !) Check internet connection. (${siteArray[$((RANDOM%$sAmnt))]} unreachable)\n"; sleep 10s;
			fi
       else
			clear;
			printf " !) Check internet connection.(${siteArray[$((RANDOM%$sAmnt))]} unreachable)\n"; sleep 10s;
       fi
Control
done
}
Control

```

---

