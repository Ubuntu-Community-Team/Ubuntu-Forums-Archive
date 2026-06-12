---
title: "Simple BASH script to run a file with a particular program"
date: 2010-11-21
forum: Programming Talk
---

### Post by pieman711 on 2010-11-21
My girlfriends mum wants to use Phillips Music Writer( [http://www.quercite.com/pmw.html](http://www.quercite.com/pmw.html)), an open source program that converts specific plain text files into PDF style sheet music. It is coded from an old acorn program she used to use. Back then she would just drop the file onto the PMW icon and it would automatically show the window with the sheet music ready for printing. The re-make is a bit more tricky, you have to run the program from a terminal to get the postscript file then open that with something else that can read them to get it to display on screen.
I was hoping to write a simple bash script that would let you right clcik on a file then open with this script. the script would run the file with PMW and create the postscript file. Then automatically open the appropriate reader with the file. 
I want to know how to get the filename from the fie you've just right clicked on. I would imagine a loop would be needed to get the script to wait until the output file has been created too.
I've only ever made very simple BASH scripts before, I've got some experience from BASIC programming when I was younger too, so I may be coming back for a bit more help if I get stuck again.

Thank you in advance.

---

### Post by hakermania on 2010-11-21
I think you must have a search about nautilus scripts :)

---

### Post by hakermania on 2010-11-21
The script could be something like:
```

#!/bin/sh
#Execute the script that makes the file
/bin/yourscriptthatmakesthefile
a=1
#making the loop that checks if the file is created so far every 1 sec
while [ $a -eq 1 ]; do
if [ -s /home/$USER/file ]; then
echo "it exists!";
#run here PMW or something to open the created file
break; else
echo "It doesn't exist yet"; sleep 1; fi
done
```

---

### Post by pieman711 on 2010-11-22
Brilliant I'll give that a go and let you know how I get on with nautilus scripts. Thanks

---

### Post by ziekfiguur on 2010-11-22
The while loop is not necessary, the program will not continue until a command has finished, unless that command is followed by a &
```

#!/bin/sh

#Execute the script that makes the file, and give it the name of the file to convert as a parameter
/usr/bin/PMW "$1"

# this probably creates a file named something like "$1.ps" to view it run
evince "$1.ps"

```

Than just right-click on the file you want to convert, select open with other application, choose `use custom command' and navigate to your script. If you keep the remember this application for this type of files box ticked, it will show up un the open with list next time you try it.

---

### Post by ziekfiguur on 2010-11-22
If you want to be able to select multiple files and convert and view them all at once you could do this:

```
#!/bin/sh

for file in "$@"
do
    #Execute the script that makes the file, and give it the name of the file to convert as a parameter
    /usr/bin/PMW "${file}"

    # this probably creates a file named something like "${file}.ps" to view it run:
    evince "${file}.ps"
done


```

---

### Post by pieman711 on 2010-11-22
I've been playing around with BASH scripting and googling nautilus scripts like you reommended and just came back here to post my results, from the looks of it I've basically come up with what you've just said. 
```

#!/bin/bash

#if file already exists then delete it

if [ -e $@.ps ]
then
    rm $@.ps
fi

#Make new PostScript file using PMW 
pmw -includefont $@

a=1
#Making the loop that checks if the file is created so far every 1 sec
while [ $a -eq 1 ]; do
if [ -e $@.ps ]; then

#If it exists open it with evince
evince $@.ps
break; else
sleep 1; fi
done

```But considering what you have said about it not moving on until it has completed each step the first and last steps aren't really necessary and 
```

#!/bin/bash
#Make new PostScript file using PMW 
pmw -includefont $@

#open it with evince
evince $@.ps

```Thanks for all your help, that pointer to nautilus scripts was exactly what I was looking for (particularly the $@) so that you can just right click --> scripts and click on the right thing.
more info at... [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php)

Just one more thing... Does anyone know if there is a similar function to this nautilus scripts in Mac OSX, I generally try and avoid anything apple but have got sucked in to this and thought a similar command would be ideal.

---

### Post by ziekfiguur on 2010-11-22
> **pieman711 said:**
> 
```

#!/bin/bash
#Make new PostScript file using PMW 
pmw -includefont $@

#open it with evince
evince $@.ps

```

There are a few errors in this code. $@ will expand to a list of all the parameters (all the files that you are converting). I dont know if pmw works if you give it multiple filenames, but the way you use it with evince it will only append .ps to the last filename. (So it would be file1 file2 file3.ps)
A way around this would be:
```

for file in "$@"
do
    evince "${file}.ps" &
    # because of the & the script will continue before evince is finished
done

```

if pmw does not work with multiple filenames you might want to put that inside the for loop as well.

---

### Post by pieman711 on 2010-11-22
Thanks for that, I had only intended it to be used via the nautilus script right click interface and only one file at a time so that name would get passed as $@. I'll put those loops in now for multitasking. In the earlier example would it try and run PMW on all the files in the directory or just appropriate files. Would you need to keep the files separate to stop it causing an error if it came up against an unusual file?

---

### Post by ziekfiguur on 2010-11-22
> **pieman711 said:**
> . In the earlier example would it try and run PMW on all the files in the directory or just appropriate files. Would you need to keep the files separate to stop it causing an error if it came up against an unusual file?

That depends on PMW, I really don't know, but I think it's pretty easy to test for you. However, it can't hurt to put it in the for loop. You could also do this:
```
pmw -includefont "${file}" && evince "${file}.ps" &
```
The && here ensures that evince is only run when pmw finished without errors.

---

### Post by pieman711 on 2010-11-22
That's sorted it thanks. It now runs through multiple files, opening them in separate evince windows without any problems.
I'll put this as solved now :)

---

