---
title: "zenity help"
date: 2006-09-06
forum: Programming Talk
---

### Post by Lunar_Lamp on 2006-09-06
I want to use zenity to make a part of a script slightly friendlier when renaming files;

zenity --entry --text="What do you want to call the file?" 

However, that line will output the users input to STDOUT, but I want it to be a variable name (i.e. $filename).  I can output to a file just by using standard redirection of output ( > FILE); but I can't work out how to make it a variable once I have done this, or if it is needed.

I'm convinced I'm just being really stupid here, but I can't figure it out.

---

### Post by Tomosaur on 2006-09-06
To direct a program's output to a variable, you need to enclose it in a dollar-bracket, like below:

FILENAME=$(zenity --entry --text="What do you want to call the file?")

That will cause the $FILENAME variable to be set to whatever the user inputs.

---

### Post by Lunar_Lamp on 2006-09-06
AHA!  Thanks, I knew that it was simple, and I had come across it before, but being new to bash scripting I was floundering a bit!

---

### Post by Lunar_Lamp on 2006-09-06
Ho-hum, I am now having another problem with zenity.  I don't know how to use 'return codes' from it's question dialogue.

From the man page:

>  Display a dialog, asking Microsoft Windows has been  found!  Would  you
       like  to remove it?. The return code will be 0 (true in shell) if OK is
       selected, and 1 (false) if Cancel is selected.

              zenity  --question --title "Alert"   --text  "Microsoft  Windows
              has been found! Would you like to remove it?"


My attempt to utilise this was:

```
rename ()
{
RenameAnswer=$(zenity --question --text="By default the file will be named $flv_file.mpg.  If you want to change this click OK, otherwise click cancel.")

	if [ "$RenameAnswer" = "0" ] ;
		then OutputFilename=$(zenity --entry --text="What do you want to call it? (.mpg will automatically be appended to the filename)" --title="FLVconvert")
		zenity --info --text="Press OK to convert flv file to $OutputFilename.mpg which will be found in $PWD"

	elif [ "$RenameAnswer" = "1" ] ;
		then OutputFilename=$flv_file
		zenity --info --text="Press OK to convert file to $OutputFilename which will be found in $PWD"

	else zenity --info --text="Something strange has happened here"

	fi
}
```

---

### Post by Tomosaur on 2006-09-06
A common problem. Zenity does not return an actual character (0 or 1) it returns a boolean operator (true, false). Therefore, you only need to use:
```

if $RenameAnswer
  then
  blah blah
else
  blah blah
fi

```

With boolean values, you don't need to use elif, since there are only two possible options (true or false), therefore, if $RenameAnswer is not true, then it must be true, so the elif statement is pointless. You only need to use 'else'.

You must also use a double equals (==) when comparing things. A single = means you want to set a variable to a value, whereas == means you want to see whether the two are equal.

---

### Post by Lunar_Lamp on 2006-09-06
```
rename ()
{
RenameAnswer=$(zenity --question --text="By default the file will be named $flv_file.mpg.  If you want to change this click OK, otherwise click cancel.")

	if "$RenameAnswer" *== true*
		then OutputFilename=$(zenity --entry --text="What do you want to call it? (.mpg will automatically be appended to the filename)" --title="FLVconvert")
		zenity --info --text="Press OK to convert flv file to $OutputFilename.mpg which will be found in $PWD"

	else 
		OutputFilename=$flv_file
		zenity --info --text="Press OK to convert file to $OutputFilename which will be found in $PWD"

	fi
}
```

I have tried this both with and without the "== true" part; both return te "else" value no matter what is selected.


EDIT: GAH! I realise as soon as I posted that I had left the " around $RenameAnswer from the original if statement.  Thanks!

---

### Post by Tomosaur on 2006-09-06
Yeah, you don't need the ==, I was just demonstrating that you were using the wrong symbol anyway :P

I take it this works now then?

---

### Post by Lunar_Lamp on 2006-09-06
OK, two more issues now.

The following function deletes $flv_file no matter which options is selected, it always reads the "if" condition and not the "else" condition.  This is a near identical situation to the previous one, so i can't work out what is going on here.

```
function flvdelete {

FileDeletionAnswer=$(zenity --question --text="Do you want to remove the original FLV file?")

	if $FileDeletionAnswer
		then rm $flv_file
		zenity --info --text="$flv_file deleted.  FLVconvert is finished."

	else 
		zenity --info --text="$flv_file not deleted.  FLVconvert is finished."

	fi
}

```


I am not sure how zenity --progress works.  I have the following line:

```
ffmpeg -i $flv_file -ab 56 -ar 22050 -b 500 -s 320x240 $OutputFilename.mpg | zenity --progress
```

It appears that this just stays at "zero" until the command finishes, at which point it shoots to 100%.  How do I get it to be more incremental?

---

### Post by Tomosaur on 2006-09-06
The zenity --progress option is pretty poor and is more a toy than a real indicator of progress. If you want it to be more incremental, you'll have to bloat up your script. I think it works by taking the number of commands and working out the percentages. Since you only have one program feeding into zenity, that command counts as 100%, and so once it's completed, you just get jumped to a 100% full bar. If you had say, 5 programs feeding into zenity, then each program's completion would fill the bar up by 20%, and so on and so forth.

As for your flv_file problem, try restructuring the code to save some space:
```

function flvdelete {
if $(zenity --question --text="Do you want to remove the original FLV file?")
  then rm $flv_file
  zenity --info --text="$flv_file deleted.  FLVconvert is finished."
else 
  zenity --info --text="$flv_file not deleted.  FLVconvert is finished."
fi
}

```

---

### Post by Lunar_Lamp on 2006-09-06
Well, thanks, that worked.  I don't understand why my way didn't work though...

Thanks again though!  Pity about the --progress bar though, but it works as a decent enough place holder at the moment as a reminder that the script is still running.

---

### Post by Tomosaur on 2006-09-06
Yeah. I use the progress bar too, but I don't really like it. It's quite useful to indicate when something hangs though, since the bar never fills up :D

As for why your way didn't work, I don't know. Scripting is pretty temperemental at times. Generally if something isn't working despite looking perfectly ok, you should just rewrite. Sometimes it's just like banging your head against a brick wall :P

---

### Post by pyros on 2006-09-08
you could try the --pulsate switch so at least it would look active.

---

### Post by Lunar_Lamp on 2006-09-09
The pulsate switch doesn't seem to do anything for me.  I presume it's supposed to make the orange bars switch left and right repeatedly, but nothing happens; there's no difference when I apply --pulsate to when I don't.

---

### Post by amu_314 on 2006-09-12
Any body knows 

How to stop close zenity auto matically....after 100% com-letion of progress bar

---

### Post by diavasudev on 2009-03-03
i am new to zenity and i wanted to display a countdown message like this:"Your system will shut down in 20 seconds" and the 20 should decrement with each second to show 19,18,17.....0 after each second...is this possible??

---

### Post by Sef on 2009-03-03
closed.  necromancing.

---

