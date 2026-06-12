---
title: "[SOLVED] Help a beginner making a script to convert m3u playlists from windows to lin"
date: 2009-01-08
forum: Programming Talk
---

### Post by mnemonik on 2009-01-08
Hi!

I am trying to create a script to convert my playlist files that I have on XP to a format that would be readable in Ubuntu. My computer dual boots xp and ubuntu so I thought this would be a good project to help me learn to use python and also because I want to be able to use these m3u files in ubuntu! All my music files are on an external hard drive so they have the same file structure in xp and ubuntu except for the very start. Here is a small m3u playlist I have been using to test my script on:

```
#EXTM3U

#EXTINF:312,Pete Rock - Mary J Blige - Reminisce (remix)

G:\Music\Pete Rock\Invented The Remix\10 - Pete Rock - Mary J Blige - Reminisce (remix).mp3

#EXTINF:231,Grand Puba - Back It Up

G:\Music\Grand Puba\Reel To Reel\Back It Up.mp3

#EXTINF:260,Brand Nubian - Try To Do Me

G:\Music\Brand Nubian\All For One\Brand Nubian - 11 - Try To Do Me.mp3

#EXTINF:303,Brand Nubian - Slow Down

G:\Music\Brand Nubian\All For One\Brand Nubian - 10 - Slow Down.mp3

#EXTINF:243,M.I.A. - Paper Planes (Scottie B. Remix)

G:\Music\MIA\Paper Planes Homeland Security Remixes\05 - M.I.A. - Paper Planes (Scottie B. Remix).mp3

```

So from what I gather I need to do two things:
1. turn "G:" in to "/media/My Book"
2 turn "\" in to "/" (I am not sure, as I have only been running ubuntu for a month but isn't "\" just the ignore next character command? would this matter at all?)

I wrote the part to change "\" in to "/" because I am not sure how to do the other part (suggestions? I have been scouring "A Non-Programmer's Tutorial For Python", my main resource, for a hint but no luck so far) but so far even this first task isn't working. Here is waht I have so far:

[PHP]#ask for playlist filename to convert
inList = raw_input("Type the playlist filename here: ")

#import file
in_file = open(inList, "r")
contents = in_file.read()
in_file.close()

#change "\" to "/"
for char in contents:
	if char == "\\":
		char = "/"
	print char,

#change "G:" to "/media/My Book/"


#ask for output filename
outList = raw_input("Save playlist as filename: ")

#export file
out_file = open(outList, "w")
out_file.write(contents)
out_file.close()[/PHP]

When I put my test.m3u file in, it prints in the console how I want the file to change, but comes out the other side the exact same as it was! All help is appreciated. Thanks.

---

### Post by wmcbrine on 2009-01-08
You want the replace() method of a string:

```
contents = contents.replace('\\', '/').replace('G:', '/media/My Book')
```

or something like that.

Your current code isn't modifying "contents" at all, just printing it out.

---

### Post by ghostdog74 on 2009-01-08
here's a one liner
```

awk -F"\\" '/G:/{sub("G:","/media/My book");$1=$1}1' OFS="/" file.m3u > newlist

```

---

### Post by mnemonik on 2009-01-08
> **wmcbrine said:**
> You want the replace() method of a string:

contents = contents.replace('\\', '/').replace('G:', '/media/My Book')

or something like that.

THANK YOU! I put that line in and it worked perfectly!

I feel that I understand the syntax and basic stuff about python, but I don't know where to go to learn about these built in functions. I feel half the stuff I am trying to create and taking hours on are already at my disposal. Where do I go to find these things?

---

### Post by Bachstelze on 2009-01-08
Here it will be better to process each line separately:

[PHP]#ask for playlist filename to convert
inList = raw_input("Type the playlist filename here: ")
outList = raw_input("Save playlist as filename: ")

#open files
in_file = open(inList, "r")
out_file = open(outList, "w")

#Dump all the lines of the input file in a list
lines = in_file.readlines()
in_file.close()

for line in lines :

        #If the line doesn't start with "G", we just write it to the output file and move on to the next one.
        if line[0] != "G" :
                out_file.write(line)
                continue

        #Replace all occurences of '\' with '/'
        line = line.replace('\\', '/')

        #Discard the first two characters
        line = line[2:]

        #Prepend '/media/My Book'
        line = '/media/My Book' + line

        #One-liner for the three operations above:
        #line = '/media/My Book' + line[2:].replace('\\', '/')

        #Write the line
        out_file.write(line)

out_file.close()
[/PHP]

---

### Post by Bachstelze on 2009-01-08
> **mnemonik said:**
> I feel that I understand the syntax and basic stuff about python, but I don't know where to go to learn about these built in functions. I feel half the stuff I am trying to create and taking hours on are already at my disposal. Where do I go to find these things?

The book *Python in a nutshell* is an excellent reference.

And of course, wmcbrine's approach is better than mine. :p Oh well, I guess at least you learned about list subsets with mine. :D

---

### Post by mnemonik on 2009-01-08
> **HymnToLife said:**
> The book *Python in a nutshell* is an excellent reference.

And of course, wmcbrine's approach is better than mine. :p Oh well, I guess at least you learned about list subsets with mine. :D

Why is it better? Yours was shorter and easier for me to understand. This is not to belittle wmcbrine's approach, I am genuinely interested.

---

### Post by wmcbrine on 2009-01-08
[quote=mnemonik]I feel half the stuff I am trying to create and taking hours on are already at my disposal. Where do I go to find these things?[/quote]

There's lots of help available in the interactive interpreter, and lots of help online. In this case, you might try:

```
help(str)
```

from an interactive session, or "python string methods" in Google.

---

### Post by Bachstelze on 2009-01-08
> **mnemonik said:**
> Why is it better? Yours was shorter and easier for me to understand. This is not to belittle wmcbrine's approach, I am genuinely interested.

On second thought, maybe it is indeed better to use string subsets to just discard the first two characters of the line, since you know the "G:"'s don't appear anywhere else (i.e. you don't search the whole line for occurrences of "G:" when you know there is only one).

---

### Post by eye208 on 2009-01-08
> **ghostdog74 said:**
> here's a one liner
```

awk -F"\\" '/G:/{sub("G:","/media/My book");$1=$1}1' OFS="/" file.m3u > newlist

```
Here's a *short* one-liner. ;)
```
sed -e "s/\\\/\//g;s/G:/\/media\/My Book/" file.m3u > newlist
```

---

