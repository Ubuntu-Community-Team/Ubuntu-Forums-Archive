---
title: "#!/bin/bash"
date: 2014-09-01
forum: Programming Talk
---

### Post by cathect2 on 2014-09-01
I'm trying to create a script and it requires copying a file from one location to the /home directory. For some reason, I'm unable to get copy to work. I think it has something to do with the fact that there are spaces in the directory names. Can anyone help? I get a "cannot stat" error when I run the script. Here is the relevant portion of the script:

```
 #!/bin/bash 


FILE="/home/cathect/Desktop/Office Briefcase/HSI Work/WorkRecord.md"
DESTINATION="/home/cathect/"


# Copy file to working directory.
cp $FILE $DESTINATION

....

```

---

### Post by Lars Noodén on 2014-09-01
You'll want to [wrap the variables in quotes](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target) in order to deal with the space in the names.  Otherwise, the shell will treat every word in the name separately.  

A wrong way to get around it would be to mess with the [internal field separator](http://tldp.org/LDP/abs/html/internalvariables.html#IFSREF), but that would cause more trouble than it fixes.  The correct way is to use [quotes](http://mywiki.wooledge.org/Quotes#Prevent_field_splitting_and_ignore_glob_pattern_characters) to prevent splitting.

---

### Post by cathect2 on 2014-09-01
Thanks for the help, Lars.

I thought I did that. Sorry, this is my first attempt to cobble together a script.

Do you mean like this:

> # Copy file to working directory.
cp "$FILE" "$DESTINATION"


---

### Post by Lars Noodén on 2014-09-01
It'll be second nature before long!

---

### Post by cathect2 on 2014-09-01
This doesn't work. It still can't find the file. However, the path is correct. I can cd into it using the same text.

---

### Post by Lars Noodén on 2014-09-01
What is the exact error message you are getting with the quotes?  What you wrote in #3 above should have done it and works for me in bash.

---

### Post by cathect2 on 2014-09-01
The script has two parts. I've tested the second part, it works fine if WorkRecord.md is copied to ~/. The problem happens here:

>  #!/bin/bash 


FILE="~/Desktop/Office Briefcase/HSI Work/WorkRecord.md"
DESTINATION="~/"


# Copy file to working directory.
cp "$FILE" "$DESTINATION"


echo "Preparing Work Report..."



After executing, I get this error:

> cp: cannot stat &#8216;~/Desktop/Office Briefcase/HSI Work/WorkRecord.md&#8217;: No such file or directory

Thanks again for helping this noob...

---

### Post by Lars Noodén on 2014-09-01
~ is not getting expanded.  I suspect because of the quotes.  You'll want to use a full absolute path or else substitute ~ for "$HOME".  

```

 FILE="${HOME}/Desktop/Office Briefcase/HSI Work/WorkRecord.md"

```

$HOME is one of the variables that gets set automatically.

---

### Post by Vaphell on 2014-09-01
yes, ~ is one of those things that don't work when wrapped in quotes and as Lars said, $HOME is its direct quote-friendly equivalent. Another example of such things would be glob wildcards ( "$dir/*" won't work because the shell doesn't "see" that *, on the other hand "$dir"/* will ) and ranges {x..y}
All these things are preprocessed by the shell - expanded to their true representation as the very first step before taking further action.
~ is substituted by the user's home, * expands to lists of matching files/dirs, {} is expanded to the full range. Then having proper values in place, commands are executed.

btw, try avoiding all caps names of variables. By convention all caps are used for environment settings and by accident you could override one. Shell won't complain and you can introduce subtle or not so subtle bugs. For example try using PATH variable for some meaningless crap in your script and see how that works... no external command will be found without full path because that's what PATH helps with.

---

### Post by cathect2 on 2014-09-01
FILE="${HOME}/Desktop/Office Briefcase/HSI Work/WorkRecord.md"
DESTINATION="${HOME}"

I've replaced FILE and DESTINATION with the above. But it still gives me the error message! Argh.

---

### Post by Vaphell on 2014-09-01
did you quote variables in cp call? unquoted vars undergo word splitting on spaces, so assuming file="a b c"; dest="d e f";
*cp $file $dest* becomes *cp 'a' 'b' 'c' 'd' 'e' 'f'*, not *cp 'a b c' 'd e f'*
*cp "$file" "$dest"* would properly yield *cp 'a b c' 'd e f'*

in your case cp would try to find 2 files and of course fail:
${HOME}/Desktop/Office
Briefcase/HSI Work/WorkRecord.md

---

### Post by cathect2 on 2014-09-01
Yes, I used this:

cp "$FILE" "$DESTINATION"

I'm **STUMPED**!

---

### Post by cscj01 on 2014-09-01
Try this:> FILE=/home/{your home directory}/Desktop/'Office Briefcase'/'HSI Work'/WorkRecord.mdLeave out the braces.

---

### Post by cathect2 on 2014-09-01
Like this?

> File=/home/larry/Desktop/'Office Briefcase'/'HSI Work'/WorkRecord.md
Destination=/home/larry/


Same error message

---

### Post by steeldriver on 2014-09-01
Can I suggest you copy/paste the ENTIRE script here so we can have a proper look at it, plus the actual command(s) you are using to run it? e.g.

```

$ cat myscript.sh
#!/bin/bash

file="$HOME/Desktop/some file"
dest="$HOME"

cp "$file" "$dest"

```

then (assuming you have made the script executable e.g. using 'chmod +x myscript.sh' or equivalent from the file manager)

```

$ ./myscript.sh
cp: cannot stat `/home/steeldriver/Desktop/some file': No such file or directory

```

---

### Post by cathect2 on 2014-09-01
It seems to have something to do with the spaces in the directory names. I just did a test by creating a set of nested folders without spaces in the names. This script works flawlessly:

> File=${HOME}/Desktop/Test/Work/WorkRecord.md
Destination=${HOME}




---

### Post by cathect2 on 2014-09-01
This is my entire script. This one functions as expected. However, when I try to use it on a folder with spaces in the name, it breaks with the error message described above.

>  #!/bin/bash 


File=${HOME}/Desktop/Test/Work/WorkRecord.md
Destination=${HOME}


# Copy file to working directory.
cp "$File" "$Destination"


echo "Preparing Work Report..."


# Pause
sleep 2s


echo "Deploying Pandoc ...."


pandoc -s -S --toc -c PanAm.css WorkRecord.md -o WorkRecord.html


# Pause to let Pandoc work.
sleep 3s


# Move the report to the Desktop.
mv WorkRecord.html ~/Desktop/




# Delete working file
echo "Cleaning Up......."


rm WorkRecord.md


echo "Report Complete."


---

### Post by steeldriver on 2014-09-01
... it would be more helpful to post the version that **doesn't** work

---

