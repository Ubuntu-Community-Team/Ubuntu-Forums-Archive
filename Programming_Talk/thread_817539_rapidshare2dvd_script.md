---
title: "rapidshare2dvd script"
date: 2008-06-03
forum: Programming Talk
---

### Post by dunryc on 2008-06-03
Hi all thought id try to get some input on a bash script ive written. If you have a rapidshare premium account and wish to download avi files from it (their always rared). This script will download the files from rapidshares server unrar them and encode to mpg then build a dvd and burn it. As I say i would love to get some comments or tips on how i can imporve this thanks dunryc 

> #!/bin/bash
#script by dunryc
#will dl files from a rapidshare server urar and convert to dvd #automaticly 
# needs a rapid share premium account premium acc

clear

#this is the user name and password for the rpaidshare account 
user=xxxxxxx
pass=xxxxxxxxx

#check if weve already downloaded the cooke from a previous session
if [ -f cookie ];

then
echo "Rapidshare cookie already available , skipping cookie download"
else
wget --save-cookies=cookie  --post-data="login=$user&password=$pass"  [https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi](https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi) --no-check-certificate
rm premiumzone.cgi

fi

################################################################################################################################################
################################################################################################################################################

#get the file name
echo "enter the file name you wish to use as input"
read filename

#check it exists

if [ -f $filename ]; then
echo "parsing rs links using $filename"
fi

#parse the links

sed 's/http/\^http/g' $filename | tr -s "^" "\n" | grep http| sed 's/\ .*//g' > output
grep [http://rapidshare.com/files/](http://rapidshare.com/files/) output > links
rm -r output

################################################################################################################################################
################################################################################################################################################

#now grab all the links

cat links | while read line; do
    wget "$line"  --load-cookies=cookie
done


################################################################################################################################################
################################################################################################################################################
#we should now have all the rar files in our origional folder 

#copy the rars to the desktop jic
echo copying rars to the desktop
cp *.rar ~/Desktop
#list all the rars in the directory (the one we dl the rars to , then extract the rared file and deltete the origional rars so we just have the movie 
ls -1 *.rar > ~/templist && RARFILE=$(head -1 ~/templist) && unrar e $RARFILE && rm -f *.rar
#make a temp directory in the home folder  
mkdir ~/temp
#copy to the desktop first so we dont have to dl the file again we have an origional
echo copying movie to the desktop
cp *.avi ~/Desktop
#move the avi file to our work directory
mv *.avi ~/temp
cd ~/temp
#rename the file to somthing we can use specified in the command line 
#atm just calling it new avi for testing purpoes 
mv *.avi new.avi

################################################################################################################################################
################################################################################################################################################


#check what sound our avi is encoded with if its ac3 we need to encode to mpg with a different command 
#is the avi ac3 ? 

AUDIO=$(mplayer -vo dummy -ao dummy -identify your_video.avi 2>&1 | grep AUDIO_FORMAT | cut -d '=' -f 2)

case $AUDIO in
	#YES IT IS 
       hwac3) do_this
          echo encoding with AC3 audio
	mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,harddup \
	-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:aspect=16/9 \
	-ofps 25 -o your_video.mpg new.avi
      
                ;;
    
	#NO ITS NOT 
        *wildcard* ) etc
                  ;;													
        *)  # default
            echo normal encoding
	    mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:576,harddup \
            -srate 48000 -af lavcresample=48000 \
            -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:aspect=16/9:acodec=ac3:abitrate=192 -ofps 25 -o new.mpg new.avi
		;;

esac


#eventualy we need to delete the temp folder 

################################################################################################################################################
################################################################################################################################################
#author the dvd complaint folders vobs etc 
dvdauthor -o dvd -x dvd.xml
#burn the dvd 
growisofs -dvd-compat -Z /dev/dvdrw -dvd-video ./dvd/
#make sure there is one in the disc first though 
cd ..
rm -r -f temp
echo all done remove your hopefully fully functioning DVD



oh yes i forgot to mention it requires mencoder and dvdauthor to be installed

---

