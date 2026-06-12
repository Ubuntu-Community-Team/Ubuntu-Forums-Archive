---
title: "Image Directories sampling using Imagemagick"
date: 2007-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by pt123 on 2007-09-30
What does it do 
*uses imagemagick to create a sample listing of images in thumbnails
```
sudo apt-get install imagemagick
```
Sadly the version in Feisty & Gutsy are rather old, but can handle this script.

* this not an indexer, but allows you to get a better glance at the images in your collection. I wish an image application could do something similar, as I feel this is a much better way to browse through collections.

* eg. in a directory of 30 images is will create thumbnails for 6 (this can be changed) images. Not the first 6 images, but the 1st, 7th, 13th etc. So you can get a better sample
* for every sub directory in the image folder it creates a row of thumbnails
Please look at the attachment below for a better idea of what this does.

Some points to note in the code you have to set the folders for where your images are and where this script will do it's work and produce the final image of the all the sample thumbnails.

Currently it only looks for jpeg & jpg extensions, you can add more extension by changing this line
```

O=$IFS IFS=$'\n' arrpics=($(find . -maxdepth 1 -regex ".*\(jpg\|jpeg\)$" -type f )) IFS=$O

```

I have commented out the 2 lines below for safet,y but if you have created work folders correctly then you can uncomment them out 
#rm -rf "thumbs"
#rm -rf "rows"

Also in the terminal you will see error messages outputted by imagemarick most are harmless like this one:
convert: Corrupt JPEG data: 1 extraneous bytes before marker 0xdb `/media/main/Collection/Wallpapers/scenic/sunset/Setting Sun over Everglades National Park, Florida.jpg'.






Below is the code save it as imageColSampler.sh
then to run it use  ```
sh imageColSampler.sh
```

```

#!/bin/bash

#this is where all the images you want to be indexed/summarised
picsFolder="/media/main/Collection/Wallpapers/"

#this is where this script will create temp images and the final grid image
# make sure it is not in the filepath of the above picsFolder
# this folder needs to exist for the script to work
workFolder="/home/yourusername/magick/"

#set the fonts to use
largeFont="/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf"
smallFont="/usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf"

# set the no pics per folder to be thumbnailed
ppf=6 

#thumbnail size limits
tw=160
th=120

#width of the text labels
labelWidth=600

#the padding to the rows
sidePadding=40
paddingBottomRow=30

#### End of configuration settings

gridComm="convert  \(" 


cd "$workFolder"
# clear any previous thumb nails
# commented out for safety but if you have created work folders correctly then you can remove the comments
#rm -rf "thumbs"
#rm -rf "rows"
mkdir "thumbs"
mkdir "rows"

cd "$picsFolder"
	
	#fill the arrdir with all the subdirectories in the pics folder
	D=$IFS IFS=$'\n' arrdir=($(find . -type d | sort)) IFS=$D
	

#go through all the sub dirs looking for images
	for (( i = 0 ; i < ${#arrdir[@]} ; i++ )) 
	do
	   echo ${arrdir[$i]}
	   # these cds are so we return to the original path as arrdir is filled with rel paths
	   # from the base pic folder 
	   cd "$picsFolder"
	   cd "$picsFolder${arrdir[$i]}"
	   
	   # here you can add more extensions
	   # the max depth is there so we dont search images in sub directories below
	   O=$IFS IFS=$'\n' arrpics=($(find . -maxdepth 1 -regex ".*\(jpg\|jpeg\)$" -type f | sort)) IFS=$O	   

		#calculate the variable to figure out the sampling 
		numPics=${#arrpics[@]}
		modVar=$((numPics/ppf))
		currentPicNo=1
		
		# note to remove the ./ from the dirName - used in the labels
		dirName="${arrdir[$i]#./}"
		
		#inform the user
		##echo $numPics$"  , "$modVar$"  , "$currentPicNo
		
		for (( j = 0 ; j < ${#arrpics[@]} ; j++ ))
		do
			
			if [ $currentPicNo -le $ppf ]
			then 
			
			picName="${arrpics[$j]#./}"
			picPath="$picsFolder${dirName}/${picName}"
			
			thisComm="convert \"${picPath}\" -thumbnail ${tw}x${th} \
            -bordercolor white  -border 6 \
            -bordercolor grey60 -border 1 \
            -background  black  \( +clone -shadow 60x4+4+4 \) +swap \
            -background  white   -flatten \
            -depth 8  -quality 95   ${workFolder}thumbs/p${i}-${currentPicNo}.png "

			##echo $thisComm
			eval $thisComm 
			
			# below is used to get the next image depending on sampling size
			if [ $modVar -gt 0 ]
			then
			j=$((j+modVar-1))
			fi
			
			currentPicNo=$((currentPicNo+1))
			
			
			fi
			# currentPicNo -le ppf
		done 
		# picture loop   
		
	if [ $numPics -gt 0 ] #prevent folders without images being added
	then 
		#create the text for the row
		textComm="convert -background white  -fill black  \
		  -font $largeFont -pointsize 20 label:'${dirName}' \
		  -font $smallFont -pointsize 12 label:'.    ${numPics} images' \
		   -append  -size ${labelWidth}x   \
		   -bordercolor white -border ${sidePadding}x0  \
		    ${workFolder}rows/text${i}.png"
		eval $textComm 
		
		
	#combine the images	to form a row
	rowComm="convert  \(" 
	for (( m = 1 ; m < ppf+1 ; m++ ))
			do	
				rowComm=$rowComm$" ${workFolder}thumbs/p${i}-${m}.png"
			done 
	rowComm=$rowComm$" \) \
			 -background white +append  \
			 -bordercolor white -border ${sidePadding}x2  \
			 -gravity south -splice 0x${paddingBottomRow}  \
			 ${workFolder}/rows/row${i}.jpg"	
			 
	##echo $rowComm 		 
	eval $rowComm 

	#build the command to combine the rows
	gridComm=$gridComm$" ${workFolder}rows/text${i}.png ${workFolder}rows/row${i}.jpg"
	
	fi	# $numPics -gt 0
	
	done
	# directory loop   	
	

#append datetime to the filename so you don't end up overwritting them.	
dateTime=`date +"%Y%m%d_%H%M"`

gridComm=$gridComm$" \) \
		 -background white -append  ${workFolder}grid_${dateTime}.jpg"
		 
eval $gridComm 		 	



```

---

### Post by pt123 on 2007-10-01
Added sort to the images find command, otherwise they weren't being sorted by alphabetical order.

---

### Post by joselin on 2007-10-01
Great script... will try it.

---

### Post by Unterseeboot_234 on 2007-10-01
I was getting odd screen captures whenever I was doing python "live" sessions -- e.g. you have a python module open and running from one Console, you open another Console and change the attributes of your module while it is in memory. Python has "import whatever_module *". 

Unfortunately, ImageMagick has a command ... import 

```
import –window root –monochrome x.gif
```

That is: 
import .......... imagemagick command, ready to run at any time in console
- window .......... in this case, a window named root
-monochrome .......... in this case, a mono-color pallete
x.gif .......... In this case, the capture will saved as a file named x, in the gif format

But, because of python interpreter and imagemagick both ready to run from Console I get a Postscript image in my Current Working Directory -- $ cd.

Thanks for your post. I love Python and I love Imagemagick. Looking through the recent forums postings reminded me I have Imagemagick and I could then figure out where these screen captures were coming from.

---

### Post by pt123 on 2007-10-05
Thanks, I am liking the possibilites of imagemagick. 
I love BASH, one of the big reasons I have switched over from Windows. (MS)

---

