---
title: "Bash script, request for comments"
date: 2013-02-02
forum: Programming Talk
---

### Post by catlover2 on 2013-02-02
I just found [this](http://www.tldp.org/LDP/abs/html/index.html) guide and an idea for a script to match it, so I created my first real (*i.e.* not just a list of commands) bash script. I'm posting it here so some more experienced eyes can have a look at it and hopefully give suggestions for improvement. It does seem to work for its intended purpose at the moment.

[php]
#!/bin/bash

TEMPLATE=template/overlay.png
IMG=label.gif
BIMG=label.gif.bak
PIMG=out-1.png

# IMGDIR=/home/username/some/fixed/directory
read -p "Enter the full path to your source directory: " IMGDIR
read -p "You entered $IMGDIR. Is this correct? (y/n) " YN

mergeimages ()
{
echo "Merging template with label..."
cp $IMGDIR/$IMG $IMGDIR/$IMG.bak
convert -coalesce $IMGDIR/$IMG $IMGDIR/$TEMPLATE $IMGDIR/out.png
rm $IMGDIR/out-0.png
mogrify -crop 813x1274+51+0 $IMGDIR/$PIMG
mogrify -rotate "180<" $IMGDIR/$PIMG
}

printlabel ()
{
echo "Printing label..."
lp -o media=Photo4x6.FB $IMGDIR/$PIMG
}

cleanup ()
{
echo "Cleaning up..."
rm $IMGDIR/$IMG $IMGDIR/$BIMG $IMGDIR/$PIMG
}

if  [ $YN = y ]
then
        mergeimages
else
        echo "Please re-run this script."
        exit 1
fi

read -p "Printable label saved to $IMGDIR/out-1.png. Ready to print? (y/n) " YN

if [ $YN = y ]
then
        printlabel
fi

read -p "Would you like me to clean $IMGDIR of $IMG, $BIMG, and $PIMG?  (y/n) " YN

if [ $YN = y ]
then
        cleanup
fi

echo "Script successful!"
exit 0
[/php]
-catlover2

---

### Post by greenpeace on 2013-02-02
Hey!  Congratulations!

Though, it's always good to let the board know what exactly it's intended purpose is... otherwise it's very difficult to evaluate!  :)

---

### Post by sisco311 on 2013-02-02
Check out the links in my signature.

By convention, environment variables (PATH, EDITOR, ...) and internal shell variables (RANDOM, BASH_VERSION) are fully capitalized. All other variable names should be lower case (or at least contain one or more lowercase letters). This convention avoids accidentally overriding environmental and internal variables.

You should double quote every expansion an anything that could possible contain a special character; e.g. "$img", "$yn", "${array[@]}", "$(comamnd)"
See:   
[http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments) 
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
and once again
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by catlover2 on 2013-02-02
> **greenpeace said:**
> Hey!  Congratulations!

Though, it's always good to let the board know what exactly it's intended purpose is... otherwise it's very difficult to evaluate!  :)
It takes two partially transparent 914x1397 images, merges and crops them, and optionally prints the result.

> **sisco311 said:**
> Check out the links in my signature.

By convention, environment variables (PATH, EDITOR, ...) and internal shell variables (RANDOM, BASH_VERSION) are fully capitalized. All other variable names should be lower case (or at least contain one or more lowercase letters). This convention avoids accidentally overriding environmental and internal variables.

You should double quote every expansion an anything that could possible contain a special character; e.g. "$img", "$yn", "${array[@]}", "$(comamnd)"
See:   
[http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments) 
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
and once again
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)The BashPitfalls page (and all the others, too) is very nice, thanks for pointing that out!

---

