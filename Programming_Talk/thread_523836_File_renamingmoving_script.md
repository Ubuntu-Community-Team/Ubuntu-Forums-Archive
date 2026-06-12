---
title: "File renaming/moving script"
date: 2007-08-12
forum: Programming Talk
---

### Post by smbm on 2007-08-12
Hi

I need to move some album are pictures from their Rhythmbox store dir to their appropriate places in my music storage folders to be picked up by gtkpod for transfer to my iPod.

They are currently named Artist - Album Title.jpg and would need to go in folders called /Artist/Album Title.

I could do it manually fairly easily but it would be very time consuming. 

What I'm looking for is to write a script (probably in bash or python) to automate the process so when new music is added I can use Rhythmbox to get the art work and automatically move it to the right place.

Can someone give me nudge in the right direction? 

How do I turn the artist name and the album title into variables from the filename?

Thanks very much in advance.

P.s Is there anyone that can look over a package I've made (first attempt) to see if it meets acceptable guidelines for Universe?

---

### Post by snoop on 2007-08-12
If you are using python you can use the glob and os modules. Here is a small script that I used that would look for an extension and change the extension to another extension. The script is just quick and dirty, but it may help you along. 

```
import glob
import os

look_for_ext = raw_input("What is the extension to look for? (ex: *.jpg): ")
print "Looking for: ", look_for_ext

change_to_ext = raw_input("What is the extension to change it to? (ex: .png): ")
print "Changing to: ", change_to_ext

files = glob.glob(look_for_ext)
print "The files: ", files


go_ahead = raw_input("Go ahead? Type Y or N ")
print go_ahead
if go_ahead == "Y" or go_ahead == "y":
    go_ahead = True
else:
    go_ahead = False

#print go_ahead


if files != None:
    if go_ahead == True:
        print "True"
        
        for each in files:
            #print os.path.splitext(each)
            (basename,ext) = os.path.splitext(each)
            #print "Basename: ", basename
            #print "Extension: ", ext
            os.rename(each,basename+change_to_ext)
            print "Renamed ", each, " to ", basename+change_to_ext 
        

```

---

