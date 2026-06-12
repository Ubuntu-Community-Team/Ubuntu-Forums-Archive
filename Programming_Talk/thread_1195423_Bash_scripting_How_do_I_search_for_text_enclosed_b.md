---
title: "Bash scripting: How do I search for text enclosed by parenthesis and rename?"
date: 2009-06-23
forum: Programming Talk
---

### Post by davidmigl on 2009-06-23
I have several folders, and somewhere in the folder name is a string enclosed in parenthesis. I want a script to remove that string from its original location, change the parenthesis to brackets, and put it at the front of the folder.

I want the following folders: ```
Led Zeppelin I (1969)
Led Zeppelin II (1969)
Led Zeppelin III (1970)
Led Zeppelin IV (1971)
Physical Graffiti (1975)
```

to be renamed like this:
```
[1969] Led Zeppelin I
[1969] Led Zeppelin II
[1970] Led Zeppelin III
[1971] Led Zeppelin IV
[1975] Physical Graffiti
```

How can I do this?

Thanks!

---

### Post by simeon87 on 2009-06-23
What have you tried yourself? Is something not working? This is not a write-a-script-for-me-service...

---

### Post by ghostdog74 on 2009-06-23
if you have Python, you can use my script called File renamer(see my sig last link), eg usage
```

# ls -1
Led Zeppelin I (1969)
Led Zeppelin II (1969)
Led Zeppelin III (1970)

# python filerenamer.py -p "^(.*) \((\d+)\)$" -e "[\\2] \\1" -l "*"
==>>>>  [ /home/Led Zeppelin II (1969) ]==>[ /home/[1969] Led Zeppelin II ]
==>>>>  [ /home/Led Zeppelin I (1969) ]==>[ /home/[1969] Led Zeppelin I ]
==>>>>  [ /home/Led Zeppelin III (1970) ]==>[ /home/[1970] Led Zeppelin III ]

```

remove the "-l" option to commit changes.

---

### Post by davidmigl on 2009-06-23
Well as far as bash goes, I have no idea how to search within a string enclosed in parenthesis. I tried grep (*) but that didn't work. If the year was at the start, I think I could try ```
 cut -d ) -f1
```. However it's not. Perhaps I could try sed to get a text file with the years and another one with the rest of the text and cat them together?

Otherwise I guess I'll just poke around the bash scripting guide hoping to find something of use.

Thanks for the python script, I will give that a try.

---

### Post by geirha on 2009-06-23
I'm fond of perl's prename command myself. In ubuntu it's called rename.
```
rename -n 's/(.*) *\(([0-9]+)\)$/[$2] $1/' *
```

The -n option will make it only print what it would've done, but not actually do it. Replace it with -v if the output looks right.

---

### Post by ghostdog74 on 2009-06-23
```

ls -1 | awk 'BEGIN{ q="\047" }
{
  s=""
  for(i=1;i<NF;i++){ s=s" "$i }
  gsub(/\(|\)/,"",$NF)
  newname = "["$NF"]" s  
  cmd="mv "q $0 q" "q newname q 
  print cmd 
  #system(cmd) #uncomment to use
}' 

```

---

### Post by stroyan on 2009-06-23
You could do that with bash with "%" and "##" parameter expansion.
They will remove trailing or leading patterns from a shell variable.
```

for D in *\(*\); do
 N=${D%(*}; Y=${D##*\(}; Y=${Y%)}; echo mv "$A" "[$Y] $N"
done

```
The use of "##" instead of "#" will skip past any additional "(" characters before one directly in front of the year.

---

### Post by davidmigl on 2009-06-24
Thank you - all of those scripts worked, they just got the job done in a different way. I'll try to learn from your examples; although I have a long way to go since I just started. There is plenty of material though!

---

### Post by kaibob on 2009-06-24
> **davidmigl said:**
> Thank you - all of those scripts worked, they just got the job done in a different way. I'll try to learn from your examples; although I have a long way to go since I just started. There is plenty of material though!
I always enjoy threads such as this because they are a great way to learn. I tried on my own to get things to work with the rename command but couldn't. I now understand geirha's solution and have copied it to my library so I'll have it when needed.

---

