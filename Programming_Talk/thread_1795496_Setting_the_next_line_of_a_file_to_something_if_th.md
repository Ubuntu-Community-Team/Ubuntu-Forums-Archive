---
title: "Setting the next line of a file to something if the above is something"
date: 2011-07-02
forum: Programming Talk
---

### Post by bcooperizcool on 2011-07-02
I am trying to get a variable set to the next line if the line above matches the criteria, as I know what the line above is, but not the line below.

So, the example of some contents of the file:
```
		<key>CFBundleDisplayName</key>
		<string>Dismount</string>
```

I know what CFBundleDisplayName is, but not the next line down (Dismount).
The next line (Dismount), is what I want to set to a variable (not the <string> and </string> in it though)

I have spent about an hour messing around with this code to try and read it right (I will probably change the variable names :P)
```
plutil -convert xml1 /Applications/Preferences.app/Info.plist
THEMEFILE=$(</Applications/Preferences.app/Info.plist)
theme="none"

for LINE in $THEMEFILE; do
    #Trim off whitespaces
    LINE2=${LINE%%<}
	LINE3=${LINE2#<key>}
    LINE3=${LINE3%</key>}

    #Now see if this is a key
    if [ "$LINE2:0:5" == "<string>" ]; then
       #Got a key line
       #Need to trim off the XML tags
	    LINE4=${LINE2#<string>}
        LINE4=${LINE4%</string>}
       theme=$LINE4;

	   
    elif [ "$LINE3" == "CFBundleDisplayName" ]; then 
#Found a true line, setting the variable $command to it :)
       echo "FOUND IT"
 fi
done
echo "$theme"
```

but alas, I don't know how it works, as this is code taken from an answer I have received before for a different question, and I just changed stuff around to try and get it working.  It succesfully reads the CFBundleDisplayName line, and knows it found it, I just don't know how to set the next line to the variable "$theme".    

Thank you :)

-Brian

---

### Post by Arndt on 2011-07-02
> **bcooperizcool said:**
> I am trying to get a variable set to the next line if the line above matches the criteria, as I know what the line above is, but not the line below.

So, the example of some contents of the file:
```
		<key>CFBundleDisplayName</key>
		<string>Dismount</string>
```

I know what CFBundleDisplayName is, but not the next line down (Dismount).
The next line (Dismount), is what I want to set to a variable (not the <string> and </string> in it though)

I have spent about an hour messing around with this code to try and read it right (I will probably change the variable names :P)
```
plutil -convert xml1 /Applications/Preferences.app/Info.plist
THEMEFILE=$(</Applications/Preferences.app/Info.plist)
theme="none"

for LINE in $THEMEFILE; do
    #Trim off whitespaces
    LINE2=${LINE%%<}
	LINE3=${LINE2#<key>}
    LINE3=${LINE3%</key>}

    #Now see if this is a key
    if [ "$LINE2:0:5" == "<string>" ]; then
       #Got a key line
       #Need to trim off the XML tags
	    LINE4=${LINE2#<string>}
        LINE4=${LINE4%</string>}
       theme=$LINE4;

	   
    elif [ "$LINE3" == "CFBundleDisplayName" ]; then 
#Found a true line, setting the variable $command to it :)
       echo "FOUND IT"
 fi
done
echo "$theme"
```

but alas, I don't know how it works, as this is code taken from an answer I have received before for a different question, and I just changed stuff around to try and get it working.  It succesfully reads the CFBundleDisplayName line, and knows it found it, I just don't know how to set the next line to the variable "$theme".    

Thank you :)

-Brian

Since the input is XML, and your question has a perfect formulation in terms of XML, I suggest you use XML routines. XPath, for example:

```
$ cat data.xml 
<data>
  <key>CFBundleDisplayName</key>
  <string>Dismount</string>
</data>
$ xpath -q -e '//*[preceding-sibling::key]/text()' data.xml 
Dismount
```

If you use XML a lot, XPath is worth learning.

---

### Post by Arndt on 2011-07-02
I actually didn't use the criterion you wanted. This is more likely to be what you want:

```
$ xpath -q -e '//*[preceding-sibling::key="CFBundleDisplayName"]/text()' data.xml 
Dismount

```

---

### Post by bcooperizcool on 2011-07-02
Actually, I got it working using something like this:
```
while read locations; do
plutil -convert xml1 $locations/Info.plist

line=`awk '/<key>CFBundleDisplayName<\/key>/{getline; print}' $locations/Info.plist | sed 's/<string>//; s/<\/string>//; s/ //;'`
echo "$line" >> "$base/displayname"
done < "$base/locations"
```

where locations is a list of stuff like /Applications/Preferences.app and so on

Except is comes out like
```
      Settings
```
instead of 
```
Settings
```

And that is messing up my other code with the name like that.

Any ideas on how to get rid of that?

xpath isn't for iPhone I don't think :/
(sorry, I should have mentioned that before)

---

### Post by bcooperizcool on 2011-07-02
Actually, never mind!  I got it working after a couple hours with no knowledge of how to :P

Thank you for your responses though!  :D

To those who might come venturing for this, I actually had misnamed the file in another command, so thats why it wasn't working for me.  The method I posted above works fine :)

---

### Post by Arndt on 2011-07-03
> **bcooperizcool said:**
> Actually, I got it working using something like this:
```
while read locations; do
plutil -convert xml1 $locations/Info.plist

line=`awk '/<key>CFBundleDisplayName<\/key>/{getline; print}' $locations/Info.plist | sed 's/<string>//; s/<\/string>//; s/ //;'`
echo "$line" >> "$base/displayname"
done < "$base/locations"
```

where locations is a list of stuff like /Applications/Preferences.app and so on

Except is comes out like
```
      Settings
```
instead of 
```
Settings
```

And that is messing up my other code with the name like that.

Any ideas on how to get rid of that?

xpath isn't for iPhone I don't think :/
(sorry, I should have mentioned that before)

If you have awk and stuff, you could have xpath, I suppose. It can't be very large. But in that case you may have to build it yourself.

As for the problem, I'm guessing, but does using

```
s/ //g
```

help? Without the g, it performs the replacement only once on each line.

---

