---
title: "&quot;replace text&quot; function i unknown langage... help"
date: 2005-11-18
forum: Programming Talk
---

### Post by otey on 2005-11-18
Hi.. 
Im no skilled programmer.. only do PHP and a tiny bit of java-script, so i was wondering if anybody would help me out at this

This code is from my .abcde.conf file, and it is surpose to do something like transformig **spaces** and **/ ** to underscores and some other stuff..

The conf-files description is this:
```
# Custom filename munging:
# By default, abcde will do the following to CDDB data to get a useful
# filename:
# * Translate colons to a space and a dash for Windows compatibility
# * Eat control characters, single quotes, and question marks
# * Translate spaces and forward slashes to underscores
# * Translate stars into pluses.
# To change that, redefine the mungefilename function.
# mungefilename recieves the CDDB data (artist, track, title, whatever)
# as $1 and outputs it on stdout.
#mungefilename ()
#{
#echo "$@" | sed s,:,\ -,g | tr \ /\* __+ | tr -d \'\"\?\[:cntrl:\]
#}
```

What language is this?
Were can i learn to understand this function? 

I would be very happy if someone could explane this to me, and maybe give me an example where the spaces are _not_ converted to underscores, and the slashes are converted to "-" instead of underscores.

---

### Post by frodon on 2005-11-18
You need to learn what are regular expressions : [http://www.comp.lancs.ac.uk/computing/users/eiamjw/unix/chap10.html](http://www.comp.lancs.ac.uk/computing/users/eiamjw/unix/chap10.html)

So to conver spaces and / to underscore the corresponding sed command is :  ```
sed "s/[ /]/_/g" input_file > output_file
```"s" mean substitute, in the "[]" is the list of the characters you want to match (here space and /), _ is the character used for replacement and g tell sed to do it each time it meet a matching character.
the sintax of sed for replacement is : ```
sed "s/PATTERN_TO_MATCH/PATTERN_TO_SUBSTITUTE/g" inputfile > outputfile
```

---

