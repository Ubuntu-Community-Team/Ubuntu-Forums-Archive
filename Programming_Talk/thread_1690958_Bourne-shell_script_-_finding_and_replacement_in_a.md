---
title: "Bourne-shell script - finding and replacement in any web page code"
date: 2011-02-19
forum: Programming Talk
---

### Post by vl72 on 2011-02-19
I want to write Bourne-shell script that will be to do finding and replacement in any web page code (.htm file) name of the tied folder in which have been saved pictures, .css, .js and other files.
This folder create a web browser when we save web page completely and has so name as web page and has ending '_files'. 
I have many web pages where name of their folder are incorrect. Of course, my web browser shows these web pages without pictures.
I can count amount of web pages in a folder (/path) needed for me.
  1) find /path -type f -name "*.htm*" -print | grep -c .htm        or
      find /path -type f -name *.htm | wc -l
I can get list of web pages.
  2) ls /path *.htm > out-list

But I don't know how to assign the value from out-list (2) or result commands from pipeline (1) to a variable.
HOW TO DO THIS????
Then I want to do next:
  3)
	var="1"
	# where variable 'list' is an amount of web pages
	while [ $var -le  $list ]
	 do
	4) &#8230;......
	8 &#8230;......
	var=$[$var+1]
	done

  4)	assign the 1st  (then 2nd , etc. ) value from out-list (2) to variable 'webfile'
	sed -n $var,+0p out-spisok
  5)      find the 1st string value '_files' in the 'webfile'
	grep -m1 _files $webfile

  6)	For example, 'abracadabra_files' is an incorrect folder in the 'webfile'
	I must to know start and end position 'abracadabra' without ending '_files', &#8220;cut&#8221; name of the incorrect 	folder and assign it to the variable 'finder'
            finder = 'abracadabra' 
	BTW, name of a folder before '_files' is between  '=&#8221;' and '_files'  in any web page code.
HOW TO DO THIS????
  7)      foldernew = $webfile (without '.htm')
            ' foldernew' is equal with name of the tied folder without ending '_files' in the folder '/path'
  8      find and replace in the 'webfile'  and save result in the 'webfile-out'
	sed s/$finder/$foldernew/g $webfile > $webfile-out

Can anybody help me?

---

### Post by Rany Albeg on 2011-02-19
This is how you can store the output of a command in a variable
```
output="$(command 2>&1 >/dev/null)"  # Save stderr, discard stdout.
output="$(command 2>&1 >/dev/tty)"   # Save stderr, send stdout to the terminal.
output="$(command 3>&2 2>&1 1>&3-)"  # Save stderr, send stdout to stderr
```

For extracting the relevant part out of abracadabra_files you can use the following:
```
var=abracadabra_files; var="${var%_*}"
```

And now var contains abracadabra.

I hope I understand you correctly.
If not - please give the main concept of what are you trying to do.
You don't have to give the entire idea of your code.

Thank you.

---

### Post by hakermania on 2011-02-19
No, you don't have to do all these....
```
#!/bin/bash
#Inside $() place whatever command will output all the .html files you want to change...
for i in $(locate *.html | grep "/home/alex"); do
#Now $i a html file, the $i will each time be the next html file, so do what you want here with $i
echo $i
fi
```

---

