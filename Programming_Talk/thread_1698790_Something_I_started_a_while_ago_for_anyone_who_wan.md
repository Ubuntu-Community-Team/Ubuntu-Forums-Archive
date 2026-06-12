---
title: "Something I started a while ago for anyone who wants it"
date: 2011-03-02
forum: Programming Talk
---

### Post by Shpongle on 2011-03-02
I was planning to make a scripting layer of automation and add voice controls and this was a part of the setup. its a setup script that creates social profiles for im , facebook , twitter and skype and toggles a ps3 headset on or off.

It could do with a lot more but I don't have the time at the minute . Just posting it here if anyone wants to add to it , just mod and repost it.

The aim was to have loads of setup scripts and add voice control.

As a hack you can make the scripts speak if you pipe them into espeak

The idea would be one main script that runs all the setup scripts for various tasks processes



```
#!/bin/sh

# Script to set up  and create the social and unsocial  profile scripts
#
# by Shpongle
#


#directory to place the created scripts
DIR="./social"

#check if it exists
if [ ! -d "$DIR" ];then
        mkdir -p social 
fi

#get infor for scripts

echo "what is your instant messenger client ? "
read IM

echo "what is your default browser ?"
read BRWSR

echo "what is your default twitter client ?"
read TWIT

echo "what is your voip client ?"
read  VOIP



echo '#!/bin/sh

#script which sets the system to a social profile
#It starts pidgin im, twitter, skype,  
# facebook in firefox and toggles the bluetooh headset on or off 
#
# toggle_headset by tsvetan
#
#
# Shpongle
# 2010
#
# Usage: ./social.sh
' >  social/social.sh

echo "$IM &" >> social/social.sh
echo "$TWIT &" >> social/social.sh
echo "$VOIP &" >> social/social.sh
echo "./toggle_headset.sh &" >> social/social.sh
echo "$BRWSR www.facebook.com &" >> social/social.sh




echo '#!/bin/sh

#script which sets the system to an unsocial profile
#It kills pidgin im, twitter, skype 
#
# toggle_headset by tsvetan
#
#
# Shpongle
# 2010
#
# Usage: ./unsocial.sh' > social/unsocial.sh
echo " killall $IM &" >> social/unsocial.sh
echo " killall $TWIT &" >> social/unsocial.sh
echo " killall $VOIP &" >> social/unsocial.sh
echo "./toggle_headset.sh &" >> social/social.sh


echo '#!/bin/bash
# by tsvetan

declare -i sinks_count=`pacmd list-sinks | grep -c index:[[:space:]][[:digit:]]`
declare -i active_sink_index=`pacmd list-sinks | sed -n -e '\''s/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\\1/p'\''`
declare -i major_sink_index=$sinks_count-1
declare -i next_sink_index=0

if [ $active_sink_index -ne $major_sink_index ] ; then
	next_sink_index=active_sink_index+1
fi

#change the default sink
pacmd "set-default-sink ${next_sink_index}"

#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e '\''s/index:[[:space:]]\([[:digit:]]\)/\\1/p'\'');
do
	pacmd "move-sink-input $app $next_sink_index"
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e '\''s/device.description[[:space:]]=[[:space:]]"\(.*\)"/\\1/p'\'' | while read line;
do
	if [ $next_sink_index -eq $ndx ] ; then
		notify-send -i notification-audio-volume-high "Sound output switched to" "$line"
		exit
	fi
	ndx+=1
done;' > social/toggle_headset.sh


chmod u+x social/social.sh
chmod u+x social/unsocial.sh
chmod u+x social/toggle_headset.sh
```

---

