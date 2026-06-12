---
title: "Could I have a bash script open multiple files when I click on one?"
date: 2008-03-09
forum: Programming Talk
---

### Post by Gen2ly on 2008-03-09
Hello all.

I just learned about feh, and I think it's a great image viewer.  I am hoping to be able to incorporate feh into my desktop.  Feh does have the ability to browse through images.   If I select feh as my default viewer in Gnome, click on the image, it opens images be in a single viewmode - I am unable to browse to images in the same directory..  So I wrote a bash script,

```
#!/bin/bash
feh *.png
```

pointed Gnome to it, to noavail.  I know this is pretty basic but I don't have a clue on what I need to have this work.  Can anyone think of a way I can browse with feh?

---

### Post by Acglaphotis on 2008-03-09
Quick solution in python:

[php]
import os

files = os.listdir("path here")
for x in files:
    os.system("feh " + x)
[/php]

I think thats what you want it to do? Open multiple instances of feh with all the images in a specific directory?

---

### Post by Gen2ly on 2008-03-09
No, actually this would be just one instance.  Feh allows browsing by right and left arrows if multiple images are opened:

```
feh desktop#1.png desktop#2.png
feh *.png
```

If only one image is picked then browsing is not available.  So I'm looking for a script that feh will be aware of other image files in the directory when double-clicking on say desktop#1.png.

---

### Post by Acglaphotis on 2008-03-09
I got into a bit of an issue when trying to solve this. When you call a program from nautilus it doesn't give you back its full path which i was going to use to scan for more images. Any ideas?

---

### Post by mssever on 2008-03-09
Here's an untested workup in Ruby:

```

#!/usr/bin/env ruby

files = Dir.entries(File.split(ARGV[0])[0])
`feh #{files[2..-1].join ' '}`
```

---

### Post by Gen2ly on 2008-03-09
Ah awesome!  I'm looking for to trying this when I get a chance later tonight.

---

### Post by Acglaphotis on 2008-03-09
The ruby one doesn't work for me : \

---

### Post by mssever on 2008-03-10
It appears that Nautilus passes the interesting information via environment variables, not commant line arguments. Here's a test script that displays the environment and arguments given to it: ```
#!/bin/bash

zenity --info --title=Environment --text="$(env)"
zenity --info --title="Command Line Arguments" --text="$*"
```This code works for me:
```
#!/usr/bin/env ruby

# Get the currently-selected files as an array
files = ENV['NAUTILUS_SELECTED_FILE_PATHS'].to_s.chomp.split "\n"

if files.length >= 1
  # One or more files must be selected
  `feh #{files.join ' '}`
else
  # no files are selected
  `feh #{ENV['NAUTILUS_SCRIPT_CURRENT_URI'].gsub(/^[^:]+:\/\/(.*)/, '\1')}`
end
```This will call feh with the selected files. If no files are selected, it will call feh with the selected directory.

---

### Post by Gen2ly on 2008-03-10
Appreciate the coding guys - cool stuff.  I just put ruby on my pc, so I hope I did it right.  :)  I chmodded the script, and put it in /usr/bin and in the "Open With" dialog choose it.  I double click it and got a spike in the cpu but thats all.  I ran the script from the command line and got this but I probably not helpful:

```
./usr/bin/feh-browser:4: private method `chomp' called for nil:NilClass (NoMethodError)
```

---

### Post by mssever on 2008-03-10
> **Dirk.R.Gently said:**
> I ran the script from the command line and got this but I probably not helpful
Actually, you did just the right thing. Running from the command line lets you see errors, and posting errors allows people to debug them. (Command line note: Because Nautilus sets environment variables, you'll need to manually set them in order to test the script from the command line.

I edited my post above to fix precisely that error. Probably you missed my edit. (By the way, you can write this in any language. I used Ruby because it's my personal favorite.

One other thing: Nautilus scripts belong in ~/.gnome2/nautilus-scripts, not /usr/bin.

---

### Post by ghostdog74 on 2008-03-10
how about checking out the feh documentation and see if there are any options that enable you to view many files? -r option perhaps?
```

feh -r /dir_of_photos

```

---

### Post by mssever on 2008-03-10
> **ghostdog74 said:**
> how about checking out the feh documentation and see if there are any options that enable you to view many files? -r option perhaps?
```

feh -r /dir_of_photos

```

If you give feh a directory on the command line, then feh recursively cycles through all images by default.

---

### Post by ghostdog74 on 2008-03-10
> **mssever said:**
> If you give feh a directory on the command line, then feh recursively cycles through all images by default.

yes, i know... its just that if this can be done, then maybe OP can try experimenting with the various options. sometimes, it makes things easier...furthermore, one way , if not the best way, is OP could have just copy all .png files into one directory and view all *.png from there .. using that syntax..

---

### Post by Gen2ly on 2008-03-10
know, this is pretty clever.  I have been going with the approach of creating a small program that would redirect gnome to select the directory rather than the file - possilby not possible.  A nautilus scriptthough, works good.  Alot people I talk to really like programming with rails saying it's one of the more visceral languages out there.

Appreciate the help msserver, this will make using my desktop alot better!

:guitar:

---

### Post by mssever on 2008-03-10
> **Dirk.R.Gently said:**
> Alot people I talk to really like programming with rails saying it's one of the more visceral languages out there.
Note that the code I wrote is pure Ruby, not Rails. I've actually never successfully used Rails, but I like Ruby.

---

