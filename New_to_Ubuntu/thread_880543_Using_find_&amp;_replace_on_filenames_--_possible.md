---
title: "Using find &amp; replace on filenames -- possible?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Neureo on 2008-08-05
Hey, most of the directory names in my ~/music directory have spaces in them. Since that makes them harder to work with in the terminal, I've decided to try and change all the spaces to underscores. How would I go about doing this with the command line -- maybe with the sed utility? Thanks for your time!

---

### Post by whitethorn on 2008-08-05
> **Neureo said:**
> Hey, most of the directory names in my ~/music directory have spaces in them. Since that makes them harder to work with in the terminal, I've decided to try and change all the spaces to underscores. How would I go about doing this with the command line -- maybe with the sed utility? Thanks for your time!

Hi I had a problem similar to yours.  I found a way of changing spaces into underscores as a bash script.  
> 
#Change Space to Underscore
IFS=$'\n'
for f in `find .`; do
   file=$(echo $f | tr [:blank:] '_')
   [ -e $f ] && [ ! -e $file ] && mv "$f" $file
done
unset IFS


---

### Post by ad_267 on 2008-08-05
Also have a look at "man rename"

You could do something like:
```
rename "s/ /_/g" *
```

---

### Post by ghostdog74 on 2008-08-05
```

for i in ~/music/*; do mv "$i" "${i// /_}"; done

```

---

### Post by Neureo on 2008-08-05
Wow, thanks everyone! I ended up using this script -- 

> **ad_267 said:**
> Also have a look at "man rename"

You could do something like:
```
rename "s/ /_/g" *
```

-- and it worked brilliantly. Thanks again.

---

### Post by dcmjkamm on 2012-03-29
I used this after pulling a few hairs out of my skull.

Thank you all of you in this post and across the site! All of your answers are appreciated. You saved me so much mind numbing work that I thought was inevitable.

Thank you!

---

### Post by hakermania on 2012-03-30
> **ghostdog74 said:**
> ```

for i in ~/music/*; do mv "$i" "${i// /_}"; done

```
just wanted to add that a check if i is a folder is vital here, like:
```

if [ -d "$i" ]; then
   mv "$i" "${i// /_}"
fi

```

---

