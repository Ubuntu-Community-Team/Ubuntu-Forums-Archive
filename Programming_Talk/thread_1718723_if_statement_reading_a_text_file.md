---
title: "if statement reading a text file"
date: 2011-03-31
forum: Programming Talk
---

### Post by bcooperizcool on 2011-03-31
How can I read a text file and check if a block of text exists, and then set a variable using that?
```
while read theme; do
           cat /home/ubuntu/file | if [[ "<key>$theme</key>
                                          <true/>" ]]; then code to set variable $theme to a constant variable;
 else echo "Sad";
fi
done < /home/ubuntu/theme_list.txt 
```
where the file is the file that needs to be checked for a block of text, the theme_list.txt is just a line-by-line list of name, E.G Theme1, Theme2, etc, and I don't know the code for setting the $theme variable to a constant variable able to be used throughout the script when it finds a matching block of text.

The contents of file are similar to:
```
<key>Theme1</key>
      <true/>
      <key>Theme2</key>
      <false/>
      <key>Theme3</key>
      <false/>
```

Any ideas?  I know my script doesn't work, I would like help in getting it to work :)

Thanks

---

### Post by Thund3rstruck on 2011-03-31
I'm not sure if I totally understand the requirement but here's some quick code I wrote to test this. 

It assumes an xml document: theme_list.xml
```

<key>Theme1</key>
<true/>
<key>Theme2</key>
<false/>
<key>Theme3</key>
<false/>

```

It assumes a text file: theme_list.txt
```

Theme1
Theme2
Theme3

```

```

#!/bin/bash
var=( )
while IFS= read -r line
do
  if [ $(cat "theme_list.xml" | grep -c "$line") -gt "0" ]; then
	printf "%s\n" "$line found in theme_list.xml"
	var+=( "$line" )
  fi
done < theme_list.txt
printf "%s\n" "${var[@]}"

```

The script reads each line of theme_list.txt and searches theme_list.xml to see if it exists or not. If it does then that value is added to global array. 

The output looks like this:
```

[neal.bailey@ACER3000Fedora ~]$ ./theme.sh 
Theme1 found in theme_list.xml
Theme2 found in theme_list.xml
Theme3 found in theme_list.xml
Theme1
Theme2
Theme3

```

---

### Post by bcooperizcool on 2011-03-31
Thanks for the reply!  I'll try that out now.

It's actually for an iPhone, and this is the preference file that has the options answers.
I have no idea how to make a GUI, and no one answered my plist questions, so this is as far as I have got on my own. 
I made a shell script to generate a plist for the settings app, and then it creates the preference file which I am trying to read what the choices are with another shell script, to get the name of the theme selected.

Just so you have an idea of what I'm trying to do.

---

### Post by bcooperizcool on 2011-03-31
No, it didn't work for what I needed :(
I need it to look for a whole block of text (two lines to be exact).

Hmmmmmmmm........

---

### Post by lloyd_b on 2011-03-31
First off, let me state some assumptions (sorry, but you aren't completely clear on some things).

1.  The file "/home/ubuntu/file" contains XML data, containing pairs of "key" and "value" (<key>Theme1</key> and <true/> or <false/> for that particular key.

2.  One and only one key will be set to true.

3.  You need to identify which of the themes is currently set to true.

If this is the case, there's no reason to even look at "themes_list.txt", since any value in it that does not exist in "file" cannot possibly be true.

Here's a script that I think will do what you want.  Note that I bypass the issues with local/global variables by the simple expedient of storing the contents of "file" in a variable, and then processing that variable.  Be advised - those are "backtics" (above the <tab> key on US keyboards) around that 'cat' command on line 3, not single quotes - makes a major difference in bash.

```
#!/bin/bash

DATAFILE=`cat /home/ubuntu/file`
SELECTED_THEME="none"
CURRENT_THEME="none"

# Process the data file one line at a time
for LINE in $DATAFILE; do
   # First, trim off any leading whitespace.
   LINE2=${LINE%%<}
   # Now see if this is a key
   if [ "${LINE2:0:5}" == "<key>" ]; then
      # Got a key line
      # Need to trim off the XML tags
      LINE3=${LINE2#<key>}
      LINE3=${LINE3%</key>}
      CURRENT_THEME=$LINE3
      echo "Handling theme $LINE3"
   elif [ "$LINE2" == "<true/>" ]; then
      # We got a true - set SELECTED_THEME to whatever CURRENT_THEME is
      echo "Theme $CURRENT_THEME is true!"
      SELECTED_THEME=$CURRENT_THEME
   elif [ "$LINE2" == "<false/>" ]; then
      # Don't really need to test for this - just a place for some
      # debugging echoes if needed
      echo "Theme $CURRENT_THEME is false"
   else
      # Got a line we can't identify - shouldn't happen
      echo "Unrecognized line ->$LINE<-"
   fi
done

echo "Currently selected theme is $SELECTED_THEME"
```

This should give you something to start with - it gets the "true" theme into the variable SELECTED_THEME, which you can use for whatever you want.

Lloyd B.

---

### Post by kurum! on 2011-03-31
> **lloyd_b said:**
> 

```
#!/bin/bash

DATAFILE=`cat /home/ubuntu/file`

```

```

DATAFILE=$(</home/ubuntu/file)

```no need to call external cat

---

### Post by lloyd_b on 2011-04-01
> **kurum! said:**
> ```

DATAFILE=$(</home/ubuntu/file)

```no need to call external cat

Cool - haven't seen that construct before.  Thanks for the new trick to add to my collection. :)

Lloyd B.

---

### Post by Thund3rstruck on 2011-04-01
Sorry I mis-understood the requirement. 

I'm fairly new to *"scripting"* (I'm coming from the OOP world) and I don't know if bash supports a native key/value pairs construct (IDictionary or similar IFace) but if you control that XML document then you could add the boolean and value as XMLAttributes instead of a nested key heirarchy. 

```

<key enabled="true" value="Theme1" />

```

That would be much cleaner since you could use egrep to match a regular expression.

As it stands now, Lloyd's solution will certainly get 'er done! :)

---

### Post by bcooperizcool on 2011-04-01
Thank you ver much for your helpful replys!    Yes, I tried out Lloyd's, and that works great, even if I don't entirely understand what he did ;P. I'll play around with it and figure it out.

I'm new to bash scripting as well, seeing as I have a lot to learn. :P

thank you again!   :D

---

