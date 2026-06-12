---
title: "mass recursive file rename w/ inherited directory name and sequential number appended"
date: 2007-04-01
forum: Programming Talk
---

### Post by srf21c on 2007-04-01
I would like to rename all the jpegs in a large file hierarchy so that the each file inherits the name of its current directory, along with a three digit sequential number tagged on the end.

For example, if I have the following file hierarchy

Pictures
---family
-------DSC00441.JPG
-------DSC00631.JPG
-------DSC00293.JPG
---cars
-------DSC00984.JPG
-------DSC00320.JPG

I would like the command or script to recursively rename all the files in the directory "Pictures" like so:

Pictures
---family
-------family-001.jpg
-------family-002.jpg
-------family-003.jpg
---cars
-------cars-001.jpg
-------cars-002.jpg


Ideally I'd like to accomplish this by using a single command in lieu of a script.  Any command line godz out there that know how to get this done?

---

### Post by srf21c on 2007-04-25
bump

---

### Post by ghostdog74 on 2007-04-26
a crude awk attempt, only tested with the sample dir structure you gave
```

ls -lR Pictures| awk '
     /^total/ || /^d/ || /Pictures\/:/ {next}
     /^Pictures/ { sub(/:$/,"", $0); dir=$0; split($0,fn,"/");x=1 ;next}
     { if ($9) { 
            split($9,ext,".")   
            num = sprintf("%03d" ,x++)
            cmd = "mv " dir"/"$9 " " dir"/"fn[2]"-"num"."ext[2]
            print cmd
            #system(cmd) # uncomment for actual
       }  
     }

```

---

### Post by bashologist on 2007-04-26
Edit: Sorry for the two posts. x_x

---

### Post by bashologist on 2007-04-26
This will work for recursive directorys:

Written in one line:
find -type d | while read d; do cd "$d"; c=1; for i in *.jpg *.JPG; do if [ ! -f "$i" ]; then continue; fi; r="${PWD##*/}-$(printf %03d $c).jpg"; mv -i "$i" "$r"; ((c++)); done; cd "$OLDPWD"; done

More readable code with indenting and stuff:
```
find -type d | while read d; do
	cd "$d"
	c=1
	for i in *.jpg *.JPG; do
		if [ ! -f "$i" ]; then
			continue
		fi
		r="${PWD##*/}-$(printf %03d $c).jpg"
		mv -i "$i" "$r"
		((c++))
	done
	cd "$OLDPWD"
done
```

---

### Post by srf21c on 2007-05-02
That did the trick...thank you very much.

---

### Post by asalford on 2008-01-17
The more I look at sed & awk, the more confused I become. I can't seem to get my hands around it. It appears to be a powerful tool for editing, but it appears you can really screw stuff up and irreparably damage your work.  However, reviewing this post solves much of the complexity I was facing.

The process may even be a multi step. I would not mind doing it by hand, but there are hundreds of files. Just not sure how to start.  to me it does seem like a multi step process is in order.  I do like the use of the directory naming convention, but would want my to be relative to the working directory.

the directory is /media/video/backup/ShopNotes

Then the first step for me is to make sure any with a lower case “Shopnotes” be capitalized to “ShopNotes” which is solved by the posts process.  then have any with a #two digit number add a leading zero “0” but not bother the ones that already have #three digits.  anything after the #digits should be kept except where "_" is found.  that will need to be replaced by a space.

so that

Shopnotes #05 - Turned Tool Handles.pdf

becomes

ShopNotes #005 - Turned Tool Handles.pdf

& something named:

Woodworking - ShopNotes #56 - Circular_Saw_Miter_Station.pdf

becomes

ShopNotes #056 - Circular Saw Miter Station.pdf

---

