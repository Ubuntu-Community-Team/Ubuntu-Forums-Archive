---
title: "change font size"
date: 2009-01-14
forum: Programming Talk
---

### Post by davidtuti on 2009-01-14
Hi,
I would like to change the font size in bash. I know how do it:


string="xxxx yyy xxx zzzzZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ lllllllllllllllllllzzzzzzzyy dslfjskdf sksksk sdfsdf sd 324234234 x.x.x.x.sdfjslfs 24 234l232423423 xxxxxxxxxxxxxxxyyyy yyyyyyyyyyyyyyy"
F_VDOBLE="\033#6"
printf "${F_VDOBLE}$string"

The problem that I have is that this command only puts the first line with wide font, the next lines have normal font. What can I do to put all the text with wide font if the string have more of one line?

Any help?

Many thanks

---

### Post by SeanHodges on 2009-01-15
I think this may be a terminal-specific problem, the easiest way might be to handle the wrapping yourself:

```
string="xxxx yyy xxx zzzzZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ lllllllllllllllllllzzzzzzzyy dslfjskdf sksksk sdfsdf sd 324234234 x.x.x.x.sdfjslfs 24 234l232423423 xxxxxxxxxxxxxxxyyyy yyyyyyyyyyyyyyy"
F_VDOBLE="\033#6"

# half the wrap width because you are making the characters twice as wide
let wrapwidth=$(tput cols)/2 
if [[ "$wrapwidth" -eq "" ]]
then
	# Force the wrap width if the calculation fails
	wrapwidth=80
fi

stringbuffer=$string
while [ ${#stringbuffer} -gt 0 ]
do
	# Extract a line of the string to draw
	part=${stringbuffer:0:$wrapwidth}

	# Draw line with control character
	printf "${F_VDOBLE}$part\n"

	# Delete the line from the string
	stringbuffer=${stringbuffer:$wrapwidth:${#stringbuffer}}
done
```

Just a warning though, I was able to reproduce your problem in xterm, but gnome-terminal completely ignores the control character and renders the string in the normal font regardless. This is probably something to do with GTK and font management, but just so you know that your "F_VDOBLE" method will not always work.

---

### Post by davidtuti on 2009-01-16
Many thanks ... It works!
I did other solution but my solution it's not so sofisticated like this.

---

