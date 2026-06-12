---
title: "Bash scripts: publishing a web site. Any suggestions for better style/functions?"
date: 2011-08-29
forum: Programming Talk
---

### Post by keithpeter on 2011-08-29
Hello All

I write my Web pages using markdown format. I use three bash scripts to publish the Web pages to a hosted Web server. These scripts are horrible hacks I've cobbled together out of bits found on Web pages. Typically, I find a single command in Bash that does what I want then wrap that in some echo line or backticks.

Any improvements you can suggest to the scripts, or better commands to use, would be appreciated. Or suggestions for functions to read up on.

[LIST]
[*]**makepage.sh** is called from within the 'pages' directory, runs the markdown script and adds a header and footer, saving the result as an html file
[*]**makeindex.sh** builds an index of all the html files in the 'pages' directory and writes an index.html file. This command is run from the directory above the pages directory and index.html ends up in the 'top' of the Web server public_html directory
[*]**publish.sh** calls lftp and mirrors the pages directory to the remote server, and then separately copies up the index and style sheet as that's all I want in the top level.
[/LIST]

**[SIZE="2"]makepage.sh[/SIZE]**

```
#!/bin/bash
TEXTFILE=${1}
TITLE=`head -1 $TEXTFILE`
echo "<!DOCTYPE gunge cut to save space"> 
<html xmlns=\"http://www.w3.org/1999/xhtml\"> 
<head> 
<meta http-equiv=\"Content-Type\" content=\"text/html; charset=ISO-8859-1\" /> 
<title> 
$TITLE 
</title>
<link rel=\"stylesheet\" href=\"../style.css\" type=\"text/css\" media=\"screen\" /> 
</head> 
<body>
<p>[ <a href=\"../index.html\">home</a> ]</p> " | tee $TEXTFILE.html
markdown $TEXTFILE | tee --append $TEXTFILE.html
DATETEXT=$(date '+%a %b %d %Y')
echo "<hr /><p><small>Keith Burnett, Last update: $DATETEXT</small></p>
</body>
</html>" | tee --append $TEXTFILE.html
chmod 777  $TEXTFILE.html
exit 0
```

**[SIZE="2"]makeindex.sh[/SIZE]** 

The html title of the page is always on line 6 of the converted html file when converted using makepage.sh. The ls -lt command produces a list of files with the most recently modified listed first.

```
#!/bin/sh
echo "<h2>Recently modified pages</h2>" # html header
echo "<ul>"
for name in `ls -lt pages/*.html | awk '{print $9}'`
  do
  echo "<li><a href="$name">`head -6 $name | tail -1`</a></li>"
done
echo "</ul>"
DATETEXT=$(date '+%a %b %d %Y')
echo "<hr /><p><small>Last updated: $DATETEXT</small></p>
</body>
</html>" 
chmod 777 index.html
exit 0
```

**[SIZE="2"]publish.sh[/SIZE]**

I need to exclude the makepage.sh script from the mirror.

```
#!/bin/sh
HOST=web.server.com
USER=usernameonserver
PASS=secret
./makeindex.sh > index.html
echo "Starting to sftp..."
lftp -u ${USER},${PASS} sftp://${HOST} <<EOF
cd public_html_folder
put index.html
put style.css
mirror -e -n -R pages
bye
EOF
echo "done"
exit 0
```

Thanks very much

---

### Post by sisco311 on 2011-08-29
Check out:
[http://mywiki.wooledge.org/BashFAQ/](http://mywiki.wooledge.org/BashFAQ/)
and
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)


Inistead of **TITLE=`head -1 $TEXTFILE`** you can use **read -r title < "$textfile"**

NOTE: By convention, environment variables (PAGER, EDITOR, ..) and internal shell variables (SHELL, BASH_VERSION, ..) are capitalized. All other variable names should be lower case.

Instead of echo "text" | tee -a file you can use a [here document]("http://mywiki.wooledge.org/BashGuide/InputAndOutput#Heredocs_And_Herestrings"):

```
cat << EOF > file  #or cat << EOF >> file
plain text
value of var is: $variable
output of command: $(command)
EOF

```

The POSIX form $(COMMAND) is preferred over `COMMAND`, see: BashFAQ #82

Never use something like: for file in `ls`, see: BashPitfalls #1 and BashFAQ #3

You can use Bash + GNU find + GNU sort:
```

while IFS= read -r -d file
do
    echo ${file#* }
done< <(find "$dir" -type f -printf '%T@ %p\0' | sort -znr)

```

Instead of **head -6 file | tail -1** you could use **sed -n "6{p;q;}" file**, see: BashFAQ #11

Oh, and always quote your variables.

---

### Post by keithpeter on 2011-08-30
Hello sisco311

Thanks for the detailed feedback with references, and the comments on style, this is all useful learning.

I'll add the alternative forms step by step and see how they work

Cheers

---

### Post by keithpeter on 2011-08-30
Hello sisco311 and anyone else

makepage.sh was relatively easy to re-write along the lines you suggested, and the Cat << EOF > filename ... EOF construction makes it much easier to use scripts to generate html.

makeindex.sh proved to be a little more complex. This works...

```
#!/bin/bash
# Bash + GNU find + GNU sort
dir=pages
while IFS= read -r -d '' file
do
    echo "<a href=\"${file#* }\">$(sed -n "6{p;q;}" ${file#* })</a>"
done< <(find "$dir" -maxdepth 1 -name "*.html" -type f -printf '%T@ %p\0' | sort -znr)
```

and it lists the html files in the directory in order of their last modification.

I've noted that I had to use !/bin/bash in the first line here as well, the usual !/bin/sh wasn't working.

The acid test will be to try these scripts on file names with spaces in...

Thanks again...

---

### Post by sisco311 on 2011-08-30
> **keithpeter said:**
> 

but it lists *all* the files in the directory. I need to work out how to restrict the files to just the html ones. I'm guessing that is a 'find' command option...



Use a -name or -iname (same as -name but case insensitive) test:
find /path -maxdepth 1 -name '*.html' -type f ....

> **keithpeter said:**
> 
I've noted that I had to use !/bin/bash in the first line here as well, the usual !/bin/sh wasn't working.


Yep, in Ubuntu /bin/sh is a symlink to dash. [uwiki]DashAsBinSh[/uwiki]

> **keithpeter said:**
> 
The acid test will be to try these scripts on file names with spaces in...


They should work with any valid filenames, files with spaces, newlines, leading and trailing whitespaces or any special characters.

---

### Post by keithpeter on 2011-08-30
Hello sisco311

Yup, I found the -name "*.extension" option and edited post number 4 just in case anyone is wondering.

I also had to quote a variable to make the script work with filenames with spaces, The 'echo' line within the loop should read

```
echo "<li><a href=\"${file#* }\">$(sed -n "6{p;q;}" [COLOR="Red"]"${file#* }"[/COLOR])</a></li>"
```

otherwise sed complains when you have spaces in the lines. I'm tidying this lot up now and reading about globs and IFS.

Thanks for the tutorial

---

### Post by sisco311 on 2011-08-30
You are welcome!

---

