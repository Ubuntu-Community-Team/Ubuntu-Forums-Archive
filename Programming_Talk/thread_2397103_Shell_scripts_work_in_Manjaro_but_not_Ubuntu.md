---
title: "Shell scripts work in Manjaro but not Ubuntu"
date: 2018-07-25
forum: Programming Talk
---

### Post by raysa on 2018-07-25
I have these two little scripts in a directory where I place music files in abc format, intending to convert them into pdf files of the same name.
They work perfectly on a laptop whose OS is Manjaro linux, but they don't work on my main desktop which is Ubuntu.
What needs to change to make them work in the Ubuntu setting?

The first script is called 'abc2pdfbatch' and it calls the second one called 'abc2pdf'
```
#!/bin/bash

 find . -maxdepth 1 -type f -name "$1" \
 -exec ./abc2pdf {} \; \

 mkdir -p pdf_a5

 find . -maxdepth 1 -type f -name "*.pdf" \
 -exec mv -v {} pdf_a5/{} \; \
```
```
#!/bin/bash
set -euo pipefail
abcm2ps "$1"
ps2pdfwr -sPAPERSIZE=a5 Out.ps "${1/%.abc/.pdf}"
```

Please note I'm not a programmer and don't really understand these scripts, which I adopted from elsewhere.
Thanks.

---

### Post by Claus7 on 2018-07-25
Hello,

you should make both of them executable:
1) open a terminal and navigate to the folder that you have placed those 2 scripts then
2) chmod 755 abc2pdfbatch abc2pdf

I tested them in my ubu box and they do work. 

Regards!

---

### Post by Olav on 2018-07-25
In addition the packages abcm2ps and ghostscript (for ps2pdf) must also be installed.

---

### Post by raysa on 2018-07-25
Many thanks, both. Followed/enacted all your points ... and checked my own typing when asking the first script to run (Doh!) ... and now all is working as it should.
Thanks again.

---

### Post by Claus7 on 2018-08-15
Hello,

> **raysa said:**
> Many thanks, both. Followed/enacted all your points ... and checked my own typing when asking the first script to run (Doh!) ... and now all is working as it should.
Thanks again.

nice!

I will make an attempt to explain what the scripts and their corresponding commands do:

**1st script**

[LIST]
[*]find . -maxdepth 1 -type f -name "$1" \
 -exec ./abc2pdf {} \; \
[/LIST]

[table="width: 500, class: grid, align: left"]
[tr]
	[td]find[/td]
	[td]we try to search for[/td]
[/tr]
[tr]
	[td]-type f[/td]
	[td]files[/td]
[/tr]
[tr]
	[td]. [/td]
	[td]having as a starting point the current folder (dot could be omitted)[/td]
[/tr]
[tr]
	[td]-maxdepth 1[/td]
	[td]descending at most 1 level of directories below the starting-point[/td]
[/tr]
[tr]
	[td]-name "$1"[/td]
	[td]where the filename should match the first argument passed to the script [the double quotes expand the variable *1*, since they are keeping the symbol, $, as a special character][/td]
[/tr]
[tr]
	[td]\[/td]
	[td]the command continues in the next line[/td]
[/tr]
[tr]
	[td]-exec[/td]
	[td]execute the part that follows exec, taking as arguments the result from find[/td]
[/tr]
[tr]
	[td]./abc2pdf[/td]
	[td]convert abc to pdf using the 2nd script[/td]
[/tr]
[tr]
	[td]{}[/td]
	[td]using as input the filename found before[/td]
[/tr]
[tr]
	[td]\;[/td]
	[td] terminate exec command[/td]
[/tr]
[tr]
	[td]\[/td]
	[td]not needed[/td]
[/tr]
[/table]


[LIST]
[*]mkdir -p pdf_a5
[/LIST]

[table="width: 500, class: grid, align: left"]
[tr]
	[td]mkdir -p pdf_a5[/td]
	[td]create parent directory pdf_a5 and report no error if it exists[/td]
[/tr]
[/table]

[LIST]
[*]find . -maxdepth 1 -type f -name "*.pdf" \
 -exec mv -v {} pdf_a5/{} \; \
[/LIST]

[table="width: 500, class: grid, align: left"]
[tr]
	[td]find . -maxdepth 1 -type f -name "*.pdf" \[/td]
	[td]the same as previous, yet now find all filenames that have the extension pdf[/td]
[/tr]
[tr]
	[td]-exec mv -v {} pdf_a5/{} \; \[/td]
	[td]and move them under the directory pdf_a5[/td]
[/tr]
[/table]

**2nd script**

[table="width: 500, class: grid, align: left"]
[tr]
	[td]set -euo pipefail[/td]
	
[/tr]
[tr]
	[td]-e[/td]
	[td]cause the bash script to exit immediately when a command fails[/td]
[/tr]
[tr]
	[td]-u[/td]
	[td]cause the bash shell to treat unset variables as an error and exit immediately[/td]
	
[/tr]
[tr]
	[td]-o pipefail[/td]
	[td]the bash shell normally only looks at the exit code of the last command of a pipeline;this particular option sets the exit code of a pipeline to that of the rightmost command to exit[/td]
[/tr]
[tr]
	[td]abcm2ps "$1"[/td]
	[td]convert abc music files to postscript files[/td]
[/tr]
[tr]
	[td]ps2pdfwr[/td]
	[td]convert postscript files to pdf[/td]
[/tr]
[tr]
	[td]-sPAPERSIZE=a5[/td]
	[td]with paper size a5[/td]
[/tr]
[tr]
	[td]Out.ps[/td]
	[td]the name of the postscript file that will be converted to pdf is Out.ps[/td]
[/tr]
[tr]
	[td]"${1/%.abc/.pdf}"[/td]
	[td]the name of the pdf file created will be that of the corresponding abc file, yet with the extention pdf - the % can be omitted and written as ${1/.abc/.pdf}, where the name that is represented from 1, its .abc part, will be substituted with the .pdf part[/td]
[/tr]
[/table]

In order to test it in one sample file line-by-line the command:
```
set -- sample.abc
```
would help since if we issue afterwards the command:
```
echo $1
```
the result will be:
> sample.abc

Just a notice: some abc files might give warnings. If they do so, then the "set -euo pipefail" option will make the scripts to exit, and the conversions won't work. For that reason it is adviced to remove that option by adding a # in front of that line of the 2nd script:
#set -euo pipefail

Regards!

---

