---
title: "Bash script in Konqueror servicemenu"
date: 2009-07-10
forum: Programming Talk
---

### Post by Lampi on 2009-07-10
I'd like to parse and format xml files using a Konqueror action. So I created a service menu entry, that looks like this.

You can put this code in a file in /usr/share/apps/konqueror/servicemenus/ -  name it for ex. xmlformat.desktop


```
[Desktop Entry]
ServiceTypes=text/xml
Actions=formatXML

[Desktop Action formatXML]
Name=format XML
Icon=terminal
Exec=konsole --noclose --workdir "%d" -T xmlformat -e bash -c 'echo "Press Return to format XML, Ctr+C will exit"; read aa; echo "Enter output <filename.xml>"; read file; /usr/bin/xmllint --recover --format %u -o "$file"; echo ""; echo "done, new XML saved to:" "$file"; echo ""; echo "press Return to open XML in Kate, Ctr+C does quit"; read bb; kate "$file"'
```
The code is written for bash and strange as it sounds this exact code works fine in a Thunar action, but it refuses to work in Konqueror. 

Basically I can't get Konqueror to cope with the "read file" command. You'll notice I use a lot of "" to make sure I can use spaces in directories and filenames.

Is there someone experienced enough with this freedesktop stuff to see why it works with Thunar and it doesn't work in Konqueror?

---

