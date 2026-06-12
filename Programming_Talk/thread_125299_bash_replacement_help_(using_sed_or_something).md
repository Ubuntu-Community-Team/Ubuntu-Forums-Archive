---
title: "bash replacement help (using sed or something)"
date: 2006-02-03
forum: Programming Talk
---

### Post by jaykup on 2006-02-03
I have a large text file with entries like this

/home/user/new/image.jpg
/home/user/new2/image.jpg
/home/user/new3/image.jpg
/home/user/weird/image.jpg
/home/user/stuff/image.jpg
/home/user/more/image.jpg

How can I change "image" to whats inbetween user and image?

I'm not looking to rename files, just edit the text file

I have no idea how you would do that with sed since its different each time, and I'm not sure where else to look.

---

### Post by rydow on 2006-02-03
cat slask | awk  'BEGIN{FS = "/"}{printf "/"$2"/"$3"/"$4".jpg\n"}' >slask2

would work (if slask is your original file and slask2 the result)
and this would do about the same with sed:

cat slask | sed 's:/home/user/\(.*\)/image\(.jpg\):\1\2:g'

Cheers
/Jonas

---

### Post by rydow on 2006-02-03
Sorry the second one should be:
 cat slask | sed 's:\(.*\)/image\(.jpg\):\1\2:g' > slask2

---

### Post by jerome bettis on 2006-02-03
awk is so much more readable and writeable than sed.  does sed's steep learning curve make it anymore powerful than awk??   i'm wondering if it's worth learning that quirky syntax (i'm familar with reg exps, +*. all that stuff) but everytime i see someone type sed code it just looks so wacky, and awk is kinda like C.

---

### Post by jaykup on 2006-02-04
Yeah, sed is a weird context

An easier way to look at a command like

sed 's/\/home\/usr/\/home\/new/'
is
sed 's|/home/usr|/home/new|'

Just replace the / with | and it elimates the need for all those back slashes

and other than that its all just regular expressions

sed seems to work better for me when i want to replace things, but then again I really don't know awk at all.

---

### Post by slavik on 2006-02-04
awk and sed are used for different things though.

sed is a text editor (search for some text and replace it), awk is a text processor (find something relavant and do something else).

---

### Post by jerome bettis on 2006-02-04
^ generally yes, but you can use gsub() in awk to do the same thing as you would in sed.  right?

---

