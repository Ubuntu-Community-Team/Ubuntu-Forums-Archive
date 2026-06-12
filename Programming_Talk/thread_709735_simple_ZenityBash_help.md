---
title: "simple Zenity/Bash help"
date: 2008-02-27
forum: Programming Talk
---

### Post by Warpedflash on 2008-02-27
I am just learning bash and i decided that i would make somehing at least vaguely useful using zenity.
i am trying to make a simple way to add repositorys to the sources.list using checkboxes. Im am having a couple of problems with doing it (hence me being here)
my code:
```
mv /etc/apt/sources.list /etc/apt/sources.list.original

repos=$(zenity  --height 300  --width 750  --list  --text "Which repositaries do you want to add?" --checklist  --column "Check" --column "Vendor" --column "Reposiary" FALSE "#Virtualbox" "deb http://www.virtualbox.org/debian gutsy non-free" FALSE "#Wicd" "deb http://apt.wicd.net gutsy extras" FALSE "#Google Picasa" "deb http://dl.google.com/linux/deb/ stable non-free" FALSE "#Skype" "deb http://download.skype.com/linux/repos/debian/ stable non-free" --separator =" \n");

echo $repos >(zenity --progress --pulsate) >>test.list
```

now my problems :)
1)i do not know how to make the results for both columns 2 (Vendor) and 3 (Repository) echo to the new file. all that is written is the secon columns value...this means that the deb line is not copied accross...

2)i cannot get the seperator to be a new line no matter what i try it just prints the selected values on the same line, this is a problem as of course i dont want to comment out the actual deb repos... just the intro name in the line above...

3) i get a strange output of /dev/fd/63 and i have no idea where this comes from...

hopefully the screens can explain better than me...
Thanks for any help provided :)
Warpedflash

[IMG]http://warpedflash.com/ubuntu/Screenshot.png[/IMG]
[IMG]http://warpedflash.com/ubuntu/Screenshot-1.png[/IMG]

---

### Post by Mr. C. on 2008-02-27
You don't need zenity to echo those results into a file.  What you need to do is simple capture the choices or indexes of the selected items and the output what you desire into a file.  You obviously know the names of the repositories, as you've hard coded them into your zenity command line.

Instead of doing that, create a array of repositories and build up the zenity command line based upon that array.

Then, once you have the selected values, loop and output what you need into your output file.

You have basic 3-column data that looks like this:

```
FALSE "#Virtualbox" "deb http://www.virtualbox.org/debian gutsy non-free"
FALSE "#Wicd" "deb http://apt.wicd.net gutsy extras"
FALSE "#Google Picasa" "deb http://dl.google.com/linux/deb/ stable non-free"
FALSE "#Skype" "deb http://download.skype.com/linux/repos/debian/ stable non-free"
```

You might use three arrays for your values, one for the default value (col 1), one for the identifier (col 2) and one for the URL (col 3):

${defaultvals[]}, ${identifiers[]}, and ${urls[]}. When you get values back from zenity, loop through each item in the identifers array, and when you match one, output the the corresponding item in the urls array.

Alternatively, you could concatenate the data in a single array, for example an array called $rows[], and encode it like this:

```
rows[0]="FALSE|#Virtualbox|deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free"
```

and split the data into words when you pass the command line arguments to zenity, and test each ID returned from zenity by testing each array item for a sub-string match.

Try setting your output separator to TAB, and then just parse the output by splitting on TAB characters.

Anyway, this is just a quick overview.  Perhaps this will help you along.

MrC

---

