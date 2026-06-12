---
title: "how does one open .eml emails?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-08-29
A friend using microsoft outlook sends me forwarded .eml emails and except for the first part of the email message, the body of the message looks like this: "CaydY5mzxGm2QCqAGLObHwVAAAAAAAACAAAAAECQKTQ0gfj0hGX8ACgyV6oUCwBAAAAAAAABQAY
AEEAcABwAGwAaQBjAGEAdABpAG8AbgAAAAAAPgBXAGkAbgBkAG8AdwBzACAATQBvAHYAaQBlACAA
..." and so on. And the file name has a .wmv windows media extension. How do I open these attachments and how can I check the extension of the file **before** I open it and if it's safe to open?

I run Hardy Heron and use gmail and evolution for email right now.

---

### Post by ProgramErgoSum on 2008-08-29
Here is a related thread : [How to read in linux the *.eml files from the microsoft Outlook express ?]("http://ubuntuforums.org/showthread.php?t=80112")

---

### Post by Brian_Newbie on 2008-08-29
Deleting the file extension and opening in gedit did not work. I'll try the converter eml2mbox - A Ruby eml to mbox converter - from the thread you mentioned as it looks promising. 

Thanks for the link.

---

### Post by forger on 2008-08-29
> 
Description: mht to war file converter
 kmhtConvert is an mht (Microsoft Windows (R) Web Archive) file to war (KDE
 Web Archive) file converter.
 Since version 0.7 kmhtConvert is able to open and display MHTML and EML
 (Microsoft Windows (R) Email Archive) files.
 kmhtConvert uses icons from the Noia Warm icon set.
 .
 Homepage: [http://users.otenet.gr/~geosp/kmhtconvert/index.html](http://users.otenet.gr/~geosp/kmhtconvert/index.html)

[http://members.hellug.gr/sng/kmhtconvert/screenshot.html](http://members.hellug.gr/sng/kmhtconvert/screenshot.html)

```
apt-cache search eml.*email
sudo apt-get install kmhtconvert
```

---

### Post by ProgramErgoSum on 2008-08-29
> **Brian_Newbie said:**
> ...
Thanks for the link.

You are welcome !

---

### Post by forger on 2008-08-29
I also think that mozilla thunderbird can handle eml files

---

### Post by Brian_Newbie on 2008-08-30
I decided try Mozilla's Thunderbird email client for my Gmail account as I already use Evolution for my ISP's emails. 

It completely resolved the issue of dealing with .eml emails from my Microsoft Outlook friends. After installing Thunderbird, I downloaded all of my .eml emails, opened them, then simply clicked on the title of the attachment to the right of the .eml file, (these were .wmv files) - and viola! they played in totem without a hitch!! No conversions, no nothing. Just click and play. 

I'd like to thank Forger for suggesting Thunderbird. I never thought it would be so easy.

---

### Post by forger on 2008-08-30
> **Brian_Newbie said:**
> I'd like to thank Forger for suggesting Thunderbird. I never thought it would be so easy.
Thank you for making me find it :KS My brother kind of needed a similar solution with the .eml files

---

### Post by 11seashell11 on 2010-04-21
I set up a computer for one of my friends, and he is not very good with computers. Since gmail downloads the files without an extension, I wrote this script for him.

```
#!/bin/sh
filename="$1"
file -b --mime-type "$filename" > temp101.txt
while read inputline
do
	kind="$(echo $inputline)"
done < ./temp101.txt
if [ ${kind} = "message/rfc822" ]
then
	cp "$filename" "$filename".eml
	rm "$filename"
	thunderbird "$filename".eml
else
	echo "This is not an EML file."
fi
rm temp101.txt
exit 0
```

I then made a symbolic link from /usr/local/bin/eml to my script.
This code makes it so that he can download and open the file from directly within his browser, as long as the default program to open it this file with is set to eml. The script puts the .eml extension on the end of the file, and opens it with thunderbird. You could change thunderbird to any other application that you wanted to open the files with.

---

### Post by Jacques.Goldberg on 2010-06-22
I found something simpler, for what it is worth.

1-Under Thunderbird, save the .eml file anywhere.
2-From a Firefox window "Open File", select the saved file, and then
3-Almost always, send the file to Trash after having read its irrelevant contents.

DBR is even more efficient, but dangerous for the may be 1  out of 100 of **my** eml's which is not crap. (DBR=Destroy Before Reading, recommended for top secret material).

---

### Post by warfacegod on 2010-06-22
Don't suppose anyone has a solution for .oft files?

---

