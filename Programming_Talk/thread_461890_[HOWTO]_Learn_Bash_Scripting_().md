---
title: "[HOWTO] Learn Bash Scripting (??)"
date: 2007-06-02
forum: Programming Talk
---

### Post by eentonig on 2007-06-02
Simple. By doing it yourself. ;)

This is my first attempt. So shoot me if you find stupid mistakes.

**[COLOR="Red"]The Reason:[/COLOR]**
It's already a long time that I tell myself I need to improve my scripting skills. So, in order to do just that, I decided to start creating a little script  and share it with the community. This way, everybody gains.
- I get the added value of a thousand eyes screening my scripts for errors and ways to do things better. 
- Experienced scriptguru's get the fun of showing their all mighty skills.
- Unexperienced guys like me can follow and think along while the script develops.
- People who just need the functionality can copy and past the script once it's complete.

**[COLOR="Red"]Let's define my first task.[/COLOR]**

"Create a script that processes all pictures in a given folder. The actions taken should include:
- resize (user defined sizes), 
- create a 'polaroid like' look, 
- stamp it with a generic message.
- output to a specific folder.
Bonus points:
- Upload results to a ftp server
- format the strings to paste in a topic, so it shows the images. ([img ] url [/ img])

**[COLOR="Red"]Requirements[/COLOR]**
- Imagemagick needs to be installed.
> sudo apt-get install imagemagick
- Patience :p


[COLOR="Red"]**Current status:**[/COLOR]
The script runs against a set of pictures in the folder where it's executed. BUT, the 'stamp' image needs to be created prior to running the script.
I already created the function to create the 'stamp' image. but it isn't called in the script yet. For now, just copy and past the function in a terminal and run it once. Make sure to name the result "label".

[COLOR="Red"]**Next issue to solve:**[/COLOR]
- Why doesn't the script continue to run after I created a label?

[COLOR="Red"]**Open issues.**[/COLOR]
- More and clearer commenting in the script.
- Give the user some good feedback while the script is running.
- Allow user to specify final filesize. (Warning: The "stamp"-image needs to be sized accordingly.)
- ...


**[COLOR="Red"]The script. Latest version[/COLOR]**

> #!/bin/bash

# Script to format pictures in a polaroid fashion. And to allow the user to attach a custom label to them
# 

# Author: Roel Fonteyn
# Mail: [email]eentonig@gmail.com[/email]
# Ubuntuforums profile eentonig
# Date : ../../....
# v.0.1


# I still need to enhance functionality.
# Ideas for improvement are:
# - Specify filesize for output
# - Allow input folder to be specified.
# - Random rotation
# - Allow user input for the watermark image.
# - Allow user to select Font
# 
###########################################################################
### 				Functions 				###
###	we want to make the script more readable and flexible. 		###
###########################################################################


# Function to check if the required programs
function f_checkpresence () 		# verify if program 'x' is installed.
	{				
	if [ -z "$(which $1)" ]; then	# If the program is not present, exit the script.
	        echo;echo "$0: error: $1 not installed"
	        exit 1
	fi
	}
# Function end


# Function to ask for the location of a file. And tests if the file is present.
function f_IsFilePresent
	{
	echo -n "Give the fullpath to the image (ex. /home/username/images/): "
	read v_labelpath				# The folderpath given by the users
	if [ ! -d $v_labelpath ]			# Test if this folder exists
	   then echo " $0: error: This folder does not exist."
	        exit 1					# abort if wrong input.
	fi
	echo -n "Give the image name (ex. watermerk.png): "
	read v_imagename				# The image chosen by the user
	v_file="${v_labelpath}/${v_imagename}";		# The full path to the file
	echo $v_file
	if [ -f ${v_file} ]				# Test if this file exists
	   then						# If it exists...
	   	echo "I will now show the file. Close the image to continue the script \
	   	and confirm that this is the correct file."
	   	display $file;				# show it to the user.
	   	echo -n "Is this the file you want to attach to your pictures (y/n)? "
	   	read v_fileok				# Does the user agree with the file shown?
	   	case $v_fileok in
	   		"y" )				# Correct file was shown
	  			echo "Ok";;
	  		"n" )				# Wrong file was shown
	  			echo "restart the script and choose the correct file.";;
	  		*   )				# Wrong answer. (And I need to find a more gracefull way
	  						# To allow the user the re-answer the question without being
	  						# thrown out of the script.
	  			echo "Please only answer with 'y' or 'n'";exit 1;;
		esac
	   else
	   echo " $0: error: This file does not exist."
	   exit 1				# Abort if wrong.
	fi
	}
# Function end



# This Function serves to make the text label we want to put on the final image
# It requires four variables to be past on to it. (font, text, filename and size
# Also, the fontsize and tekstlength is limited to the output size you specified.
# Font needs to be specified with the full pathname.
vMark="/home/${USER}/HVPics/tmp/label.PNG"		# this is the tekst label to attach
function f_NewLabel () 
	{ 
	v_font1=$1					# i.e. /home/rfonteyn/art/Ttf/BIGLOG__.ttf
	v_text1=$2					# The text to display. Why can I only use one word?
	v_wm1=$3					# output name for the watermark. not the extension. This needs to be PNG format
	v_size1=$4					# The size to put on our image
	echo $v_size1
	convert -size $v_size1 xc:none -font $v_font1 -pointsize 72 \
           -annotate +25+70 $v_text1   -blur 0x4 \
           -fill white  -stroke black  -annotate +25+65 $v_text1 \
           ~/HVPics/tmp/$v_wm1
           vMark="/home/${USER}/HVPics/tmp/${v_wm1}"
        } 




###########################################################################
### 				Functions 				###
###	we want to make the script more readable and flexible. 		###
###########################################################################

###########################################################################
### 				Program Start 				###
###########################################################################

clear

# Definition of the variables needed.
vTemppolaroid="tmp_polaroid.png"	# Picture after rezize 
vTempWM="wmark_dissolve.png"		# Image after the Watermark is applied
v_imgcounter=0				# Counters serves to provide unique filenames for the results.
v_folder="/home/${USER}/HVPics/"	# This is the output folder.

f_checkpresence convert; 		# check presence program 'convert'. If not present, abort.

echo; echo; echo "We will now start to process your pictures."

	# First we check if the label-img exists. And if it exists, we ask the user
	# if he wants to use that, or create a new one.
	echo;echo "Part of the process is to attach a standard text to your images. This text will be placed "
	echo "on a seperate and transparant PNG image. If you already have a picture to attach, you can skip "
	echo "this step."

	echo;echo -n "Do you already have a file to attach to your pictures (y/n)? "
	read v_previouspicture				# We read the user input.

	case $v_previouspicture in
	   "y" ) # If the file exist, we ask the user where it is
	   	echo "You claim to already have a file to use. Let's check if the file is available";
	   	f_IsFilePresent;			# function creates error.
	   	;;
	   	
	   "n" )
	   	echo "So you don't have a file ready. Let's create one."
	   	# Ask the user what font to use.
	   	echo "What kind of font do you want to use? Please specify the full path to the font."
		echo -n "This is usually a file under /usr/share/fonts/\<fontname\>: "  
	   	read v_font				# i.e. /home/rfonteyn/art/Ttf/BIGLOG__.ttf
		# Ask the user what text he wants to display.
		echo;echo "What test do you want to be displayed? Do not forget to place '\"' if you use more than one word."
		echo -n "Text? " 
		read v_text				# The text to put on the pictures.
		# What name to give the file?
		echo;echo "we will call this file \'label.PNG\'"
		v_wm="label.PNG"			# output name for the watermark. 
		
		# What size do we want for the output pictures?
		echo "Please specify the dimensions for the label. These must be smaller then the Pictures we will create." 
		echo -n "size \(600x140\): "
		read v_size				# The dimensions for the label
		echo "$v_size $v_font $v_text $v_wm"
		f_NewLabel $v_font $v_text $v_wm $v_size
		echo "The new label is created. Close the image to continue."
		display $vMark
		;;
	   *   )
	   	echo "Please answer with 'y' or 'n'";exit 1;;
	esac

for vPicturein in $(ls | egrep '\<jpg$|JPG$|png$|PNG|gif$|GIF$|bmp$|BMP$\>') # for all image files in the current dir.

do
		let v_imgcounter=v_imgcounter+1;
		echo; echo "The pictures will be places in ${v_folder}"
		echo $v_folder
		v_imgoutput="${($v_folder)hv_($v_imgcounter)}.png";		# Set the output filename

# This is the imagemagick string to resize and create a Polaroid like photo with a little twist.
		convert  $vPicturein -resize 640x480 -gravity south -background white  -splice 0x80 -bordercolor white  			-border 30 -bordercolor grey60 -border 2 $vTemppolaroid

# and here we try to paste it.
		composite -dissolve 25% -gravity south $vMark   $vTemppolaroid  $vTempWM
										# Combine the temp file with a watermark

# And give it a little twist.
		convert $vTempWM -background none -rotate 6 -background none \( +clone -shadow 120x8+8+8 \) +swap 				-background none -flatten -depth 8  -quality 95 $v_imgoutput

# remove our temp files
		rm $vTemppolaroid
		rm $vTempWM
done


---

### Post by raja on 2007-06-02
I guess your intention here is to brush up on bash while doing this. But it looks to be a bit too much of a load for bash. It would be so much simpler to write it in python, and if you use PIL for the image processing, you can end up with a program that you can use in windows and mac too. 
Again, I know your aim here is to learn bash scripting than to find the best way to do this, but I personally find shell too troublesome beyond a certain size.

---

### Post by eentonig on 2007-06-02
Point taken. 

But you're right. The main goal is to brush up my shell skill.

And then, I'll have to learn Python and write it all over again. :mrgreen:

---

### Post by TreeFinger on 2007-06-02
I am looking to learn to do something exactly like this in Python. I was really excited when I read what you wanted to do with your script.

I want to write a program like this in python because my mother always complains about having to do all resizing and renaming on her pictures so I figure this is a good way to learn some programming. Right now though I have no idea where to start as I am just beginning to learn Python.

---

### Post by bashologist on 2007-06-02
> - How can I test on the presence of a given application, prior to running the script? This way, I could inform the user that they need to install imagemagick if it's not present.

If you need the convert command that's part of the imagemagick package then you could chech if the command's available. The portability probably isn't very good but for gnu at least you can do this:
```
if [ -z "$(which convert)" ]; then
        echo "$0: error: imagemagick not installed"
        exit 1
fi
```

> for vPicturein in `ls | egrep '\<jpg$|JPG$|png$|PNG|gif$|GIF$|bmp$|BMP$\>'` # for all image files in the current dir.
"The backquote (`) is used in the old-style command substitution, e.g. foo=`command`. This syntax is deprecated in favor of foo=$(command). Backslash handling inside $() is less surprising, and $() is easier to nest. See http://wooledge.org/mywiki/BashFAQ#faq82" -- greybot

You seem to be forgetting to quote variables. It's always a good idea unless maybe you're using perl.
"USE MORE QUOTES! Read [http://www.grymoire.com/Unix/Quote.html](http://www.grymoire.com/Unix/Quote.html) -- Optimally, you should quote every parameter expansion ($foo)." -- greybot

> **raja said:**
> I guess your intention here is to brush up on bash while doing this. But it looks to be a bit too much of a load for bash. It would be so much simpler to write it in python, and if you use PIL for the image processing, you can end up with a program that you can use in windows and mac too. 
Again, I know your aim here is to learn bash scripting than to find the best way to do this, but I personally find shell too troublesome beyond a certain size.

It can be done easily in bash, and imagemagick can manipulate images in seconds.

---

### Post by eentonig on 2007-06-02
@bashologist

Thanks!!! I'll go through my script again and use your comments.
I'll also include the test to see if 'convert' is present.

I originally had the convert commands backslashed and commented per option, but it tended to give errors while testing. So I removed them. I'll put them back now that I know this part is already working.

Another thing that caused headaches, was the '#' comments behind a commandline. Sometimes it broke the command. Sometimes it didn't. Must have been something I was doing wrong, but for now, the easiest solution was to remove them. Again. I'll put them back in.

Concerning the (`). Am I correct if I have to rephrase that command as following?

> for vPicturein in $(ls | egrep '\<jpg$|JPG$|png$|PNG|gif$|GIF$|bmp$|BMP$\>') # for all image files in the current dir.

Anyway. I'm first going to bed now and will post an updated version tomorrow.

---

### Post by statictonic on 2007-06-03
You've probably already found this, but this is a good resource on bash scripting.  [http://www.tldp.org/LDP/abs/html/index.html](http://www.tldp.org/LDP/abs/html/index.html)

---

### Post by bashologist on 2007-06-03
> **eentonig said:**
> Concerning the (`). Am I correct if I have to rephrase that command as following?

Anyway. I'm first going to bed now and will post an updated version tomorrow.

That looks very good, yes. Another way might be to not use the the command substitution like this:

```
ls | grep -i "jpg$\|png$\|gif$\|bmp$" | while read filename; do
	# process filenames here
	echo "$filename"
done
```And also you could make grep search for case insensitive patterns with the "-i" switch.

Have a good night eentonig!

---

### Post by eentonig on 2007-06-03
Ok,

I just posted an updated version in the first post.

Big changes:
- Script checks on the presence of the 'convert' program.
- User is allowed to specify an existing watermark to use.
- User can create a custom watermark.

New questions:
- Why can I only use one word in the command to create the watermark picture? Is it because of the options I use, Or am I inserting my data the wrong way?
- Why doesn't the script contonue after I created a new label?

---

### Post by cmnorton on 2007-07-03
"Linux Shell Scripting with Bash" 
Ken O. Burtch 
Developer's Library 2004

is a pretty good book. 

The O'Reilly "Learning the Bash Shell" is another good book, and is more into the fundamentals of Bash.

---

