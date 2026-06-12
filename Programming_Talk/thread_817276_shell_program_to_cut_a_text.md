---
title: "shell program to cut a text"
date: 2008-06-03
forum: Programming Talk
---

### Post by Green_Star on 2008-06-03
Hi all,

I need to cut a file name, for example i get files like following.

1. text1.text2.text3.text4.###
2. text1.text2.###
3. text1.text2.text3.###

All I want to do is to remove the last part (.###). Can some one suggest a shell program to do that?

Thanks in advance.

---

### Post by Martin Witte on 2008-06-03
use [pattern matching]("http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion")
```
#!/bin/bash
var1="1. text1.text2.text3.text4.###"
var2="2. text1.text2.###"
var3="3. text1.text2.text3.###"

echo ${var1%%.###}
echo ${var2%%.###}
echo ${var3%%.###}

```

---

### Post by Green_Star on 2008-06-03
thanks man, i think i didn't put my question properly.

I receive some files everyday, and names are like following

dgb.current.report.txt.011
mif.02022008.sales.txt.422
dunkin.001


I want to take out that last ".{three numbers}"
Or if I can remove last four characters that would be greate

---

### Post by Martin Witte on 2008-06-03
here you are
```
#!/bin/bash
var1="text1.text2.text3.text4.012"
var2="text1.text2.234"
var3="text1.text2.text3.236"

echo ${var1%%.[0-9][0-9][0-9]}
echo ${var2%%.[0-9][0-9][0-9]}
echo ${var3%%.[0-9][0-9][0-9]}

```

---

### Post by Green_Star on 2008-06-03
Thanks man, i will try as soon as I go home. by the way it is not going to delete the numeric numbers in the middle of the file name. another one i need to think is i get around 50 files a day, so i may need to write a loop script to avoide assigning var1 , var2 etc.

---

### Post by stroyan on 2008-06-03
Did you want to rename those files removing the trailing . and digits?
Then you could use this bash command.
```

for f in *.[[:digit:]][[:digit:]][[:digit:]];do mv "$f" "${f%.???}";done

```

---

### Post by HalPomeranz on 2008-06-03
Use the "rename" command:

```

rename 's/\.\d+$//' *

```

Be careful with the wildcard ("*") operator-- make sure you're not going to end up renaming files you don't want to rename!

---

### Post by rye_ on 2008-06-03
I've put you this as a multiline script rather than a one-liner to make it more understandable for you, just execute it in the same folder as the files you wich to alter and it will change ###.###.txt.### to ###.###.txt

Note ### can be of variable length and content

```

#!/usr/bin/ruby -w

counter = 0
Dir["*"].each do |f| 
	if m = /(\.txt)(\..+)/.match(f)
		File.rename(f, $` + $1.to_s)
		counter+=1
	end
end
puts "the number of files altered is #{counter}"

```

Ryan

---

### Post by ghostdog74 on 2008-06-03
```

awk 'BEGIN{q="\047"}
{
 file=FILENAME
 sub(/\....$/,"",file) 
 cmd="mv "q FILENAME q" "q file q
 print cmd
}
' *.[0-9][0-9][0-9]

```

---

### Post by Green_Star on 2008-06-04
Thanks guys, It worked perfectly. With the help of all your examples I wrote a script to loop for all the files and rename it.

Next step I am thinking is to make a gui display for my shell program using [zenity]("http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/").  I would like to review the files list to make sure it is not renaming other not-needed files. Of course I can do it on command prompt but my final goal is to modify this script to use it with nautilus, so that I can just right click on a file in the directory and select this script and it will automatically take all possible files in that directory and rename it(so that i do not have to go to command prompt everything for renaming). 

So my question is, is there any other easy/good gui programming tool other than zenity?

By the way **rye_**, what is /usr/bin/ruby shell? I never heard of this. looks interesting.

---

### Post by rye_ on 2008-06-04
Hi Green_Star,

#! is called 'shebang' symbol, you place it at the top of a script with directions to the programming interpreter the script corresponds to.

e.g. /usr/bin/ruby is the location of the ruby interpreter (a programming language not too dissimilar to python).

if I make my script executable, e.g. at the commandline type
    chmod +x script.rb

I can now execute this script using ./script.rb, and the shebang line #!/usr/bin/ruby tells ubuntu what interpreter to use.


Hope that helps,

Ryan

---

### Post by Green_Star on 2008-06-04
> **rye_ said:**
> Hi Green_Star,

#! is called 'shebang' symbol, you place it at the top of a script with directions to the programming interpreter the script corresponds to.

e.g. /usr/bin/ruby is the location of the ruby interpreter (a programming language not too dissimilar to python).

if I make my script executable, e.g. at the commandline type
    chmod +x script.rb

I can now execute this script using ./script.rb, and the shebang line #!/usr/bin/ruby tells ubuntu what interpreter to use.


Hope that helps,

Ryan

Thanks Ray, yeah I know about the first line of the shell script. I always see some thing like /bin/sh, /bin/ksh, /bin/bash but this is the first time i am seeing ruby, actually i am interested to know more about ruby, when i googled i found about 'ruby on rails' is it same? or something else?

---

### Post by Phenax on 2008-06-04
> **Green_Star said:**
> Thanks Ray, yeah I know about the first line of the shell script. I always see some thing like /bin/sh, /bin/ksh, /bin/bash but this is the first time i am seeing ruby, actually i am interested to know more about ruby, when i googled i found about 'ruby on rails' is it same? or something else?

Hi,

When you load the script (either through double clicking it, or ./script) the shebang line tells your computer what to use to load the script. This is so you don't have to run a command like "ruby file.rb" If you wanted your script to use Python, you'd add #!/usr/bin/python at the top of your script.

Ruby on Rails is a web framework (Similar to Django for Python, and can serve as a replacement for things like PHP). It's not the same thing as Ruby, it is just a massively popular Ruby project.

If you'd like to get into Ruby, feel free to message me (It's a great programming language!)

A great tutorial for Ruby is [http://tryruby.hobix.com/](http://tryruby.hobix.com/) - it allows you to try Ruby in your browser. It gives you an "Interactive Prompt" so you can experience Ruby in the flesh.

---

### Post by rye_ on 2008-06-04
I'd also be more that happy to send you some ruby ebooks.

Ryan

---

### Post by Green_Star on 2008-06-04
thanks guys, I definately love to read online help or ebooks.

---

### Post by rye_ on 2008-06-05
First of all edition 1 of the 'pragmatic programmer's guide', which is an older, free edition of the famous book.  It's the book I started with and edition 2 sits on my desk.  Though edition 2 is MUCH more complete, this link will get you up and running very quickly
[http://www.whytheluckystiff.net/ruby/pickaxe/](http://www.whytheluckystiff.net/ruby/pickaxe/)

When I get chance later, I'll PM you a link to the ebooks I have in mind.

Ryan

---

