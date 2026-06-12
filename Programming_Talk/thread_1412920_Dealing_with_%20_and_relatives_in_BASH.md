---
title: "Dealing with %20 and relatives in BASH"
date: 2010-02-21
forum: Programming Talk
---

### Post by jamesisin on 2010-02-21
I am working to write my first complicated script.  I am in the planning stage right now.  The script will parse information from Rhythmbox playlists and synk music between the library and my iPod with Rockbox.  Lofty, I suppose, but why not start tough?

I have noticed something that I would like to deal with systemically if possible.  There are characters in the playlists which are substituted by %## designations.  For example, the space character is shown as %20.  This is pretty standard, but what I am wondering is if there is a way to deal with any %## characters I am likely to encounter *en masse*.

I understand how to replace characters ok.  I would just rather avoid calling out %01, %02... %99 or how ever many would scope the whole range of possibilities.

Is there a way to make BASH understand "%20" (and its relatives) as "\ " (and its relatives)?  Or a way to parse these en masse with a small code snippet?

---

### Post by Simon17 on 2010-02-21
I don't think bash will be able to do this on its own. It'll be fairly easy to do a search-and-replace for each token on the entire string, but you're going to need to use another program such as awk to do it.

---

### Post by jamesisin on 2010-02-21
Yes, of course.  I'm not concerned with how to search for the string.  Nor with how to replace the string.  I am concerned with a compact way to *describe* the string.

Replacing any instance of %20 with " " is easy enough.  I just don't want to have to anticipate every possible %## substitution which might occur and include in the script a search/substitution algorithm for each one.

Perhaps I will have to specify each one, but I was hoping to find a more compact/efficient way to handle that.

---

### Post by Simon17 on 2010-02-21
The cleanest way I can think of right now would be to have two arrays- one with the escape sequences and one with the replacements and loop through them doing a S&R.

```

escapes=(%20 %24 ...)
replacements=("\ " "\\$" ...)
for ((i=0; i < ${#escapes[@]};i++))
do
  # replace escapes[$i] with replacements[$i]
done 

```

This will be reasonably compact and easy to add to escapes if necessary.

---

### Post by Some Penguin on 2010-02-21
It's hex.  20 (hex) = 32 (decimal).  And a space happens to be 32 in the ASCII set.

---

### Post by jamesisin on 2010-02-21
Simon17 - Thanks for the idea.  That will certainly be more compact than using a line of code for each replacement.

Some Penguin - Thanks for the heads-up.  How might I use this knowledge to create a more compact and streamlined replacement script?

---

### Post by Simon17 on 2010-02-22
Some Penguin, lawl. That was stupid. I don't know how that flew by me.

james, ignore what I said. You can pull out the numerical part of the escape and use it to find the ascii value.

There are a few ways to do this. One way is to replace the %NN with
```
`printf "\xNN"`
```

There is probably a better way but this should work.

---

### Post by jamesisin on 2010-02-22
A little slow here...

I think I get you.  I use the printf command to interpret the %## characters.  It will parse them as BASH recognizable characters.  Then take the output of the printf command as my new input?  Or should I be using this snippet within a replace snippet?

---

### Post by Simon17 on 2010-02-22
:)

Now that I think about it, the first thing I told you about the 2 arrays isn't so bad.

Using the ascii value is simpler in some ways, but it makes the parsing quite a bit more complicated. Off the top of my head, I can't think of a good way to do it.

You will have to do a little bit of typing, but I think what I told you first will end up being much cleaner in the end. Unless someone comes up with a good way, I go back to what I said earlier.

Sorry to flip-flop like that.

---

### Post by jamesisin on 2010-02-22
Sensible enough.

Now I just need to figure out *which* characters I need to worry about.  Currently the music is on a Samba share, so I guess I could look for a list of valid Samba characters and compare that to a list of valid Web characters to see which characters don't appear in both lists?

So far: " " %20, [] %5B and D, accented characters (quite a few but I don't know them), others (&).

Any idea how I might go about setting up such a comparison?

---

### Post by Reiger on 2010-02-22
Well to my knowledge BASH understands Hex escape sequences just fine: \x20 will work in e.g. a printf statement. So something like this:

```

printf $(echo 'hello%20world%21%0A' | sed 's!%!\\x!g')

```

Ought to work just fine. (Should print 'hello world!' with newline.)

---

### Post by jamesisin on 2010-02-22
Ah, I think I see the course.

I could set up a for loop to parse each file/path/name.flac through echo and that will replace those pesky characters.

Or will I have to send echo also through printf?

Basically I'm parsing data from an xml file ( /home/$USER/.gnome2/rhythmbox/playlists.xml ).  The files are stored there as such:

```
<playlist name="_0_0_RockBox1" type="static">
   <location>smb://server/share/Jay%20Farrar%20and%20Benjamin%20Gibbard/One%20Fast%20Move%20or%20Im%20Gone%20music%20from%20Kerouacs%20Big%20Sur/01%20-%20California%20Zephyr.flac</location>
```

---

### Post by jamesisin on 2010-02-22
Grrr...

I'm noticing that the xml also includes & characters (like &amp; instead of the ampersand).  Damn it.  I'll have to figure out a way to deal with those as well.

---

### Post by Reiger on 2010-02-22
If you are willing you can use XSLT to extract the data strings you want and dump it to plain text (this still leaves those %xx characters but sed can take care of that), thereby getting rid of the XML entities (&amp; etc.). More ambitiously you could dynamically generate the appropriate scripts from the XML, so you merely have to pipe the output to sh.

You can use xsltproc (package in the repositories) to run an XSLT stylesheet against an XML document and specify output file.

This fairly simple thing will dump the location contents of such an XML file as newline separated plain text list:
```

<xsl:transform version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <!-- require the XSLT processor to output plain text (instead of XML or HTML -->
  <xsl:output method="text"/>
  <!-- 
    - local-name() takes care of any XML namespaces that may exist in the file: 
    - any <location>some_data</location> entry is matched by //*[local-name()='location']
    - and its some_data text is dumped as newline ('&#x0A;') delimited text via concat() and the value-of element  
    - for the normalize-space() function see: http://www.zvon.org/xxl/XSLTreference/Output/function_normalize-space.html  
   -->
  <xsl:template match="//*[local-name() = 'location']">
    <xsl:value-of select="concat(normalize-space(text()),'&#x0A;'"/>
  </xsl:template>
</xsl:transform>

```

---

### Post by jamesisin on 2010-02-23
> **Reiger said:**
> You can use xsltproc (package in the repositories) to run an XSLT stylesheet against an XML document and specify output file.

I like the possibility and will keep this one in mind.  I am seeking to keep this script portable and will seek out solutions (where possible) that don't involve introducing dependencies.  Hopefully I can find a more native solution.

I am going to explore your sed option above.  That substitution does clean the characters for BASH.

---

