---
title: "HOW TO: Fix JavaScript/C MIME type problem with GNOME"
date: 2007-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Samjiman on 2007-06-03
**_Problem_**
Your JavaScript files (application/x-javascript) are incorrectly identified as C source code files (text/x-csrc)
by your GNOME system.

**_Cause_**
This is caused because your system is set to identify C source code files by looking for C-style comments
(/* */ and //) in your JavaScript and therefore 'deciding' your files are C source code.

**_Solution_**

[color="Red"]DISCLAIMER: Follow this solution with caution - I in no way claim responsibility if your system breaks.[/color]

Luckily, the solution to the problem is quite straightforward, open a terminal and enter the following
at the prompt (#).
```

# cd /usr/share/mime/packages

```

Then
```

# ls

```

You are now displaying the contents /usr/share/mime/packages, which will look something like this
```

apt.xml            
brasero.xml         
freedesktop.org.xml  

```

Now enter
```

# sudo *gedit* freedesktop.org.xml

```

(Of course, you may use any text editor installed on your system which you can access with root, rather than *gedit*)

When prompted, enter your administrator password, the file should then display in your text editor of choice.
In freedesktop.org.xml, locate this line of XML markup
```

<comment>C source code</comment>

```

When you have located that, scroll further down until you locate these lines
```

<match value="/*" type="string" offset="0"/>
<match value="*/" type="string" offset="0"/>
<match value="//" type="string" offeset="0"/>

```

These are the lines that are causing the problem, so let's comment them out with XML comments like so
```

<!-- 
<match value="/*" type="string" offset="0"/>
<match value="*/" type="string" offset="0"/>
<match value="//" type="string" offeset="0"/>
-->

```

Next we need to located this line
```

<comment>JavaScript program</comment>

```

Scroll up until you find this line
```

<alias type="application/x-javascript"/>

```

Change the line to this
```

<alias type="application/javascript"/>

```

Scroll up until you find this line
```

<mime-type type="application/javascript">

```

Change the line to this
```

<mime-type type="application/x-javascript">

```

Save the file and close the text editor.

In the terminal enter
```

# sudo update-mime-database /usr/share/mime

```

Log out of the system and log in again, the change should now be visible as JavaScript files
will be correctly identified. :)

---

### Post by aiserv on 2007-12-10
```
me@desktop:~$ sudo update-mime-database /usr/share/mime
Segmentation fault (core dumped)
```
And now JavaScript files displays as MATLAB script/function :confused:

---

### Post by Samjiman on 2007-12-17
Hmmm... I  don't know what to suggest until I can see what you've done in your freedesktop.org.xml file. A small mistype perhaps.

I'll see if I can get it fixed for you over MSN Messenger.

---

