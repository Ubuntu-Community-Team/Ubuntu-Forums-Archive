---
title: "little shell script"
date: 2011-06-08
forum: Programming Talk
---

### Post by d32l4 on 2011-06-08
hi guys,

I want a little *.sh -script which move files from the same category to the same folder.

I tryed:

```

#!/bin/bash
blau="\033[1;34m"
end="\033[0m"

 echo "$blau --$end" "$blau Start... $end"


mv -v *.avi *.AVI *.mpeg *.MPEG *.divx *.DIVX *.mkv *.MKV *.mpg *.MPG *.mp4 *.MP4 /home/d3z1v/Videos/
mv -v *.jpg *.JPG *.jpeg *.JPEG *.bmp *.BMP *.png *.PNG *.gif *.GIF /home/d3z1v/Pictures/
mv -v *.txt *.doc *.docx *.ppt *.pps *.TXT *.DOC *.DOCX *.PPT *.PPS /home/d3z1v/Documents/
mv -v *.mp3 *.MP3 *.wav *.WAV /home/d3z1v/Music/


 echo "$blau --$end" "$blau End... $end"


```

it works fine, but i dont want to see the errors:
mv: cannot stat `*.***': No such file or directory

but i want to see, if the scripts is moving a file//

it would be even better, if someone could give me the syntax for editing my script that im able to get the messages via:

```

 echo "$blau --$end" "$blau FILENAME was found and moved to Videos... $end"

```

Iam using:
Distro: Ubuntu 11.04 natty
Environment: Gnome
Terminal: Gnome-Terminal && fish

Thank you in advance for your help

---

### Post by papibe on 2011-07-08
I hope this is not too late.

What is happening is that some of the patterns are not being match to a particular file, so they are being passed 'as is' to the mv command. This is also happens on the ls command. For example:
```
$ ls *.gify
ls: cannot access *.gify: No such file or directory

$ mv *.gify ./tmp
mv: cannot stat `*.gify': No such file or directory

```
That is the expected behavior of bash as an interactive shell. In scripts the default can be change, so that the not matching expression is expanded as a null string. For that use this in your script:
```
shopt -s nullglob
```
Now in the case of a custom message for each copied file, you would have to copy one file at a time, so you can learn the result of the command mv. This is an example:
```
#!/bin/bash

# List of patterns.
FILES='*.jpg *.JPG *.jpeg *.JPEG *.bmp *.BMP *.png *.PNG *.gif *.GIF'

# Destination directory
DIR=./tmp

# Exapand non maching patterns to null.
shopt -s nullglob

for file in $FILES; do
	mv "$file" "$DIR" &> /dev/null

	if [ $? = 0 ]; then
		echo "$file was found and moved to $DIR."
	else
		echo "Unable to move $file to $DIR."
	fi
done

```
Hope it helps.

---

### Post by pafoo on 2011-07-08
[FONT=monospace]Dont make it so difficult

```


#!/bin/bash

PICS='*.jpg *.JPG *.jpeg *.JPEG *.bmp *.BMP *.png *.PNG *.gif *.GIF'

for item in $PICS 
do 
find /pics -type f -name $item -exec mv {} /allmypics \;
done


```[/FONT]

---

### Post by papibe on 2011-07-08
@pafoo: that does **[COLOR="Red"]NOT[/COLOR]** work, because $PICS is expanded by globbing in the 'for' line. To debug it, you can replace the 'find' line for 'echo $item' to see what I mean.

Regards.

---

### Post by pafoo on 2011-07-09
Not sure what you are talking about. Did you use single quotes? That removes the value of the * bub. When you do the for item in $PICS 

The for loop uses a " " as the delimiter and runs find perfectly, I just ran it on my server as a test and it worked fine.

My line was
[FONT=monospace][FONT=Verdana]
[/FONT][/FONT]```
[FONT=monospace]for item in $PICS; do 
echo $item; find /home/pic_test -type f -name $item
;done

*.jpg
/home/pic_test/pic1.jpg

*.JPG
/home/pic_test/pic1.JPG
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by papibe on 2011-07-09
If there are pics file in the directory in which the script is running, globbing will kick:
```
$ ls -R
.:
dir1/  dir2/  pic1.jpg  pic2.JPG  test9.sh

./dir1:
pic3.jpg

./dir2:
pic4.JPG

```
If you run your script here, $DIR will be expanded and the 'for' won't pass the '*.jpg' and '*.JPG' to the loop, and thus to the find.
```
$ ./test9.sh 
mv ./pic1.jpg /allmypics
mv ./pic2.JPG /allmypics

```
Your script won't be able to get to pic3 and pic4.

I hope it is s bit clear now.
Regards.

---

