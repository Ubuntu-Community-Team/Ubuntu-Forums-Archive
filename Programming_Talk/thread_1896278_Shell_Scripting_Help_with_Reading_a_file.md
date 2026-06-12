---
title: "Shell Scripting Help with Reading a file"
date: 2011-12-16
forum: Programming Talk
---

### Post by CrusaderAD on 2011-12-16
This may seem easy for some of you... but here's what I'm trying to achieve:

Load a .txt file which looks like:

1234567890
0987654321
1356890372
8923748923
5692329855

Go through it line by line and execute a wget command using one of the lines from the text file in the string. Any help with this would be appreciated. The script will be doing many more things, but this is where I'm stuck.

---

### Post by Lars Noodén on 2011-12-16
[s]Do you mean something like this?[/s]

```

[s]for i in $(cat file.txt);do
 wget "http://${i}/";
done[/s]

```

Edit: Old habits die hard.  See post #3 instead. :)

---

### Post by sisco311 on 2011-12-16
See: BashFAQ 001 (link in my sig)
```

file="path/to/file"
while read -r line
do
    wget "whatever${line}somethingelse"
done < "$file"
```

---

### Post by CrusaderAD on 2011-12-16
```

[s]for i in $(cat file.txt);do
 wget "http://${i}/";
done[/s]

```

Exactly, Thanks! There guys had a similar solution too: [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-read-data-from-file-to-use-in-shell-script-477610/]("http://www.linuxquestions.org/questions/linux-newbie-8/how-to-read-data-from-file-to-use-in-shell-script-477610/")

Here's a hard one though... the wget command will return an XML file. Is it possible to read that XML file, pull a node from it, and put that value in another file?

---

### Post by Lars Noodén on 2011-12-16
> **CerealCypher said:**
> Is it possible to read that XML file, pull a node from it, and put that value in another file?

Kind of, but it's infinitely better to use a real XML parser.  You can do one in a few lines with perl.  Which schema or DTD, if any, is in use?

---

### Post by CrusaderAD on 2011-12-16
Here's what it looks like:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<tracking>
  <links>
    <link uri="http://www.123.com" rel="self"/></links>
      <status><returncode>101</returncode>
        <message>No results were found.</message>
          <timestamp>2011.12.16 14:06:48,616</timestamp>
      </status>
      <package_id>123.xml</package_id>
  <events/><messages/>
</tracking>
```

---

### Post by Telengard C64 on 2011-12-16
> **CerealCypher said:**
> This may seem easy for some of you... but here's what I'm trying to achieve:

Load a .txt file which looks like:

1234567890
0987654321
1356890372
8923748923
5692329855

Go through it line by line and execute a wget command using one of the lines from the text file in the string. Any help with this would be appreciated. The script will be doing many more things, but this is where I'm stuck.

It should be possible to accomplish this in of the scripting languages common to GNU/Linux systems. 

Is the file **a.txt** just a list of URLs? If so then see this [wget](http://manpages.ubuntu.com/manpages/wget) option:

[quote=man wget] -i file
       --input-file=file
           Read URLs from a local or external file.  If - is specified as
           file, URLs are read from the standard input.  (Use ./- to read from
           a file literally named -.)

           If this function is used, no URLs need be present on the command
           line.  If there are URLs both on the command line and in an input
           file, those on the command lines will be the first ones to be
           retrieved.  If --force-html is not specified, then file should
           consist of a series of URLs, one per line.

           However, if you specify --force-html, the document will be regarded
           as html.  In that case you may have problems with relative links,
           which you can solve either by adding "<base href="url">" to the
           documents or by specifying --base=url on the command line.

           If the file is an external one, the document will be automatically
           treated as html if the Content-Type matches text/html.
           Furthermore, the file's location will be implicitly used as base
           href if none was specified.[/quote]

---

### Post by Lars Noodén on 2011-12-16
> **CerealCypher said:**
> Here's what it looks like:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<tracking>
  <links>
    <link uri="http://www.123.com" rel="self"/></links>
      <status><returncode>101</returncode>
        <message>No results were found.</message>
          <timestamp>2011.12.16 14:06:48,616</timestamp>
      </status>
      <package_id>123.xml</package_id>
  <events/><messages/>
</tracking>
```

Which XML element do you want to extract?

---

### Post by CrusaderAD on 2011-12-16
> **Lars Noodén said:**
> Which XML element do you want to extract?

Here's what I want to extract from the XML: 

```

<event>
  <links/>
    <timestamp>12/07/2011 06:43 AM</timestamp>
      <description>Here's a description</description>             
        <location>COLUMBUS, OH</location>
</event>
```

---

### Post by CrusaderAD on 2011-12-23
Here's what I ended up doing. Hopefully it helps someone out. It takes a simple txt file to loop through line by line, hits a site for an xml file, then scrubs and inserts the xml data into a very simple html file.

```
#!/bin/bash

############# GET THE FILE TO LOOP THROUGH
echo -e "\033[32m \033[1m Generating the loop file... \033[0m"
wget http://www.123.com/123.txt

############# BUILD THE BEGINNING OF THE HTML FILE
echo "<html>" >> /home/user/123.html
echo "<head>" >> /home/user/123.html
echo "<title>123ing Status</title>" >> /home/user/123.html
echo "<style type=text/css>" >> /home/user/123.html
echo "p{font-size:5px arial,sens-serif;}" >> /home/user/123.html
echo "</style>" >> /home/user/123.html
echo "</head>" >> /home/user/123.html
echo "<body>" >> /home/user/123.html
echo "<table cellpadding=0 cellspacing=0 border=0 width=100%>" >> /home/user/123.html

############## GETTING THE FILE CONTENTS
echo -e "\033[32m \033[1m Starting Test... \033[0m"
file="/home/user/123.txt"
cd /home/user/123/xml
############## LOOP THROUGH FILE
while read -r line
do
    wget "https://123.com/test.php?Id=${line}"
echo -e "\033[32m \033[1m Number: ${line} Ran... \033[0m"
echo -e "\033[32m \033[1m Inserting into the HTML... \033[0m"
info=`awk '{gsub(/<[^>]*>/,"<br>")};1' XMLfileNameGoesHereId=${line}`
echo "<tr><td><font size=2>${info}</font></td></tr>" >> /home/user/123.html

############# LOOP DONE
done < "$file"
cd /home/user/123
############# FINISH THE HTML
echo -e "\033[32m \033[1m Finish writing the HTML... \033[0m"
echo "</table>" >> /home/user/123.html
echo "</body>" >> /home/user/123.html
echo "</html>" >> /home/user/123.html
```

---

